---
title: "Incorrect Intel 3165 driver status in Software&amp;Updates on dual boot Ubuntu 20.04"
date: 2020-05-21
forum: Networking &amp; Wireless
---

### Post by y.vitiuk on 2020-05-21
Hi, Ubuntu community. 
I've got an issue with the wifi card(Intel Wireless AC 3165) drivers detection on Ubuntu 20.04: 
though the device is able to provide internet connection and is powered on(and even has kernel module loaded), 
the "Software&Updates" tab "Additional Drivers" is showing "The device is not working" message near the "Intel Corporation: Wireless 3165" driver. 

Here's the prerequisites:
1. I've installed Ubuntu 20.04 on my Dual-boot notebook Dell Inspiron 7559 with Windows 10 default OS.
2. After starting to check the system default drivers, I've noticed this error inside "Software&Updates" UI application's tab "Additional Drivers" - ***Intel Corporation: Wireless 3165; The device is not working.***
3. After starting to investigate deeper into the issue fix(and into kernel/drivers of Ubuntu 20.04, which I'm newbie in), I haven't found any EXPLANATION of this message NOR the reason for it, according to current system kernel's driver details output 

*_**Question1**_*: Why the driver status inside "Additional Drivers" tab is "The device is not working"([screen.jpeg]("https://i.imgur.com/7ILFptF.png")), but the Wi-Fi connection is working correctly and the module is loaded into kernel?

According to this I need a help regarding specifics of Dell+Intel Wifi <-> Ubuntu Kernel(Modules, Drivers) loading/unloading/troubleshooting. 
My assumption is that the driver is working correctly, but the "Software&Updates" have some BUG or incorrect driver status detection, related to Intel Wi-Fi card and Kernel/OS.

Here's why. 
My setup:
 - Kernel version(`uname -r`): 5.4.0-31-generic
 - OS: Ubuntu 20.04 **LTS **Desktop
 - Wifi card - Intel 3165AC + BT4.2 [802.11ac + Bluetooth 4.2, Dual Band 2. 4&5 GHz, 1x1]
- Video: NVIDIA GeForce GTX 960M+Mesa Intel® HD Graphics 530 (SKL GT2) # posting it due to *(see ref. 1 below)

What I've already check:
 1. According to Intel driver [recommendations]("https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html")(1) and kernel compatibility [docs]("https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#d_3165_and_3168_support")(2) the supported versions of driver are:
 - iwlwifi-7265-ucode-25.30.14.0.tgz # with 7265-14.ucode inside. compatible with kernel [COLOR=#555555][FONT=intel-clear]4.2+[/FONT][/COLOR]. archive downloaded from [www.intel.com](www.intel.com) table's link(1)
 - iwlwifi-7265-ucode-16.242414.0.tgz # with 7265-16.ucode inside. compatible with kernel [COLOR=#555555][FONT=intel-clear]4.3+. [/FONT][/COLOR]archive downloaded from wireless.wiki.kernel.org table's link(2)
which I've prepared for setup. 
1.1 But before that, I've checked this [tutorial]("https://codeyarns.com/2017/02/04/how-to-make-intel-wireless-ac-3165-work-in-ubuntu/") related to 18.04 issues, which solves the issue by updating HWE & AC according to Official Ubuntu [LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") or by updating kernel. 
According to this tutorial, I've:
 >sudo apt-get install linux-generic-hwe-20.04 # though it's already included in 20.04 LTS 
 >sudo apt-get install **xserver-xorg-hwe-18.04 # **for 20.04 this is the latest version of X(<- using [search]("https://ubuntu.pkgs.org/20.04/ubuntu-universe-amd64/xserver-xorg-hwe-18.04_14.5_amd64.deb.html"))
BUT THE ISSUE REMAINS even after _*reboot*_. 
1.2 According to Ubuntu 20.04 shipped drivers 7265-*.ucode even newer one(iwlwifi-7265-17.ucode) IS ALREADY present by default:
 > ls -l /lib/firmware/iwlwifi-7265-*ucode
```
-rw-r--r-- 1 root root  736844 &#1073;&#1077;&#1088; 19 18:37 /lib/firmware/iwlwifi-7265-10.ucode
-rw-r--r-- 1 root root  880604 &#1073;&#1077;&#1088; 19 18:37 /lib/firmware/iwlwifi-7265-12.ucode
-rw-r--r-- 1 root root  885224 &#1073;&#1077;&#1088; 19 18:37 /lib/firmware/iwlwifi-7265-13.ucode
-rw-r--r-- 1 root root 1180412 &#1073;&#1077;&#1088; 19 18:37 /lib/firmware/iwlwifi-7265-17.ucode
-rw-r--r-- 1 root root  690452 &#1073;&#1077;&#1088; 19 18:37 /lib/firmware/iwlwifi-7265-8.ucode
-rw-r--r-- 1 root root  697828 &#1073;&#1077;&#1088; 19 18:37 /lib/firmware/iwlwifi-7265-9.ucode
```
which should be good, but is more strange. 

2. my current network hardware output is:
 > lshw -C network
```
*-network
       description: Wireless interface
       product: Wireless 3165
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: _*wlp5s0*_
       version: **79**
       serial: --:d4:--:7b:--:--
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=**iwlwifi** driverversion=5.4.0-31-generic firmware=**29.1654887522.0** ip=192.168.0.103 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:134 memory:df200000-df201fff

```
and wifi is on(using which I'm writing this post :) ):
 > iwlist *_wlp5s0_* power
```

wlp5s0    Current mode:on

``` 
where *wlp5s0* is my active network interface:
 > ifconfig
```

...
wlp5s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.103  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::9807:2d2f:1f32:a663  prefixlen 64  scopeid 0x20<link>
        ether --:d4:--:7b:--:--  txqueuelen 1000  (Ethernet)
        RX packets 26545  bytes 25092442 (25.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 16299  bytes 4335368 (4.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```
and the driver/kernel module/pci is loaded:
 > lsmod | grep wifi
```
iwlwifi               331776  1 iwlmvm
cfg80211              704512  3 iwlmvm,iwlwifi,mac80211

```
> modinfo iwlwifi
```
filename:       /lib/modules/5.4.0-31-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
...
firmware:       iwlwifi-7265-17.ucode
...
depends:        cfg80211retpoline:      Y
intree:         Y
name:           iwlwifi
vermagic:       5.4.0-31-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
...

```
 > lspci 
```
**05:00.0 **Network controller: Intel Corporation Wireless 3165 (rev 79)
``` 

> find /sys | grep drivers.*05:00
```
/sys/bus/pci/drivers/**iwlwifi**/0000:05:00.0
```

> dmesg | grep iwlwifi
```

[    3.069974] iwlwifi 0000:05:00.0: enabling device (0000 -> 0002)
[    3.078870] iwlwifi 0000:05:00.0: Found debug destination: EXTERNAL_DRAM
[    3.078872] iwlwifi 0000:05:00.0: Found debug configuration: 0
[    3.079032] iwlwifi 0000:05:00.0: loaded firmware version 29.1654887522.0 op_mode iwlmvm
[    3.157078] iwlwifi 0000:05:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[    3.170897] iwlwifi 0000:05:00.0: Applying debug destination EXTERNAL_DRAM
[    3.171320] iwlwifi 0000:05:00.0: Allocated 0x00400000 bytes for firmware monitor.
[    3.178016] iwlwifi 0000:05:00.0: base HW address: --:d4:--:7b:--:-- 
[    3.460305] iwlwifi 0000:05:00.0 wlp5s0: renamed from wlan0
[    5.037076] iwlwifi 0000:05:00.0: Applying debug destination EXTERNAL_DRAM
[    5.126592] iwlwifi 0000:05:00.0: Applying debug destination EXTERNAL_DRAM
[    5.128097] iwlwifi 0000:05:00.0: FW already configured (0) - re-configuring
[ 1546.190248] iwlwifi 0000:05:00.0: Applying debug destination EXTERNAL_DRAM
[ 1546.270358] iwlwifi 0000:05:00.0: Applying debug destination EXTERNAL_DRAM
[ 1546.272013] iwlwifi 0000:05:00.0: FW already configured (0) - re-configuring

```

3. After downgrading to 16th - iwlwifi-7265-ucode-25.30.14.0.tgz:

sudo modprobe -r iwlmvm && sudo modprobe -r iwlwifi && sudo mv /lib/firmware/iwlwifi-7265-17.ucode ~/
sudo cp ~/Downloads/iwlwifi-7265-ucode-16.242414.0/iwlwifi-7265-16.ucode /lib/firmware/
sudo modprobe iwlwifi
dmesg | grep iwlwifi

```

[14186.506626] iwlwifi 0000:05:00.0: Found debug destination: EXTERNAL_DRAM
[14186.506627] iwlwifi 0000:05:00.0: Found debug configuration: 0
[14186.506806] iwlwifi 0000:05:00.0: loaded firmware version 29.1654887522.0 op_mode iwlmvm
[14186.526517] iwlwifi 0000:05:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[14186.540705] iwlwifi 0000:05:00.0: Applying debug destination EXTERNAL_DRAM
[14186.541064] iwlwifi 0000:05:00.0: Allocated 0x00400000 bytes for firmware monitor.
[14186.555701] iwlwifi 0000:05:00.0: base HW address: --:d4:--:7b:--:-- 
[14186.636289] iwlwifi 0000:05:00.0 wlp5s0: renamed from wlan0
[14186.702876] iwlwifi 0000:05:00.0: Applying debug destination EXTERNAL_DRAM
[14186.789316] iwlwifi 0000:05:00.0: Applying debug destination EXTERNAL_DRAM
[14186.790908] iwlwifi 0000:05:00.0: FW already configured (0) - re-configuring
[14186.843296] iwlwifi 0000:05:00.0: Applying debug destination EXTERNAL_DRAM
[14186.922345] iwlwifi 0000:05:00.0: Applying debug destination EXTERNAL_DRAM
[14186.923904] iwlwifi 0000:05:00.0: FW already configured (0) - re-configuring

```
sudo modprobe -r iwlmvm && sudo modprobe -r iwlwifi && mv ~/iwlwifi-7265-17.ucode /lib/firmware/  
sudo rm -rf /lib/firmware/iwlwifi-7265-16.ucode && modprobe iwlwifi
 
and rebooting, THE ISSUE STILL REMAINS.

3.1. and to 14th - iwlwifi-7265-ucode-25.30.14.0.tgz:
sudo modprobe -r iwlmvm && sudo modprobe -r iwlwifi && sudo mv /lib/firmware/iwlwifi-7265-17.ucode ~/
sudo cp ~/Downloads/iwlwifi-7265-ucode-25.30.14.0/iwlwifi-7265-14.ucode /lib/firmware/
sudo modprobe iwlwifi
dmesg | grep iwlwifi

```
[14765.135426] iwlwifi 0000:05:00.0: Found debug destination: EXTERNAL_DRAM
[14765.135428] iwlwifi 0000:05:00.0: Found debug configuration: 0
[14765.135654] iwlwifi 0000:05:00.0: loaded firmware version 29.1654887522.0 op_mode iwlmvm
[14765.156436] iwlwifi 0000:05:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[14765.170501] iwlwifi 0000:05:00.0: Applying debug destination EXTERNAL_DRAM
[14765.171135] iwlwifi 0000:05:00.0: Allocated 0x00400000 bytes for firmware monitor.
[14765.184093] iwlwifi 0000:05:00.0: base HW address: --:d4:--:7b:--:-- 
[14765.262389] iwlwifi 0000:05:00.0 wlp5s0: renamed from wlan0
[14765.311863] iwlwifi 0000:05:00.0: Applying debug destination EXTERNAL_DRAM
[14765.389894] iwlwifi 0000:05:00.0: Applying debug destination EXTERNAL_DRAM
[14765.391277] iwlwifi 0000:05:00.0: FW already configured (0) - re-configuring
[14765.436351] iwlwifi 0000:05:00.0: Applying debug destination EXTERNAL_DRAM
[14765.516862] iwlwifi 0000:05:00.0: Applying debug destination EXTERNAL_DRAM
[14765.518472] iwlwifi 0000:05:00.0: FW already configured (0) - re-configuring
```
sudo modprobe -r iwlmvm && sudo modprobe -r iwlwifi && mv ~/iwlwifi-7265-17.ucode /lib/firmware/ 
sudo rm -rf /lib/firmware/iwlwifi-7265-14.ucode && modprobe iwlwifi
 
and rebooting, THE ISSUE STILL REMAINS.

*_**Question2**_*: If the fix with "Additional drivers" tab doesn't relate to kernel drivers, are there any possibility to switch radio-button to "Continue using manually installed driver" and enable "Apply changes" button?

(*) Ref. 1: nVidia/Intel video cards(discrete&integrated one) are working on stock drivers(nvidia-440 proprietary&Mesa with i915 kernel module respectively). Also cuda 10-2 [metapackage]("https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=debnetwork")(for 18.04 as for now) is installed and tested by running samples(though with minor _build issues)_ successfully. 
This info is "for general information" regarding another drivers, which operates better. Please take this into account if that is necessary.  

UPDATE: 
according to 
> modinfo iwlwifi  | more
filename:       /lib/modules/5.4.0-31-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
...
firmware:       iwlwifi-6000-6.ucode
firmware:       iwlwifi-7265D-29.ucode
**firmware:       iwlwifi-7265-17.ucode **# the downloaded firmware isn't detected by iwlwifi module as it isn't present in output of this command, is it?
firmware:       iwlwifi-3168-29.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
...
though, 
> ls -l /lib/firmware/iwlwifi-7265-*ucode
```
-rw-r--r-- 1 root root  736844 &#1073;&#1077;&#1088; 19 18:37 /lib/firmware/iwlwifi-7265-10.ucode-rw-r--r-- 1 root root  880604 &#1073;&#1077;&#1088; 19 18:37 /lib/firmware/iwlwifi-7265-12.ucode
-rw-r--r-- 1 root root  885224 &#1073;&#1077;&#1088; 19 18:37 /lib/firmware/iwlwifi-7265-13.ucode
**-rw-r--r-- 1 root root 1180224 &#1090;&#1088;&#1072; 21 21:19 /lib/firmware/iwlwifi-7265-14.ucode**
-rw-r--r-- 1 root root  690452 &#1073;&#1077;&#1088; 19 18:37 /lib/firmware/iwlwifi-7265-8.ucode
-rw-r--r-- 1 root root  697828 &#1073;&#1077;&#1088; 19 18:37 /lib/firmware/iwlwifi-7265-9.ucode
```
firmware was replaced in firmware folder.

Why 14th *.ucode file wasn't loaded by firmware? 
Should *ucode files be loaded using special procedure? Eg: using special runlevel or with additional files or by stopping wifi/unloading module?
According to this [docs]("https://software.intel.com/en-us/node/721517")(FOR ANOTHER intel wifi card), see Section "[FONT=&amp]Files Copied to Root", the additional *.ko file should be supplied with Intel card - [/FONT][COLOR=#FFFFFF][FONT=&amp]/[/FONT][/COLOR][COLOR=#FFFFFF][FONT=&amp]lib/modules/<kernel_version>/updates/iwlwifi.ko
[/FONT][/COLOR][FONT=&amp]But current /[/FONT]lib/modules/5.4.0-31-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko do exist.

---

### Post by chili555 on 2020-05-21
> My assumption is that the driver is working correctly, but the "Software&Updates" have some BUG or incorrect driver status detection, related to Intel Wi-Fi card Yes, indeed, it is a bug. You may safely ignore it. As you noted, your wireless is working properly and so there is no need to &#8220;fix&#8221; it.

You can fiddle with the firmware all you want and you can&#8217;t and won&#8217;t change Additional Drivers; you might, however, stop your wireless from working.

---

### Post by chili555 on 2020-05-22
I wrote the above post from my bedroom and the response was short. I now have other observations.

First:

> iwlwifi-7265-ucode-16.242414.0.tgz # with 7265-16.ucode inside. 

And it also has 7265D inside. That's entirely consistent with the link you gave which says:

> Those devices will not be supported by the newest firmware versions: the last firmware that was released for 3160, 7260 and 7265 is -17.ucode. Bug fixes will be ported to -17.ucode. 7265D, **3165 **and 3168's latest firmware version is -29.ucode. In order to determine if your 7265 device is a 'D' version, you can check the dmesg output:

Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
The revision number of a 7265D device is 0x210, if you see any other number, you have a 7265 device.

And you have:

> Detected Intel(R) Dual Band Wireless AC 3165, REV=0x[COLOR="#FF0000"]210[/COLOR]
Therefore, the latest firmware for your device is not the old iwlwifi-7265-17.ucode but, instead, the newer iwlwifi-7265[COLOR="#FF0000"]D[/COLOR]-29.ucode. In fact, the version number -29 corresponds to what is actually loaded:

> loaded firmware version [COLOR="#FF0000"]29[/COLOR].1654887522.0 op_mode iwlmvm
Also:

> sudo cp ~/Downloads/iwlwifi-7265-ucode-16.242414.0/iwlwifi-7265-16.ucode [COLOR="#FF0000"]/lib/firmware/[/COLOR] In later Ubuntu versions, starting at 20.04, firmware is at /usr/lib/firmware. Please recheck your location.

The iwlwifi driver looks at pci.ids, which you can find with:

```
lspci -nnk | grep 0280
```

As an example, here is the data from my machine:

```
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [[COLOR="#FF0000"]8086:08b2[/COLOR]] (rev 83)

```
So the driver, seeing a pci.id, 8086:08b2, for example, that's included therein, loads and then looks for firmware. Finding the appropriate firmware, it creates a wireless interface, Network Manager uses it to get a connection and everything is then working as expected.

However, none of this at all is going to fix the bug in Additional Drivers. You are encouraged to find and add to the bug report here: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) After that, I recommend that you do what I do: ignore it and enjoy  your wireless.

I do congratulate you on your thorough investigation into the mysteries and vagaries of Intel wireless firmware! It is mostly correct but wholly unrelated to the bug.

---

### Post by chili555 on 2020-05-22
> and wifi is on(using which I'm writing this post  ):
> iwlist wlp5s0 power
Code:
wlp5s0    Current mode:onIn this context, Power:on refers to power management; that is, the ability of the device to power down when not under a load and, most crucially, to power back up properly when needed. Learn more from the terminal command:

```
man iwlist
```> **power**
List the various Power Management attributes and modes of the device.



---

### Post by y.vitiuk on 2020-05-23
> **chili555 said:**
> Yes, indeed, it is&nbsp;a bug. 
1) Do you assume it the same as I do?
or
2) Does that mean than Intel drivers are missing implementation of generic functionality required from "Additional Drivers" ui window "presenter"(see MVP) side or from inner dependency - library/shell/kernel api/"driver management system design"?
Or do "Additional Drivers" window implementation is lack of code-base update due to further-released improvements from driver dev team or inner dependency?
Or in short: "What component in this OS feature is lack of dependency update?"


> **chili555 said:**
> You may safely ignore it. As you noted, your wireless is working properly and so there is no need to “fix” it.
In fact No, as I've got a question in post's update. Please check it and sorry for that: "Why 14th *.ucode file wasn't loaded by firmware?...."

> **chili555 said:**
> you might, however, stop your wireless from working.
In order to prove that there's a bug in Ui window, I can try to switch-off card's power and check that there's no errors on "Additional Drivers" UI. 
I would appreciate if you share a shell command for that or any other TLP like utility(which I'm investigating now :idea:) for that task, as currently I've only googled this SE's [answer]("https://unix.stackexchange.com/questions/269661/how-to-turn-off-wireless-power-management-permanently"), which seems not solve the issue(powersave != poweroff).

---

### Post by chili555 on 2020-05-23
> "Why 14th *.ucode file wasn't loaded by firmware?...."

Because it is incorrect for your 0x210 device, as I said and as a link you gave in your original question clearly shows.

> In order to prove that there's a bug in Ui window, I can try to switch-off card's power and check that there's no errors on "Additional Drivers" UI.

Why do you suppose that turning off power management proves that there is a bug in the Additional Drivers utility? I do not. However, if you'd like to test:

```
sudo iwconfig wlp5s0 power off

```
Verify:

```
iwconfig
```

You should see something like:

```
wlp5s0    IEEE 802.11  ESSID:"my_lil_router"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: xx:xx:xx
          Bit Rate=866.7 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
         [COLOR="#FF0000"] Power Management:**off**[/COLOR]
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:494   Missed beacon:0
```
          
Did that magically fix Additional Drivers? I don't think so.

> which seems not solve the issue(powersave != poweroff).

Why do you want to turn power management off at all? Is your card not recovering from idle periods properly? My Intel does and I think it is a useful feature particularly on battery power.

>  "What component in this OS feature is lack of dependency update?"   
 
 I'm not a kernel developer nor a driver developer. I don't know what the root problem is. If I did, I'd have already submitted a patch to fix the bug and fielded a juicy job offer from Intel.

I suggest that you add to the bug report here: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1859308](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1859308)

---

### Post by y.vitiuk on 2020-05-30
> In this context, Power:on refers to power management; that is, the ability of the device to power down when not under a load and, most crucially, to power back up properly when needed. 

Thanks a lot for update and sharing a knowledge. In general I wanted to show that the wifi card is *enabled*, without knowing the better way to do that. 
But in general regarding this update  - in the next post, which I've wrote after your observations and further update(without checking the update :) ), I've mentioned that 

>  powersave != poweroff

as a warning. By this I wanted to note, that powering off isn't possible by switching power management to "off" (of course if you aren't' going to trigger power-off somehow(in power:on mode) by DDOSing a card or by disabling it and make a candidate for powering off :) ). 
At least from my knowledge perspective :) 


> Because it is incorrect for your 0x210 device, as I said and as a link you gave in your original question clearly shows.

Just check the possibility to load 7265D-16.ucode driver and *_get the error_*:

Updated version loading code:
> sudo modprobe -r iwlwifi && sudo mv /usr/lib/firmware/iwlwifi-7265D-29.ucode ~/
sudo cp ~/Downloads/iwlwifi-7265-ucode-16.242414.0/iwlwifi-7265D-16.ucode /usr/lib/firmware/
ls -l /usr/lib/firmware/iwlwifi-7265D-*.ucode
echo "loading 7265D-16.ucode"
sudo modprobe iwlwifi
echo "loaded"
dmesg | grep iwlwifi
sleep 2s
sudo modprobe -r iwlwifi && mv ~/iwlwifi-7265D-29.ucode /usr/lib/firmware/
sudo rm -rf /usr/lib/firmware/iwlwifi-7265D-16.ucode && modprobe iwlwifi


resulted in next output:
> 
# output of   > ls -l /usr/lib/firmware/iwlwifi-7265D-*.ucode
lrwxrwxrwx 1 root    root         21 &#1090;&#1088;&#1072; 20 12:48 /usr/lib/firmware/iwlwifi-7265D-10.ucode -> iwlwifi-7265-10.ucode
-rw-r--r-- 1 root    root    1002800 &#1073;&#1077;&#1088; 19 18:37 /usr/lib/firmware/iwlwifi-7265D-12.ucode
-rw-r--r-- 1 root    root    1008692 &#1073;&#1077;&#1088; 19 18:37 /usr/lib/firmware/iwlwifi-7265D-13.ucode
**-rw-rw-r-- 1 root root 1384500 &#1075;&#1088;&#1091; 23  2015 /usr/lib/firmware/iwlwifi-7265D-16.ucode**
....
# dmesg output
[ 6182.451629] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7265D-29.ucode failed with error -2
[ 6182.451640] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7265D-28.ucode failed with error -2
[ 6182.451658] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7265D-27.ucode failed with error -2
[ 6182.451671] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7265D-26.ucode failed with error -2
[ 6182.451683] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7265D-25.ucode failed with error -2
[ 6182.451696] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7265D-24.ucode failed with error -2
[ 6182.451707] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7265D-23.ucode failed with error -2
[ 6182.451718] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-7265D-22.ucode failed with error -2
***[ 6182.451719] iwlwifi 0000:05:00.0: _no suitable firmware found!_***
[I][ 6182.451722] iwlwifi 0000:05:00.0: minimum version required: iwlwifi-7265D-22
[ 6182.451723] iwlwifi 0000:05:00.0: maximum version supported: iwlwifi-7265D-29[/I]
[ 6182.451724] iwlwifi 0000:05:00.0: check git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git


...

This error still persist after rename of 16 to 22(minimum required) *.ucode file and reload with modprobe:
>sudo mv /usr/lib/firmware/iwlwifi-7265D-16.ucode /usr/lib/firmware/iwlwifi-7265D-22.ucode
>sudo modprobe iwlwifi

In this case 
> dmesg | grep iwlwifi 
have no updates in output.


> Why do you suppose that turning off power management proves that there is a bug in the Additional Drivers utility? I do not. However, if you'd like to test:
To be short, by this I want to check whether the "switching-off-by-software-turn-off"(<-by this I mean to physically pull of a card, which isn't worth it and easy task for this case) would cause a message "The device is not working" to **_disappear_** from tab,
but by "causing a disabling of a driver if the device isn't connected" and therefore to proove that this label is based on the driver-driven-logic-in-ui-presenter, but not due to other side-effect.

---

### Post by y.vitiuk on 2020-05-30
> I suggest that you add to the bug report here: [https://bugs.launchpad.net/ubuntu/+s...n/+bug/1859308](https://bugs.launchpad.net/ubuntu/+s...n/+bug/1859308)

Super! Thanks a lot for this link - this is just what I've been googling for without knowing the right place :) 

Just post a comment with a link to this thread [-o< 

> If the fix with "Additional drivers" tab doesn't relate to kernel drivers, are there any possibility to switch radio-button to "Continue using manually installed driver" and enable "Apply changes" button?

Am I understanding right, that this is also makes not a lot sense in comparison to waiting to bugfix release? 
Will the 7265D-16.ucode(the lower version) driver be detected as manually installed?

---

### Post by chili555 on 2020-05-30
> To be short, by this I want to check whether the "switching-off-by-software-turn-off"(<-by this I mean to physically pull of a card, which isn't worth it and easy task for this case) would cause a message "The device is not working" to disappear from tab,
but by "causing a disabling of a driver if the device isn't connected" and therefore to proove that this label is based on the driver-driven-logic-in-ui-presenter, but not due to other side-effect.No, I strongly doubt that any action that you or I as users can take will cause a message "The device is not working" to disappear from the tab. As I've said several times, it is a known bug.

Powering off the card, which you can easily do with the wireess switch or key combination, is an entirely different operation than power management, the mechanism that reduces power, but not to zero, when the card is momentarily inactive and restores it again upon new activity. Turning the radio down is not the same as turning it off.

Please try the airplane mode switch on your laptop and tell us if the message "The device is not working" has disappeared from the tab,

Again, it's a known bug. We don't know the reason.

> Will the 7265D-16.ucode(the lower version) driver be detected as manually installed?The firmware is a different thing from the driver iwlwifi itself. In the context of the tab that bothers you, it refers to the driver iwlwifi, not the firmware. The version of the driver that you and I have is written for specific firmware versions and none other as you've discovered:

> [ 6182.451722] iwlwifi 0000:05:00.0: [COLOR="#FF0000"]minimum [/COLOR]version required: iwlwifi-7265D-[COLOR="#FF0000"]22[/COLOR]
[ 6182.451723] iwlwifi 0000:05:00.0: [COLOR="#FF0000"]maximum[/COLOR] version supported: iwlwifi-7265D-[COLOR="#FF0000"]29[/COLOR]You have and load -29 if you haven't over-written it.

---

### Post by y.vitiuk on 2020-05-31
> Please try the airplane mode
The message still persist. 

> load -29 if you haven't over-written it.
I've restored them from backup after failed v16 and renamed to v22 load. They're working now.

The firmware is a different thing from the driver iwlwifi itself.
I agree. Here we're loading a firmware which contains iwlwifi/iwlmvm drivers(which interact with hardware firmware).

---

