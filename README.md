# 科大讯飞AI学习机破解安装第三方应用教程

* 本项目欢迎各位读者开issue，**本项目秉承公益的原则，故禁止倒卖！被骗的欢迎开issue来提供骗子个人信息！**
* 如果看不了图片，你可以去下载WattToolkit，里面有“Github加速”功能；或者你也可以把这个项目克隆到本地，然后下个VScode，Vscode中下一个OfficeViewer插件就能看了
* 材料：电脑*1，数据线一根，乐于提问、勤于思考/会用搜索引擎的人x1
* 文件库:https://kdxf.work/

### 第三方应用安装（又称：升级软件法）

##### 思路

* 制作可以打开隐藏的activity的apk（包名得是应用商店可下载的软件的包名，且将版本号更改为9999999999），然后拿钉钉、QQ、微信等聊天软件传上去，进行“更新”，后面通过这个途径达到开启adb的效果。

##### 实践

###### 第一步：确认cpu的厂商

打开平板上的“设置”app，点到“我的设备”，看到“处理器”一栏，一般这里会显示“Unisoc”“Qualcomm”等字样，那你就完成了第一步，且证明了该设备系统版本为安卓9

###### 第1.1步（通过UI猜安卓版本）：看平板右上角的状态栏，如果像![1706627508990](image_markdown/QQ截图20240127141621.png)一样，那就是安卓12，如果是其他样子的，那就是安卓9

###### 第二步：修改得到apk

准备文件：

* [APK Editor Studio](https://qwertycube.com/apk-editor-studio/download/)
* [创建快捷方式.app(这里的是洋葱学园改版，你需要将它包名改为你需要的)](https://whhhh.cloud/%E7%A0%B4%E8%A7%A3%E6%96%87%E4%BB%B6/%E5%88%9B%E5%BB%BA%E5%BF%AB%E6%8D%B7%E6%96%B9%E5%BC%8F.apk)
* [展讯特有的adb/下载模式驱动](https://androiddatahost.com/dsa6h)
* [adb工具下载及环境配置（一看就会）](https://zhuanlan.zhihu.com/p/653371171)

然后，打开APK Editor Studio

![1706707610274](image_markdown/image_2.png)

![1706707825974](image_markdown/img3.png)

![1706708094229](image_markdown/img4.png)

自此，准备工具的制备告一段落，你需要点“保存apk”来保存你来之不易的成果。

###### 第三步：在平板上实施”调虎离山“之计，并做到

3.1：通过某种方式将你的劳动成果从电脑上传到平板上（QQ、微信、钉钉，甚至是USB传输也行），打开下载好的apk文件，此时正常会弹出软件更新，点击继续，然后直接返回桌面，****长按被替换的软件并卸载，卸载之后会看到之前的应用更新**，一路无脑安装即可**，*打开创建快捷方式后右上角菜单把三个方框勾上*

3.2.1（"设置-我的设备"中看到自己是”Qualcomm“的情况）：在”打开快捷方式“app中搜索”搜索建议“，点右边绿色的”详情“按钮，点”打开“然后如下图操作

![1706713223387](image_markdown/img5.png)

然后点几次"版本号"就能打开开发者，进而打开"USB 调试"

3.2.2（"设置-我的设备"中看到自己是"Unisoc"的情况）：在**步骤3.1完成后**直接在"打开快捷方式"中向下翻到***EngineerMode*那一项(包名为com.sprd.engineermode)**，然后点"活动列表"，点开最顶上那一个的"详情"，然后点"打开"，切换到"DEBUG&LOG"选项卡，向下滑找到"USB Debug"并打开该选项

**到这里，你已经成功开启了adb，可以进入下一个步骤了！加油，达瓦里氏，胜利就在眼前！**

3.3  安装adb驱动和爱玩机工具箱，并授予工具箱MDM权限，来实现软件安装的本地化、自主可控化

[下载：爱玩机工具箱(com.byyoung.setting) - S-22.0.8.1 - 应用 - 酷安 (coolapk.com)](https://www.coolapk.com/apk/com.byyoung.setting)

[Download SPD Driver R4.20.4201 (UniSoc Driver) (androiddatahost.com)](https://androiddatahost.com/dsa6h)

你在**第二部准备工作**还下了一个压缩包（.zip）文件，你需要把它解压到一个目录。然后将下载的爱玩机工具箱移到那个解压的目录中，并在上方的地址栏输入"cmd",能打开一个窗口，你需要输入如下内容

```
adb install <apk文件路径（我更建议你打个空格，然后直接将apk文件拖进来，windows会自动识别路径）>
```

然后，点开平板上的“爱玩机工具箱”app，你需要进到“权限中心”，并照着应用提示，启用最下面的“高级设备管理员（带防卸载）”即可。后面，你可以在“导航——应用相关——应用安装器”中自行启用“激活此安装器”，本篇不过多赘述。

建议在破解后删除“系统更新”应用，命令如下：

```
adb shell pm uninstall -k --user 0 com.iflytek.study.ota
```

这样是为了防止KDXF官方后续对该方法完全的封杀

## 自此，第三方应用安装的教程结束！完结撒花~

## 2024.2.13更新：有一种基于修改system分区以达到自动开启adb的方法，我放在了[&#34;AI学习机高阶教程（Experimental | 未完工警告）&#34;中的&#34;修改system分区以达到连接电脑自动打开adb&#34;部分](https://github.com/sdgasdgahj/studentpad-research/tree/main#修改system分区以达到连接电脑自动打开adb（T10，v1.07.7实践成功，2024.2.12）)

## 2024.2.20更新：新研发出一种基于修改system分区以达到root的方法（已在展讯部分机型测试通过）

## 2024.2.24更新：如果你是新版本的展讯机型，你可以直接去root然后配合上"修改system分区……adb部分"强开adb，上方的教程留给未更新的老机型

## 2024.3.2更新：将把教程中关于开启adb部分与root系统部分进行合并

## 2024.3.8更新：高阶教程中关于开启adb部分与root系统部分合并完成

## 2024.3.23————添加贡献者名单+机型配置和玩机情况表

---

# AI学习机高阶教程（Experimental | 未完工警告）

* Warning：下列操作要想生效，都需要进行**解锁bl(即Bootloader锁)**，以及**刷入分区**的危险操作，三思而行，所以备份尤为重要，我建议是但凡是要进行修改的分区都应当进行备份，以及在root完成后，请使用爱玩机工具箱"导航——刷机工具箱——镜像分区管理"导出系统除userdata分区以外的所有分区的备份
* 下列操作都已经超出了《科大讯飞AI学习机AI学习软件服务用户协议》：

> 用户若对学习机进行刷机行为，包括但不限于获取root权限，刷入第三方ROM等，则本机将会从科大讯飞AI学习机官方技术支持和软件保修服务中被移除

所以，下面的内容请三思而行

## 获取学习机(展讯系机型)的root（即刷入Magisk）

为何要把root部分拿出来讲呢？因为展讯芯片系学习机的boot无法patch（原因是没有ramdisk）

system分区植入法目前已成功实践，rec法因为avb的原因无法正常启动，所以下文只讲system分区植入magisk法

适配机型:x2pro,t10等ud710设备，c系列机型（c6,c10,c10pro）因未知原因提取失败，

* 大概思路：将magisk安装到安卓system分区，可以参考[某酷安大佬写的方案（Magisk system root部分）](https://github.com/TomKing062/CVE-2022-38694_unlock_bootloader/wiki/Magisk)

总结下来就四步：①解锁板子的bootloader（这一步已经做到能纯Windows环境下进行了），②提取system分区并进行修改，③将修改好的文件放回分区并刷回板子中以root

### 解锁bootloader（最重要的一集）

* 文件：[到“紫光解BL锁”目录下下载adb-fastboot-win-unlock.zip文件](http://qutick102.ysepan.com/)
* 文件2：[下载&#34;用来得到解锁密钥的软件.apk&#34;](https://kdxf.work/)
* 进入fastboot模式(有两种方法):
* 1.使用物理按键进入REC（提示：与Jingpad A1进入rec的方式一致），然后使用电源键+音量加的按键组合调出菜单，用音量上选择第二项，然后使用电源键进入fastboot模式
* 2.检查学习机内是否有编程空间软件，若没有可升级学习机系统；进入编程空间后输入以下文本并执行学习机会自动进入fastboot模式

```
import os
os.system("reboot bootloader")
```

#### 生成解锁密钥方式1（有另一台安卓设备的情况下）

* 在下载下来的文件的解压目录的地址栏输入cmd，在打开的窗口中输入 `fastboot devices `得到一串字母加数字，这就是你机器的序列号，在另一台安卓设备上安装“文件”中的[apk](https://www.alipan.com/s/SLgfA1dFGrt)，输入你得到的序列号（或平板背面贴纸上的SN码），完事会生成一个叫signature.bin的文件，你需要将这个文件拷到当前目录(即：你cmd在的目录)

#### 生成解锁密钥方式2(纯电脑方式)

* 步骤1.安装环境，在powershell/Windows Terminal（管理员）中输入以下链接中的命令

[自动转换Windows版本至专业工作站版,准备WSL相关Windows功能,安装WSL(Ubuntu)相关命令 · Issue #4 · KDXF-BOOM/studentpad-research (github.com)](https://github.com/KDXF-BOOM/studentpad-research/issues/4)

* 步骤2.在下载下来的文件的解压目录的地址栏输入cmd，在打开的窗口中输入 `fastboot oem get_identifier_token` 命令获取 android 设备ID

输出结果类似于这样：

```
Identifier token:
XXXXXXXXXXXXXXXXXXXXXXXX
OKAY [  0.019s]
finished. total time: 0.019s
```

* 将步骤 2 所获取的设备ID作为参数，在wsl中执行设备号签名脚本，命令如下：

  ```
  ./signidentifier.sh  <填入设备ID，若为多行，请将其连成一行， 并且中间不能出现空格字符> rsa4096_vbmeta.pem signature.bin
  ```

取生成的signature.bin文件，这就是你需要的解锁文件

#### 正式解锁

* 使用 `fastboot flashing unlock_bootloader signature.bin`的命令，进行设备解锁，然后按下音量下键，确认解锁即可，然后bootloader会进行格机
* 恭喜你，成功解锁bootloader

### 进入download

进系统后关机，然后长按音量下+插上数据线即可进入下载

附赠：按键图

![1708767509011](image/README/1708767509011.png)

### 获取分区大小(有关下一步提取)

```
spd_dump fdl <fdl1> 0x5500 fdl <fdl2> 0x9efffe00 exec partition_list partition.xml
```

### 提取分区（重要：提取完请手动将system镜像复制一份，防止出意外状况后无法恢复至原来状态）

其中size部分填入上一步执行后cmd反馈中system后的数字+M，如114514M

```
spd_dump fdl <fdl1> 0x5500 fdl <fdl2> 0x9efffe00 exec read_part system 0 <size> system.img read_part vendor 0 <size> vendor.img
```

### 修改system(system-root文件下的内容在system-root.zip)

```
mkdir system
sudo mount -o rw system.img system
sudo cp system-root/bin/magisk  system/system/bin/magisk
sudo cp system-root/bin/magiskpolicy system/system/bin/magiskpolicy
sudo cp system-root/init/magisk.rc system/system/etc/init/magisk.rc
sudo cp -r system-root/magisk system/system/etc/init
sudo chmod 0700 -R system/system/etc/init/magisk 
sudo chown -R 0 system/system/etc/init/magisk
sudo chcon -R -h u:object_r:system_file:s0 system/system/etc/init/magisk
cd system/data
mkdir adb
cd ..
cd ..
sudo cp -r system-root/data-magisk system/data/adb/
```

### 修改bootanim.rc（必做）：

```
sudo nano system/system/etc/init/bootanim.rc
```

用键盘将光标移动在最底下并按几下回车，然后向其中复制以下内容
Tips:把鼠标放到代码框右上角，你会发现有一个复制的按钮，按一下就好，然后在命令行中使用右键进行粘贴即可

```
on post-fs-data
    start logd
    exec u:r:su:s0 root root -- /system/etc/init/magisk/magiskpolicy --live --magisk
    exec u:r:magisk:s0 root root -- /system/etc/init/magisk/magiskpolicy --live --magisk
    exec u:r:update_engine:s0 root root -- /system/etc/init/magisk/magiskpolicy --live --magisk
    exec u:r:su:s0 root root -- /system/etc/init/magisk/magisk64 --auto-selinux --setup-sbin /system/etc/init/magisk /sbin
    exec u:r:su:s0 root root -- /sbin/magisk --auto-selinux --post-fs-data

on nonencrypted
    exec u:r:su:s0 root root -- /sbin/magisk --auto-selinux --service

on property:vold.decrypt=trigger_restart_framework
    exec u:r:su:s0 root root -- /sbin/magisk --auto-selinux --service

on property:sys.boot_completed=1
    mkdir /data/adb/magisk 755
    exec u:r:su:s0 root root -- /sbin/magisk --auto-selinux --boot-complete
   
on property:init.svc.zygote=restarting
    exec u:r:su:s0 root root -- /sbin/magisk --auto-selinux --zygote-restart
   
on property:init.svc.zygote=stopped
    exec u:r:su:s0 root root -- /sbin/magisk --auto-selinux --zygote-restart
```

在修改完后，你需要用Ctrl+X+Y的组合键来保存你的修改，然后就完成了

### （可选但非常推荐的步骤）：1.卸载系统更新

```
cd system/system/app/
sudo rm -rf IFlyOTA
```

### （可选但非常推荐的步骤）：2.开启adb

Tips：如果你前一步"卸载系统更新"也进行了，那你需要先执行三次 `cd ..`

```
nano system/system/build.prop
```

用键盘将光标移动在最底下并按几下回车，然后加入以下内容（Tips:把鼠标放到代码框右上角，你会发现有一个复制的按钮，按一下就好，然后在命令行中使用右键进行粘贴即可）：

```
persist.service.adb.enable=1
persist.sys.usb.config=diag,adb,mtp
ro.sys.usb.default.config=diag,adb,mtp
```

在修改完后，你需要用Ctrl+X+Y的组合键来保存你的修改，然后就完成了

### 取消挂载system.img：

```
sudo umount system.img
```

### 刷入system：

```
spd_dump fdl <fdl1> 0x5500 fdl <fdl2> 0x9efffe00 exec write_part system system.img reset
```

### 开机后步骤

#### 安装爱玩机工具箱

电脑在解bootloader那一步用的文件夹里打开cmd
输入

```
adb devices
adb install <你爱玩机的apk文件>
```

工作模式选择Root，给它授权，然后你就可以使用这里面的安装器了（喜

#### 使用爱玩机工具箱备份全分区（救砖可以使用备份的分区

步骤放图片里了，自己看吧
![1](image/README/1.png)
![2](image/README/2.png)
![3](image/README/3.png)

## 衍生教程

### T20Pro

[激活双系统（即dsu）教程](https://github.com/KDXF-BOOM/studentpad-research/blob/main/t20p.md) ——By[@YedLeo1](https://github.com/YedLeo1)

### C10(Pro)

[Yixiyixi666/KDXF-studypad-C10 (github.com)](https://github.com/Yixiyixi666/KDXF-studypad-C10) ——By[@Yixiyixi666](https://github.com/Yixiyixi666)

### 全机型通用教程

[获取OTA全量包](https://github.com/KDXF-BOOM/studentpad-research/blob/main/guide_OTA_full_Get.md)——By[@KawaiiSparkle](https://github.com/KawaiiSparkle)

## 附录：一些资源及其使用方法/作用

#### SPD_Driver

Link：[Download SPD Driver R4.20.4201 (UniSoc Driver) (androiddatahost.com)](https://androiddatahost.com/dsa6h)
国内网盘分流：[到“紫光通用”目录下下载“紫光驱动”即可](http://qutick102.ysepan.com/)

作用：ADB驱动+展讯下载模式的驱动

使用方法：下载安装即可

注：macOS、Linux不需要安装这个东西

#### spd_dump及CVE-2022-38694_unlock_bootloader项目

Link：[GitHub - TomKing062/CVE-2022-38694_unlock_bootloader](https://github.com/TomKing062/CVE-2022-38694_unlock_bootloader)
Spd_Dump工具下载：[到“紫光通用”目录下下载日期最新的spd_dump_dev版本](http://qutick102.ysepan.com/)

作用：提供了第二种进行读写设备分区操作的工具，但它是命令行的；提供了一种强解bootloader的方法（SoC漏洞）；可以用这个读取平板的分区表（数据单位为MB）

用法

固定部分(这部分复制粘贴就行)

```
spd_dump fdl fdl1.bin 0x5500 fdl fdl2.bin 0x9efffe00 exec
```

命令部分(需要在exec后面空格后输入)：

---

读取分区表：`partition_list partition.xml`

读分区：`read_part <分区名> 0 <分区大小，或直接填0xFFFFFFFFFFF> <保存的文件名称> `
或者 `read_parts partition.xml`批量读取分区

写分区：`write_part <分区名> <要刷入的镜像>`

擦除分区：`erase_part <分区名>`

执行完操作后重启：`reset`(一般加在命令的末尾即可)

---

技巧：命令的拼接——————只需要将好几个完整命令exec部分后面的东西放在一起（注：如果有reset应该将reset放在命令末尾），下面是一个例子：
问：我有三条命令（见代码块）,要把他们整合成一条，该怎么做？

```
spd_dump fdl fdl1.bin 0x5500 fdl fdl2.bin 0x9efffe00 exec read_part system 0 10G system.img reset
spd_dump fdl fdl1.bin 0x5500 fdl fdl2.bin 0x9efffe00 exec erase_part vbmeta_bak reset
spd_dump fdl fdl1.bin 0x5500 fdl fdl2.bin 0x9efffe00 exec write_part vbmeta_bak vbmeta.img reset
```

答：

---

spd_dump fdl fdl1.bin 0x5500 fdl fdl2.bin 0x9efffe00 exec `read_part system 0 10G system.img` `erase_part vbmeta_bak` `write_part vbmeta_bak vbmeta.img reset`

---

#### 学习机配置及目前玩机进度一览表

| 学习机型号 | 系统版本    | 运/储存配置 | soC型号            | 是否可以安装第三方APP | 是否可以进行Root                | 备注                                                                                        | TWRP                   |
| ---------- | ----------- | ----------- | ------------------ | --------------------- | ------------------------------- | ------------------------------------------------------------------------------------------- | ---------------------- |
| T10        | Android 9.0 | 8+256       | （展讯）ud710_2h10 | Y                     | Y                               |                                                                                             | 已成功编译，但刷不进去 |
| X2Pro      | Android 9.0 | 4+128       | （展讯）ud710_2h10 | Y                     | Y                               |                                                                                             | 没设备树               |
| X3Pro      | Android 9.0 | 8+256       | （展讯）ud710_2h10 | Y                     | ？                              | 操作人员刷了C6的系统，后面就没进展了                                                        |                        |
| T20        | Android 9.0 | 8+256       | （展讯）ud710_2h10 | ？                    | N                               | 卡在进download，操作人员的机器没有反应                                                      |                        |
| X1Pro      | Android 9.0 | ？          | 高通芯片           | Y                     | Y                               | Root教程在[X1 PRO - 研究导航 - 小白向supersuroot.github.io](https://supersuroot.github.io/)    |                        |
| C6         | Android 9.0 | ？          | （展讯）ud710_2h10 | Y（毕业后官刷）       | N（有多人测试后反应不行）       | 校园版请毕业后再折腾                                                                        |                        |
| T20Pro     | Android 12L | 8+512       | （瑞芯微）RK3588   | Y                     | ？（可以使用自带root的DSU镜像） | 目前仅可以使用DSU进行提取且无法进行BL解锁（被隐藏了），我们正在试图用另一种方式实现这个功能 | 已成功编译，但刷不进去 |
| X3-5G      | Android 12  | ？          | 高通 骁龙778G      | Y                     | N                               | 泄露文档中说这个是拿Lenovo TB-J607Z改的                                                     |                        |

交流群组：点击链接加入群聊【IFLYTEK-BOOM】：https://qm.qq.com/q/x0rW2tPXVe

## Contributors | 贡献者名单

[@KawaiiSparkle](https://github.com/KawaiiSparkle)/[@qwqlemon2333](https://github.com/qwqlemon2333)一起编写了伪造apk更新包教程+Root教程； <br>
[@Tomking062](https://github.com/Tomking062)提供了Root的思路 <br>
[@whhh233](https://github.com/whhh233)为我们免费提供了网盘来存放文件 <br>
[@WalleoAndrew](https://github.com/WalleoAndrew)最初开始搞科大AI学习机解除安装限制的人 <br>
[@YedLeo1](https://github.com/YedLeo1)正在研究T20Pro解锁BL，他编写了T20Pro的DSU食用方法，在[本项目下的t20p.md中](https://github.com/KDXF-BOOM/studentpad-research/blob/main/t20p.md) <br>
[@LYao2514](https://github.com/LYao2514)正在创作一键自动patch系统分区的脚本 <br>
[@MC220C](https://github.com/MC220C)教了我一种新的高效率提取分区方法 <br>


## 常见Q&A

Q1：如何进入榜单？<br>
A1：你得做足够大的贡献才行 <br>
Q2：我还是不会破解怎么办 <br>
A2：请确保你先学会**spd_dump程序命令，Linux系统基础命令（包括nano,mount,sudo,包管理器,cp,chmod,chown,chcon的命令），计算机基础知识，搜索引擎的使用**再试试，实在不行你把这页内容扔给chatGPT，然后问它也行（<br>
