---
title: "QCA9377 and no wireless network adapter Ubuntu 15.04"
date: 2015-11-25
forum: Networking &amp; Wireless
---

### Post by jettcalleja on 2015-11-25
I'm using acer e5-47G, I tried the instructions given by dr-cono in [http://ubuntuforums.org/showthread.php?t=2300861&page=3](http://ubuntuforums.org/showthread.php?t=2300861&page=3) but [http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2](http://filebin.ca/2LVgpjSgiT56/backports-ath-2015-11-05.tar.bz2) is down so I cant wget the tar.bz2.

[COLOR=#000000]*for lspci *[/COLOR]
[COLOR=#000000]*02:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)*[/COLOR]
[COLOR=#000000][I]03:00.0 Network controller: Qualcomm Atheros Device 0042 (rev 30)

[/I][/COLOR][ATTACH]265770[/ATTACH]

---

### Post by chili555 on 2015-11-25
I have been trying to work this out for quite some time and I'm stuck because I do not have the hardware. You will need to test for us.

With a temporary working internet connection, by ethernet, tethered or whatever means possible, open a terminal and do:```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz
tar -zxvf backports-20151120.tar.gz
cd backports-20151120
make defconfig-ath10k
make
sudo make install
```Reboot and let us see:```
dmesg | grep ath
```

---

### Post by jettcalleja on 2015-11-25
the result of sudo make install 
```

Building modules, stage 2.
  MODPOST 6 modules
  INSTALL /home/chocho/backports-20151120/compat/compat.ko
Can't read private key
  INSTALL /home/chocho/backports-20151120/drivers/net/wireless/ath/ath.ko
Can't read private key
  INSTALL /home/chocho/backports-20151120/drivers/net/wireless/ath/ath10k/ath10k_core.ko
Can't read private key
  INSTALL /home/chocho/backports-20151120/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
Can't read private key
  INSTALL /home/chocho/backports-20151120/net/mac80211/mac80211.ko
Can't read private key
  INSTALL /home/chocho/backports-20151120/net/wireless/cfg80211.ko
Can't read private key
  DEPMOD  4.2.0-18-generic
depmod will prefer updates/ over kernel/ -- OK!
Note:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against "update-initramfs.sh". If your distribution does not
require this send a patch with the '/usr/bin/lsb_release -i -s'
("Ubuntu") tag for your distribution to avoid this warning.

Your backported driver modules should be installed now.

```

is this okay? I'll be back I'll reboot this now.

WOW Thank you so much!! It works now!

Acer- E5-473G QCA9377 for future users :) Thank you!

---

### Post by chili555 on 2015-11-25
Awesome! Glad it's working. You will have helped many searchers.

You have compiled the driver for your current kernel version only. When Update Manager installs a later linux-image, after the required reboot, recompile the driver:```
cd backports-20151120
[COLOR="#FF0000"]make clean[/COLOR]
make defconfig-ath10k
make
sudo make install
```Reboot and it should be working again.

Please retain the file and these instructions for that time.

---

### Post by rinfinity on 2015-11-25
@Chili555

Thanks for helping people out while i was a bit busy to check the forum. Anyways, i can see that yours is a more elegant solution as we get the backport from none other than kernel.org

Thanks again.

---

### Post by chili555 on 2015-11-25
> **rinfinity said:**
> @Chili555

Thanks for helping people out while i was a bit busy to check the forum. Anyways, i can see that yours is a more elegant solution as we get the backport from none other than kernel.org

Thanks again.I'm glad it's working for you all. I actually had no way to find out for sure until a test case, jettcalleja, helped us confirm it.

---

### Post by yakubskiy2002 on 2015-11-26
Hi, guys. Did all the steps described above. Still not working. Could you Heelp me out, please.

yuriy@yuriy-Aspire-E5-573G:~$ dmesg | grep ath
[    2.763569] ath10k_pci 0000:03:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    3.015230] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[    3.015486] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-5.bin failed with error -2
[    3.015491] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-5.bin': -2
[    3.015504] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-4.bin failed with error -2
[    3.015506] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-4.bin': -2
[    3.015514] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-3.bin failed with error -2
[    3.015516] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-3.bin': -2
[    3.015525] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-2.bin failed with error -2
[    3.015527] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-2.bin': -2
[    3.015536] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware.bin failed with error -2
[    3.015538] ath10k_pci 0000:03:00.0: could not fetch firmware (-2)
[    3.015540] ath10k_pci 0000:03:00.0: could not fetch firmware files (-2)
[    3.015542] ath10k_pci 0000:03:00.0: could not probe fw (-2)


yuriy@yuriy-Aspire-E5-573G:~$ lspci
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
00:1c.4 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 (rev e3)
00:1d.0 USB controller: Intel Corporation Wildcat Point-LP USB EHCI Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
03:00.0 Network controller: Qualcomm Atheros Device 0042 (rev 30)
04:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 940M] (rev ff)


yuriy@yuriy-Aspire-E5-573G:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)

---

### Post by chili555 on 2015-11-26
> Direct firmware load for ath10k/QCA9377/hw1.0/firmware-5.bin failed with error -2It looks like you need some firmware. Please open a terminal and do:```
sudo mkdir /lib/firmware/ath10k/QCA9377/
sudo mkdir /lib/firmware/ath10k/QCA9377/hw1.0
```If it reports that the file already exists, that's fine, just continue.

With a temporary working internet connection:```
sudo apt-get install git
git clone https://github.com/kvalo/ath10k-firmware.git
cd ath10k-firmware/QCA9377/hw1.0
sudo cp board.bin  /lib/firmware/ath10k/QCA9377/hw1.0
sudo cp firmware-5.bin_WLAN.TF.1.0-00267-1   /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin
sudo modprobe -r ath10k_pci
sudo modprobe ath10k_pci
```Your wireless should be working; if not, try a reboot.

---

### Post by yakubskiy2002 on 2015-11-26
[chili555]("http://ubuntuforums.org/member.php?u=35909")

Thanks for a quick response.

Have done all steps again. But doesn't work.
Actually directory was present like you said and contains the same file but with different name. Not sure if it help to solve the problem.

yuriy@yuriy-Aspire-E5-573G:/lib/firmware/ath10k/QCA9377/hw1.0$ md5sum firmware5.bin 
568690a62b5e69ec24400bf41eb07aa2  firmware5.bin


yuriy@yuriy-Aspire-E5-573G:/lib/firmware/ath10k/QCA9377/hw1.0$ md5sum firmware-5.bin_WLAN.TF.1.0-00267-1
568690a62b5e69ec24400bf41eb07aa2  firmware-5.bin_WLAN.TF.1.0-00267-1


Here is all the files in directory.
yuriy@yuriy-Aspire-E5-573G:/lib/firmware/ath10k/QCA9377/hw1.0$ ls -la
total 1248
drwxr-xr-x 2 root root   4096 &#1083;&#1080;&#1089; 26 18:02 .
drwxr-xr-x 3 root root   4096 &#1083;&#1080;&#1089; 24 23:47 ..
-rw-r--r-- 1 root root   8124 &#1083;&#1080;&#1089; 26 18:01 board.bin
-rw-r--r-- 1 root root 605908 &#1083;&#1080;&#1089; 26 18:02 firmware5.bin
-rw-r--r-- 1 root root 605908 &#1083;&#1080;&#1089; 25 00:31 firmware-5.bin_WLAN.TF.1.0-00267-1
-rw-r--r-- 1 root root  46142 &#1083;&#1080;&#1089; 25 00:31 notice.txt_WLAN.TF.1.0-00267-1

This command gives the same error even after the reboot

yuriy@yuriy-Aspire-E5-573G:/lib/firmware/ath10k/QCA9377/hw1.0$ dmesg | grep ath
[    2.810428] ath10k_pci 0000:03:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    3.058607] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[    3.063739] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-5.bin failed with error -2
[    3.063746] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-5.bin': -2
[    3.063762] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-4.bin failed with error -2
[    3.063765] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-4.bin': -2
[    3.063799] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-3.bin failed with error -2
[    3.063803] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-3.bin': -2
[    3.063812] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-2.bin failed with error -2
[    3.063814] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware-2.bin': -2
[    3.063823] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/firmware.bin failed with error -2
[    3.063825] ath10k_pci 0000:03:00.0: could not fetch firmware (-2)
[    3.063827] ath10k_pci 0000:03:00.0: could not fetch firmware files (-2)
[    3.063829] ath10k_pci 0000:03:00.0: could not probe fw (-2)


Thanks

---

### Post by chili555 on 2015-11-26
This is all a bit experimental. I haven't the device; I have only a slight knowledge of how these things are supposed to, but often don't, work.

Please see: [http://lists.infradead.org/pipermail/ath10k/2015-November/006403.html](http://lists.infradead.org/pipermail/ath10k/2015-November/006403.html) I think part of the problem was that the driver identified your device as HW_1_0 when it is actually a HW_1_1.> -		.id = QCA9377_HW_1_0_DEV_VERSION,
-		.name = "qca9377 hw1.0",
+		.id = QCA9377_HW_1_1_DEV_VERSION,
+		.name = "qca9377 hw1.1",Let's try to trick the driver. We'll make a new folder hw1.1 and copy over the firmware files. Then reboot and check dmesg.```
sudo mkdir /lib/firmware/ath10k/QCA9377/hw1.1
sudo cp  /lib/firmware/ath10k/QCA9377/hw1.0/*  /lib/firmware/ath10k/QCA9377/hw1.1 
```Cross your fingers and reboot.

---

### Post by chili555 on 2015-11-26
> ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA9377/hw1.0/firmware[COLOR="#FF0000"]**-**[/COLOR]5.bin': -2However, we have:> drwxr-xr-x 2 root root 4096 &#1083;&#1080;&#1089; 26 18:02 .
drwxr-xr-x 3 root root 4096 &#1083;&#1080;&#1089; 24 23:47 ..
-rw-r--r-- 1 root root 8124 &#1083;&#1080;&#1089; 26 18:01 board.bin
-rw-r--r-- 1 root root 605908 &#1083;&#1080;&#1089; 26 18:02 firmware5.bin
-rw-r--r-- 1 root root 605908 &#1083;&#1080;&#1089; 25 00:31 firmware-5.bin_WLAN.TF.1.0-00267-1
-rw-r--r-- 1 root root 46142 &#1083;&#1080;&#1089; 25 00:31 notice.txt_WLAN.TF.1.0-00267-1...with no hyphen. I apologize for the typographical error. I am sorry for my mis-step. Please do:```
cd /lib/firmware/ath10k/QCA9377/hw1.0
sudo mv firmware5.bin  firmware-5.bin
```Reboot.

-----
Thanks, Jeremy. I appreciate the help.

---

### Post by yakubskiy2002 on 2015-11-27
Hi, yes it works after rename of firmware file!!!

[chili555]("http://ubuntuforums.org/member.php?u=35909")[COLOR=#000000]  

[/COLOR]I'm really appreciate your help. 
Many, many thanks!!!

---

### Post by rinfinity on 2015-11-28
Chili555,
Seems the fw nomenclature bug is still there.

Chili555,
Btw, i do have the device and would be glad to help with testing, should the need arise henceforth.

---

### Post by Ravisha_Heshan on 2015-12-13
> **chili555 said:**
> However, we have:...with no hyphen. I apologize for the typographical error. I am sorry for my mis-step. Please do:```
cd /lib/firmware/ath10k/QCA9377/hw1.0
sudo mv firmware5.bin  firmware-5.bin
```Reboot.

-----
Thanks, Jeremy. I appreciate the help.

Thanks chili555. You saved my day

---

### Post by Terone on 2015-12-25
Haha, Thanks everyone. It fixed my wireless too. I'm using Acer Aspire e5-473g-56k4. Finally found this thread after hours of googling. :D

---

### Post by Chikitulfo on 2015-12-28
Thank you very much for this!! 
After following the instructions and copying the firmware I was able to make the wifi work!

However, I'm a bit worried about a kernel upgrade breaking the fix, and having to recompile and reinstall manually again.
This laptop is my father's, and he is not savvy enough to do that by himself, so I was wondering if it is possible to write a command to rebuild the module automatically when a new kernel is installed.

---

### Post by chili555 on 2015-12-28
> **Chikitulfo said:**
> Thank you very much for this!! 
After following the instructions and copying the firmware I was able to make the wifi work!

However, I'm a bit worried about a kernel upgrade breaking the fix, and having to recompile and reinstall manually again.
This laptop is my father's, and he is not savvy enough to do that by himself, so I was wondering if it is possible to write a command to rebuild the module automatically when a new kernel is installed.There probably is, but I haven't any idea how to do it. Scripting isn't my area of limited expertise.

You could easily write commands in /etc/rc.local to recompile every time the machine is booted; something like:```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

cd /home/poppa/backports-20151120
make clean
make defconfig-ath10k
make
make install

exit 0

```However, this will be a bit time consuming, Poppa may complain that it takes three minutes to boot!

You could instead freeze the linux-image package from being updated:```
sudo apt-mark hold linux-image-generic linux-headers-generic

```I think the best approach is to install a later mainline kernel that includes the driver and won't be updated by Update Manager.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3.3-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.3.3-wily/)

If you need a step-by-step, post back and I'll be happy to help.

---

### Post by andrea96 on 2016-01-01
Hello.

I have an Acer Aspire E5-574G-57ZD.

I have been trying to install Ubuntu for almost a month now. Ubuntu is working fine, Wlan is not. .


I have followed the advice given in the first 10 answers to this thread. 


When I type: 

dmesg | grep ath


There is no output.


Yet I still do not have wlan, even after a reboot.


Please, could anyone help me?


Thanks a lot

---

### Post by jeremy31 on 2016-01-01
Post ```
lspci -nnk | grep -iA2 net; uname -a
```

---

### Post by andrea96 on 2016-01-02
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Acer Incorporated [ALI] Device [1025:100c]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
    Subsystem: Lite-On Communications Inc Device [11ad:0806]
Linux anweber-Aspire-E5-574G 4.2.0-22-generic #27-Ubuntu SMP Thu Dec 17 22:57:22 UTC 2015 i686 i686 i686 GNU/Linux

The thing is, I had it working on the bootstick yesterday by following first your post and then afterwards
[http://askubuntu.com/questions/701350/qualcomm-atheros-qca9377-wireless-not-working-on-lenovo-with-14-04-3](http://askubuntu.com/questions/701350/qualcomm-atheros-qca9377-wireless-not-working-on-lenovo-with-14-04-3)

But I then had to use another bootstick for installation.

With this one I tried what is in the link first, to no avail. 

I do not seem to have the firmwareproblem though, as I am not getting these errors.

Now I am sorry I wrote this post.

I followed through with the post I linked and then with what you recommended and now it works like a charm. 
So do not trouble yourself over my post.

This is Acer Aspire E 5-574g-57ZD



And thank you thank you thank you so much for these posts!

---

### Post by algo-fh on 2016-01-05
Hi Guys,

I followed the instructions - still a problem - looks like some firmware files are still missing
(using Xubuntu 14.04)

I see now all WLAN's but I cannot connect. It keeps asking for the WPA-Key. The key is copy/pasted from the working Realtek connection.
A strange thing is when it's asking for the WPa-Key. In the Dialog is a dropdown for the "Funknetzwerkkarte" (Wlan adapter) -> in the dropdown is listed the Realtek and always preselected some strange string in the Screenshot "dhcp_message_type" should be probably the "Atheros".
When I select in this menu the Realtek it comes up again and asks for the WPA-Key.

Output: wireless-info:
[http://paste.ubuntu.com/14409191/](http://paste.ubuntu.com/14409191/)

output of dmesg | grep ath

[    0.605362] Loaded X.509 cert 'Magrathea: Glacier signing key: 759bcd6455a9dfaba6111485d04eded53ab83150'
[    1.831643] ath10k_pci 0000:03:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    2.074572] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[    2.138334] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/board-2.bin failed with error -2
[    2.574245] Path A IQK Success!!
[    2.577367] Path A IQK Success!!
[    2.578851]  Path A IQ Calibration Success !
[    3.912746] ath10k_pci 0000:03:00.0: qca9377 hw1.0 (0x05020000, 0x003820ff sub 105b:e09a) fw WLAN.TF.1.0-00267-1 fwapi 5 bdapi 1 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
[    3.912751] ath10k_pci 0000:03:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[    3.914609] ath: EEPROM regdomain: 0x6c
[    3.914612] ath: EEPROM indicates we should expect a direct regpair map
[    3.914615] ath: Country alpha2 being used: 00
[    3.914616] ath: Regpair used: 0x6c
[  158.289016] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[  284.889751] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!

---

### Post by chili555 on 2016-01-05
I will be nearly impossible to simultaneously troubleshoot with two devices competing with each other. Please detach the Realtek, reboot and try again. Try to connect and if you are unsuccessful, let us see another wireless script.

---

### Post by algo-fh on 2016-01-05
I rebooted only with the qca9377 device and a LAN you find the wireless-info here:
[http://paste.ubuntu.com/14413137/](http://paste.ubuntu.com/14413137/)

The output of dmesg | grep ath
[    2.992082] Loaded X.509 cert 'Magrathea: Glacier signing key: 759bcd6455a9dfaba6111485d04eded53ab83150'
[    3.985449] ath10k_pci 0000:03:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    4.241897] ath10k_pci 0000:03:00.0: Direct firmware load for [COLOR=#ff0000]ath10k/cal-pci-0000:03:00.0.bin failed with error -2[/COLOR]
[    4.331598] ath10k_pci 0000:03:00.0: Direct firmware load for [COLOR=#ff0000]ath10k/QCA9377/hw1.0/board-2.bin failed with error -2[/COLOR]
[    6.107391] ath10k_pci 0000:03:00.0: qca9377 hw1.0 (0x05020000, 0x003820ff sub 105b:e09a) fw WLAN.TF.1.0-00267-1 fwapi 5 bdapi 1 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
[    6.107397] ath10k_pci 0000:03:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[    6.109009] ath: EEPROM regdomain: 0x6c
[    6.109011] ath: EEPROM indicates we should expect a direct regpair map
[    6.109013] ath: Country alpha2 being used: 00
[    6.109014] ath: Regpair used: 0x6c
[    6.120779] ath10k_pci 0000:03:00.0 wlan1: renamed from wlan0
[  184.521246] Path A IQK Success!!
[  184.524450] Path A IQK Success!!
[  184.525955]  Path A IQ Calibration Success !
[  224.139275] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[  269.046211] Path A IQK Success!!
[  269.049337] Path A IQK Success!!
[  269.053731] Path A IQK Success!!
[  269.055221]  Path A IQ Calibration Success !

---

### Post by chili555 on 2016-01-05
It looks awesome to me! It creates an interface,in your case, wlan1. It scans and sees networks. It probably won't connect because Network Manager defaults to ethernet if available as it's often faster and always more secure.

I assume this is your network:> wlan1     Scan completed :
          Cell 01 - Address: <MAC 'fs' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"fs"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000007f5ed08f
                    Extra: Last beacon: 4584ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSKMost Linux drivers don't like TKIP and they don't like WPA and WPA2 mixed mode.

WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Reboot with the ethernet detached and tell us if you connect.

---

### Post by algo-fh on 2016-01-06
changed the router configuration as recommended.

Changed the country code.

Tried without wired connection ... no connection
Connection with my USB-Realteak possible

The new output of wireless-info:
[http://paste.ubuntu.com/14419220/](http://paste.ubuntu.com/14419220/)

I added the screenshot of my fritzbox (router configuration)
By the way I had 5 different Xubuntu Laptops int the old configuration running, without problems.

---

### Post by chili555 on 2016-01-06
Let's try a driver parameter:```
sudo -i
echo "options ath10k_core skip_otp=y"  >  /etc/modprobe.d/ath10k.conf
exit
```Reboot with the ethernet detached and if you cannot connect, paste for us:```
dmesg | grep -e ath10 -e wlan
```

---

### Post by algo-fh on 2016-01-06
Didn't connect:

Output of:
dmesg | grep -e ath10 -e wlan

[    4.793366] ath10k_pci 0000:03:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    5.052739] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[    5.118811] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/board-2.bin failed with error -2
[    6.896386] ath10k_pci 0000:03:00.0: qca9377 hw1.0 (0x05020000, 0x003820ff sub 105b:e09a) fw WLAN.TF.1.0-00267-1 fwapi 5 bdapi 1 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
[    6.896392] ath10k_pci 0000:03:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[    6.936649] ath10k_pci 0000:03:00.0 wlan1: renamed from wlan0
[    6.966041] systemd-udevd[353]: renamed network interface wlan0 to wlan1
[    8.912881] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   12.754258] wlan1: authenticate with 00:24:fe:40:d4:9a
[   12.794626] wlan1: send auth to 00:24:fe:40:d4:9a (try 1/3)
[   12.796192] wlan1: authenticated
[   12.796336] ath10k_pci 0000:03:00.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[   12.796340] ath10k_pci 0000:03:00.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[   12.799373] wlan1: associate with 00:24:fe:40:d4:9a (try 1/3)
[   12.802672] wlan1: RX AssocResp from 00:24:fe:40:d4:9a (capab=0x411 status=0 aid=6)
[   12.804134] wlan1: associated
[   12.804156] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   16.804102] wlan1: deauthenticated from 00:24:fe:40:d4:9a (Reason: 1=UNSPECIFIED)
[   16.997999] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[   17.358253] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[   17.461303] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[   20.697320] wlan1: authenticate with 00:24:fe:40:d4:9a
[   20.736778] wlan1: send auth to 00:24:fe:40:d4:9a (try 1/3)
[   20.738329] wlan1: authenticated
[   20.738477] ath10k_pci 0000:03:00.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[   20.738481] ath10k_pci 0000:03:00.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[   20.739337] wlan1: associate with 00:24:fe:40:d4:9a (try 1/3)
[   20.742626] wlan1: RX AssocResp from 00:24:fe:40:d4:9a (capab=0x411 status=0 aid=6)
[   20.744192] wlan1: associated
[   24.742179] wlan1: deauthenticated from 00:24:fe:40:d4:9a (Reason: 1=UNSPECIFIED)
[   33.849227] wlan1: authenticate with 00:24:fe:40:d4:9a
[   33.889003] wlan1: send auth to 00:24:fe:40:d4:9a (try 1/3)
[   33.890690] wlan1: authenticated
[   33.890868] ath10k_pci 0000:03:00.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[   33.890871] ath10k_pci 0000:03:00.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[   33.892512] wlan1: associate with 00:24:fe:40:d4:9a (try 1/3)
[   33.895773] wlan1: RX AssocResp from 00:24:fe:40:d4:9a (capab=0x411 status=0 aid=6)
[   33.897301] wlan1: associated
[   37.895352] wlan1: deauthenticated from 00:24:fe:40:d4:9a (Reason: 1=UNSPECIFIED)
[  179.429565] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[  183.129340] wlan1: authenticate with 00:24:fe:40:d4:9a
[  183.169096] wlan1: send auth to 00:24:fe:40:d4:9a (try 1/3)
[  183.171438] wlan1: authenticated
[  183.171591] ath10k_pci 0000:03:00.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[  183.171595] ath10k_pci 0000:03:00.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[  183.174040] wlan1: associate with 00:24:fe:40:d4:9a (try 1/3)
[  183.177317] wlan1: RX AssocResp from 00:24:fe:40:d4:9a (capab=0x411 status=0 aid=6)
[  183.178876] wlan1: associated
[  187.174979] wlan1: deauthenticated from 00:24:fe:40:d4:9a (Reason: 1=UNSPECIFIED)

---

### Post by Raffael_Vogler on 2016-01-07
I tried the steps kindly suggested by [chili555]("http://ubuntuforums.org/member.php?u=35909") on an Acer E5-573 running Ubuntu 15.10 64bit and a second time with Linux Mint 17.3 64bit - it worked on both.

Because the necessary steps are spreading over 3 posts by [chili555]("http://ubuntuforums.org/member.php?u=35909") I decided to compose a little summary.

From [Post #2]("http://ubuntuforums.org/showthread.php?t=2304250&p=13396650#post13396650"):

```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz
tar -zxvf backports-20151120.tar.gz
cd backports-20151120
make defconfig-ath10k
make
sudo make install

```

From [Post #9]("http://ubuntuforums.org/showthread.php?t=2304250&p=13397159#post13397159"):

```
sudo mkdir /lib/firmware/ath10k/QCA9377/
sudo mkdir /lib/firmware/ath10k/QCA9377/hw1.0

sudo apt-get install git
git clone https://github.com/kvalo/ath10k-firmware.git
cd ath10k-firmware/QCA9377/hw1.0
sudo cp board.bin  /lib/firmware/ath10k/QCA9377/hw1.0
sudo cp firmware-5.bin_WLAN.TF.1.0-00267-1 /lib/firmware/ath10k/QCA9377/hw1.0/firmware5.bin
sudo modprobe -r ath10k_pci
sudo modprobe ath10k_pci

```

From [Post #12]("http://ubuntuforums.org/showthread.php?t=2304250&p=13397450#post13397450"):

```
cd /lib/firmware/ath10k/QCA9377/hw1.0
sudo mv firmware5.bin  firmware-5.bin

```
[U]
Then: Reboot[/U]

Thanks a lot to [chili555]("http://ubuntuforums.org/member.php?u=35909") :-({|=

---

### Post by algo-fh on 2016-01-07
Today I tried to connect to my mobile via Mobile Hotspot - and it worked. So my router is quite old and I ordered a new one.

I got the new router ... and finally it works :KS


Thanks for the support chili555

---

### Post by klepkachristopher on 2016-01-11
Thank you for this thread. I did all the steps up to (and including) post #11, and it finally worked. The first few instructions weren't enough, it was either the renaming with the hyphen or creating a hw1 profile (did both of those at the same time before rebooting). I now have wireless working on an Acer R11 R3-131T-C1YF. Very nice for a $250 convertible from Wal-Mart :p

---

### Post by stephen93 on 2016-01-16
@chili555, man your instruction saved my life, I thank you so much man! im a newbie in ubuntu (I only use ubuntu for programming, already practiced on VMware :D), do you know that I installed ubuntu for I guess 10x++ in 1week... 3 nights for searching how the grub 2 to work 'coz im dual booting windows 10 and ubuntu 14, and another 3 nights for my wifi and almost gave up, I thank myself for having "No retreat no surrender" attitude XD THANKS!!! (Lesson learned "go directly to the forum, 'coz not all solution can be found on youtube and google") XD

---

### Post by gyu2 on 2016-01-17
Thanks Chili555 for all the information you have been putting in this thread,
but i have happened to be another noob who bumped into an error following your way. Please help!!!


System Information
        Manufacturer: SAMSUNG ELECTRONICS CO., LTD.
        Product Name: 500R4K/500R5H/5400RK/501R5H/5500RH/500R5S


I've been catching up with this one:

```

sudo apt-get update
sudo apt-get install linux-headers-generic build-essential
wget [https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz)
tar -zxvf backports-20151120.tar.gz
cd backports-20151120
make defconfig-ath10k
make
sudo make install


```



Until this got me sad:

```

gyu@Gyu:~$ tar -zxvf backports-20151120.tar.gz
tar (child): backports-20151120.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

```


What should i do? Thank you so much in advance :)

---

### Post by jeremy31 on 2016-01-17
[https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz)

Clicking on the link should download it to Downloads folder in Ubuntu, so go to Downloads and right click on the file and select 'extract here'.  Then you should find a backports-20151120 folder in Downloads
Then in terminal
```
cd Downloads/backports-20151120
make defconfig-ath10k
make
sudo make install
```

---

### Post by gyu2 on 2016-01-17
@jeremy31 Thanks for your reply.

I did exactly as you said, installation was successful and I rebooted.
 But my Ubuntu still can't seem to detect wireless network.

I checked 'Additional Drivers' at 'Software & Updates' but found nothing there.

What is going on with my computer?!

---

### Post by chili555 on 2016-01-17
Jeremy hopes you will post:```
sudo modprobe ath10k_pci
dmesg | grep ath
```Jeremy thinks you may need firmware.

We now return you to your regularly scheduled guru.

---

### Post by gyu2 on 2016-01-17
I walked through the following step by step and everything is working fine now!!!

Thank you everyone, having a forum like this is a blessing indeed.

```

sudo mkdir /lib/firmware/ath10k/QCA9377/
sudo mkdir /lib/firmware/ath10k/QCA9377/hw1.0

sudo apt-get install git
git clone [https://github.com/kvalo/ath10k-firmware.git](https://github.com/kvalo/ath10k-firmware.git)
cd ath10k-firmware/QCA9377/hw1.0
sudo cp board.bin  /lib/firmware/ath10k/QCA9377/hw1.0
sudo cp firmware-5.bin_WLAN.TF.1.0-00267-1   /lib/firmware/ath10k/QCA9377/hw1.0/firmware5.bin
sudo modprobe -r ath10k_pci
sudo modprobe ath10k_pci


cd /lib/firmware/ath10k/QCA9377/hw1.0
sudo mv firmware5.bin  firmware-5.bin


```

---

### Post by gyu2 on 2016-01-18
I appreciate all the support I've had so far, thanks a lot guys. I have one last question.

Where must I keep my backports-20151120 folder?

It is at the moment in my downloads folder and I just don't want to mess up by mistakenly deleting something that I must not.

Thanks in advance :)

---

### Post by chili555 on 2016-01-18
> **gyu2 said:**
> I appreciate all the support I've had so far, thanks a lot guys. I have one last question.

Where must I keep my backports-20151120 folder?

It is at the moment in my downloads folder and I just don't want to mess up by mistakenly deleting something that I must not.

Thanks in advance :)Anywhere you like. If you are concerned that you might accidentally delete it, you could make a new directory within Downloads; something like:```
cd ~/Downloads
mkdir backportsDONOTDELETE
mv  backports-20151120  backportsDONOTDELETE 
```Thereafter, your process would be:```
cd ~/Downloads/backportsDONOTDELETE/backports-20151120
make clean
make defconfig-ath10k
make
sudo make install
```...and then reboot.

---

### Post by gyu2 on 2016-01-19
Dear @chili555

Once again, I appreciate every support you have been providing in this thread.

But a new problem is haunting me down. I updated Ubuntu using Software Updater a few minutes ago, it wanted me to reboot and I did.

And Wifi refuses to work once again...

So I did the following once again:

```

sudo apt-get update
sudo apt-get install linux-headers-generic build-essential
wget [https://www.kernel.org/pub/linux/ker...0151120.tar.gz]("https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz")
tar -zxvf backports-20151120.tar.gz
cd backports-20151120
make defconfig-ath10k
make
sudo make install




```

And then reboot.


Wifi works again... but i wonder what the update did to my computer. Seems like it didn't affect the firmware.
I'm scared if I will have to reinstall every single time there's an update.

Any ideas?

---

### Post by chili555 on 2016-01-20
> Wifi works again... but i wonder what the update did to my computer. Seems like it didn't affect the firmware.
I'm scared if I will have to reinstall every single time there's an update.

Any ideas?You  accidentally did (almost) the exact correct thing.

When you originally compiled the driver, you compiled it for your currently running kernel version only. When Update Manager installs a later kernel version, also known as linux-image, after the requested reboot, you must recompile. I recommend:```
cd backports-20151120
[COLOR="#FF0000"]make clean[/COLOR]
make defconfig-ath10k
make
sudo make install
```Now load the module:```
sudo modprobe ath10k_pci
```Also, as you see, there is no need to download a fresh copy of *backports*. I suggest you retain the file and these instructions for that time.

---

### Post by Shikhar_Raje on 2016-01-20
> **chili555 said:**
> I have been trying to work this out for quite some time and I'm stuck because I do not have the hardware. You will need to test for us.

With a temporary working internet connection, by ethernet, tethered or whatever means possible, open a terminal and do:```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz
tar -zxvf backports-20151120.tar.gz
cd backports-20151120
make defconfig-ath10k
make
sudo make install
```Reboot and let us see:```
dmesg | grep ath
```

Hi!

I tried following these steps on an Acer Aspire E15 (E5-573-32IT), but this doesn't help. I managed to get the same output on running these commands, but the WiFi still doesn't function.

Please find attached the output for running the "wireless-info" bash script. Could someone please provide some insight into how to proceed here?

Thanks in advance!

---

### Post by chili555 on 2016-01-20
> **Shikhar_Raje said:**
> Hi!

I tried following these steps on an Acer Aspire E15 (E5-573-32IT), but this doesn't help. I managed to get the same output on running these commands, but the WiFi still doesn't function.

Please find attached the output for running the "wireless-info" bash script. Could someone please provide some insight into how to proceed here?

Thanks in advance!In dmesg, we see this:> Direct firmware load for ath10k/QCA9377/hw1.0/firmware-5.bin failed with error -2The next step is:```
sudo mkdir /lib/firmware/ath10k/QCA9377/
sudo mkdir /lib/firmware/ath10k/QCA9377/hw1.0

sudo apt-get install git
git clone https://github.com/kvalo/ath10k-firmware.git
cd ath10k-firmware/QCA9377/hw1.0
sudo cp board.bin  /lib/firmware/ath10k/QCA9377/hw1.0
sudo cp firmware-5.bin_WLAN.TF.1.0-00267-1   /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin
sudo modprobe -r ath10k_pci
sudo modprobe ath10k_pci
```

---

### Post by Shikhar_Raje on 2016-01-21
> **chili555 said:**
> In dmesg, we see this:The next step is:```
sudo mkdir /lib/firmware/ath10k/QCA9377/
sudo mkdir /lib/firmware/ath10k/QCA9377/hw1.0

sudo apt-get install git
git clone https://github.com/kvalo/ath10k-firmware.git
cd ath10k-firmware/QCA9377/hw1.0
sudo cp board.bin  /lib/firmware/ath10k/QCA9377/hw1.0
sudo cp firmware-5.bin_WLAN.TF.1.0-00267-1   /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin
sudo modprobe -r ath10k_pci
sudo modprobe ath10k_pci
```

Hello, chili555! Thank you for your reply, this finally managed to get the WiFi working! Unlike most others with this problem, I don't much difference in speed between WiFi and Ethernet, and no intermittent loss of connection, either.

But, could you walk me through what you did here? In the previous steps, I had downloaded the latest kernel, manually selected the wireless driver from that, and installed it. I can't make out what this git command is downloading, and what we did after that.

Also, I wonder if there was some other driver I was supposed to install? Because, in some of the other folders, I saw some other folders already present (This was while I was tab-autocompleting the two sudo cp commands after the git clone). Particularly, in /lib/firmware, I noticed a folder called "ath6k" in addition to ath10k. Also, inside ath10k, there was a single folder, "QCA988X" already present, containing a folder "hw2.0", with it's own board.bin and firmware.bin files. Is this expected, or did I download the wrong files by mistake?

Thank you, once again!

---

### Post by chili555 on 2016-01-21
> But, could you walk me through what you did here? In the previous steps, I had downloaded the latest kernel, manually selected the wireless driver from that, and installed it. I can't make out what this git command is downloading, and what we did after that.Many Linux wireless (and other) drivers require firmware. This can be seen in the terminal command:```
modinfo ath10k_pci
``````
filename:       /lib/modules/4.2.0-25-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
<snip>

```As we saw in your message logs, the firmware was not present. The git repository is a well-known source for the firmware files. We simply downloaded them and copied the specific files needed to the correct location; /lib/firmware//lib/firmware/ath10k/QCA9377/hw1.0/.> Because, in some of the other folders, I saw some other folders already present (This was while I was tab-autocompleting the two sudo cp commands after the git clone). Particularly, in /lib/firmware, I noticed a folder called "ath6k" in addition to ath10k. Also, inside ath10k, there was a single folder, "QCA988X" already present, containing a folder "hw2.0", with it's own board.bin and firmware.bin files. Is this expected, or did I download the wrong files by mistake?
Perfectly normal. No worries.

There is actually an easier way to do this today and my answer will be a bit different in the future. I assume your wireless is working as expected, so there is no need to do anything further except enjoy!

---

### Post by ke9tv on 2016-01-23
I've done the suggested steps, on an Acer Aspire E5-573G.

The good news is that I have Wi-Fi service.

The bad news is that there are still some alarming messages in the log:

```

~$ dmesg | grep ath
[    9.158312] ath10k_pci 0000:03:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    9.545582] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[    9.998782] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/board-2.bin failed with error -2
[   11.794581] ath10k_pci 0000:03:00.0: qca9377 hw1.0 (0x05020000, 0x003820ff sub 11ad:0806) fw WLAN.TF.1.0-00267-1 fwapi 5 bdapi 1 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
[   11.794585] ath10k_pci 0000:03:00.0: debug 0 debugfs 0 tracing 0 dfs 0 testmode 0
[   11.796257] ath: EEPROM regdomain: 0x6c
[   11.796259] ath: EEPROM indicates we should expect a direct regpair map
[   11.796261] ath: Country alpha2 being used: 00
[   11.796262] ath: Regpair used: 0x6c
[   11.857301] ath10k_pci 0000:03:00.0 wlp3s0: renamed from wlan0
```

Is this to be expected, or should I be concerned?

Also, does anyone know whether the new driver will be in Xenial? Rebuilding on kernel upgrades gets old. I remember this from an older laptop that had a Broadcom Wi-Fi that was one generation beyond the kernel support.

---

### Post by chili555 on 2016-01-23
> **ke9tv said:**
> I've done the suggested steps, on an Acer Aspire E5-573G.

The good news is that I have Wi-Fi service.

The bad news is that there are still some alarming messages in the log:

```
<snip>
```

Is this to be expected, or should I be concerned?

Also, does anyone know whether the new driver will be in Xenial? Rebuilding on kernel upgrades gets old. I remember this from an older laptop that had a Broadcom Wi-Fi that was one generation beyond the kernel support.Entirely normal. It simply indicates that the driver attempted to find a firmware file and failed, a second and failed and a third and succeeded. 

I do reccomend that you set your regulatory domain permanently. Find it here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then, in a terminal:

```
gksudo gedit /etc/default/crda

```
Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:

```
REGDOMAIN=IS
```Of course, substitute your country code if not Iceland. Proofread carefully, save and close the text editor.

I believe the driver will be in the 16.04 release but I haven't yet heard for sure.

---

### Post by Nir_Shalmon on 2016-02-06
> **chili555 said:**
> I have been trying to work this out for quite some time and I'm stuck because I do not have the hardware. You will need to test for us.

With a temporary working internet connection, by ethernet, tethered or whatever means possible, open a terminal and do:```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz
tar -zxvf backports-20151120.tar.gz
cd backports-20151120
make defconfig-ath10k
make
sudo make install
```Reboot and let us see:```
dmesg | grep ath
```


Thanks! This worked!
Will this work on Linux distributions other than Ubuntu?

---

### Post by chili555 on 2016-02-06
> **Nir_Shalmon said:**
> Thanks! This worked!
Will this work on Linux distributions other than Ubuntu?I haven't any current experience with other distros, however, there is no reason why it shouldn't that I know of. Just be sure to install the prerequisites; make, g++, etc., known in Ubuntu as a meta package build-essential; and the kernel headers, known in Ubuntu as linux-headers-generic.

---

### Post by mohammadsamani2 on 2016-02-11
I have not been able to make my QCA9377 wireless card on Lenovo YOGA 700  to work, after following the instructions here. At this point, Ubuntu's  Network manager tells me that I have a wireless card but it is disabled  by a switch. There is no such a switch on my laptop, and the wireless  works when I boot Windows.

```

$ dmesg | grep ath
[    1.907212] ath10k_pci 0000:01:00.0: enabling device (0000 -> 0002)
[    1.907977] ath10k_pci 0000:01:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    2.148741] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
[    2.214683] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/board-2.bin failed with error -2
[     4.081172] ath10k_pci 0000:01:00.0: qca9377 hw1.0 (0x05020000,  0x003820ff sub 17aa:4035) fw WLAN.TF.1.0-00267-1 fwapi 5 bdapi 1 htt-ver  3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features  ignore-otp
[    4.081176] ath10k_pci 0000:01:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[    4.083035] ath: EEPROM regdomain: 0x6c
[    4.083038] ath: EEPROM indicates we should expect a direct regpair map
[    4.083041] ath: Country alpha2 being used: 00
[    4.083042] ath: Regpair used: 0x6c
[    4.097007] ath10k_pci 0000:01:00.0 wlp1s0: renamed from wlan0

$ sudo ls /lib/firmware/ath10k/QCA9377/hw1.0/
board.bin  firmware-5.bin

```

It looks like the firmware cannot be loaded for some reason. I do not understand why. It looks like it is looking for board-2.bin, but I only have board.bin. I tried renaming board.bin to board-2.bin, but that is probably just silly and it didn't help anyway. And I am stuck now.
Here is some more info:

```

$ lspci | grep Ath
01:00.0 Network controller: Qualcomm Atheros Device 0042 (rev 30)

```

My MS-Windows tells me that the driver for this hardware was produced in June of 2015. I think I read somewhere that after August 2015, there was a new driver which Ubuntu doesn't support yet.

Any help is very much appreciated, of course.

UPDATE 1: It seems like my wlan driver is working, but Lenovo deactivates all RF emitters by default.
[URL="http://billauer.co.il/blog/2014/08/linux-ubuntu-yoga-hardware-blocked-wireless-lan/"]http://billauer.co.il/blog/2014/08/linux-ubuntu-yoga-hardware-blocked-wireless-lan/
[/URL]
I am not sure yet if this is my problem.
<code>rfkill list all</code>
tells me that it is.

UPDATE 2: 
<code>
sudo rmmod ideapad_laptop
</code>
fixed my problem, but also disabled the "Aeroplane Mode" button on the keyboard.

---

### Post by Shikhar_Raje on 2016-02-13
Thank you, chilli555, for your time and help! It's much appreciated.

The wireless is working perfectly fine. Looking forward to seeing more of your tips on this forum in the future!

---

### Post by chili555 on 2016-02-13
> UPDATE 1: It seems like my wlan driver is working, but Lenovo deactivates all RF emitters by default.
[http://billauer.co.il/blog/2014/08/linux-ubuntu-yoga-hardware-blocked-wireless-lan/](http://billauer.co.il/blog/2014/08/linux-ubuntu-yoga-hardware-blocked-wireless-lan/)

I am not sure yet if this is my problem.
<code>rfkill list all</code>
tells me that it is.

UPDATE 2:
<code>
sudo rmmod ideapad_laptop
</code>
fixed my problem, but also disabled the "Aeroplane Mode" button on the keyboard. That is a well-known issue with the module *ideapad-laptop*. In the newest Ubuntu versions, it seems to be fixed. If you don't want to manually unload the module at every boot, you may blacklist it so it never loads at all:```
sudo -i
echo "blacklist ideapad-laptop"  >>  /etc/modprobe.d/blacklist.conf
exit
```

---

### Post by Shikhar_Raje on 2016-02-14
> **chili555 said:**
> In dmesg, we see this:The next step is:```
sudo mkdir /lib/firmware/ath10k/QCA9377/
sudo mkdir /lib/firmware/ath10k/QCA9377/hw1.0

sudo apt-get install git
git clone https://github.com/kvalo/ath10k-firmware.git
cd ath10k-firmware/QCA9377/hw1.0
sudo cp board.bin  /lib/firmware/ath10k/QCA9377/hw1.0
sudo cp firmware-5.bin_WLAN.TF.1.0-00267-1   /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin
sudo modprobe -r ath10k_pci
sudo modprobe ath10k_pci
```

Hello, again, @Chilli555!

Last night, Elementary OS updated my kernel to "3.19.0-49-generic". This broke the WiFi setup that you had helped me setup previously. I followed the same steps that you had outlined in this thread previously (beginning from downloading the backport from "https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz" till "sudo modprobe ath10k_pci". However, this time around, I receive this error on the last modprobe command:

```
modprobe: ERROR: could not insert 'ath10k_pci': Invalid argument
```

I tried searching around for some solutions for this message. [One post]("http://askubuntu.com/questions/397564/no-wifi-connection-rtl8723be-on-ubuntu-13-04") (on which you had participated) suggested changing the version number of the backport, but I don't know if that would work. After all, I'm backporting the same kernel module that I did the first time around, and it had worked at that time!

Could you help me fix this WiFi issue, again? I'd appreciate it very much.

EDIT: Adding the text files of the instructions from beginning to end, so that you don't have to scroll back in this thread to see what I did. Hope this helps!

---

### Post by jeremy31 on 2016-02-14
You should have just needed to do
```
cd backports-20151120
make clean
make defconfig-ath10k
sudo make install
```

Then reboot

---

### Post by jeremy31 on 2016-02-14
> **chili555 said:**
> That is a well-known issue with the module *ideapad-laptop*. In the newest Ubuntu versions, it seems to be fixed. If you don't want to manually unload the module at every boot, you may blacklist it so it never loads at all:```
sudo -i
echo "blacklist ideapad-laptop"  >>  /etc/modprobe.d/blacklist.conf
exit
```

The Yoga 700 was just added to the ideapad-laptop module on January 26 of this year

[http://kernel.ubuntu.com/git/ubuntu/linux.git/commit/drivers/platform/x86/ideapad-laptop.c?h=linux-4.2.y-queue&id=93931e9db588f52694d92d4284ca340cafbbfec5](http://kernel.ubuntu.com/git/ubuntu/linux.git/commit/drivers/platform/x86/ideapad-laptop.c?h=linux-4.2.y-queue&id=93931e9db588f52694d92d4284ca340cafbbfec5)

---

### Post by mohammadsamani2 on 2016-03-07
Following this thread, as noted above, I managed to get my wifi to work.
It stopped working tonight, I assume after a kernel update or something. So I executed the following commands, with no luck:
```
cd backports-20151120/
make defconfig-ath10k
make install

```
The second line gives me the following error:
```

make[2]: Warning: File 'conf' has modification time 26531 s in the future
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o zconf.tab.o zconf.tab.c
make[2]: warning:  Clock skew detected.  Your build may be incomplete.
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#

```
And the third line gives me these error messages:
```

  INSTALL /root/wifi/backports-20151120/compat/compat.ko
Can't read private key
  INSTALL /root/wifi/backports-20151120/drivers/net/wireless/ath/ath.ko
Can't read private key
  INSTALL /root/wifi/backports-20151120/drivers/net/wireless/ath/ath10k/ath10k_core.ko
Can't read private key
  INSTALL /root/wifi/backports-20151120/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
Can't read private key
  INSTALL /root/wifi/backports-20151120/net/mac80211/mac80211.ko
Can't read private key
  INSTALL /root/wifi/backports-20151120/net/wireless/cfg80211.ko
Can't read private key
  DEPMOD  4.2.0-30-generic
depmod will prefer updates/ over kernel/ -- OK!
Note:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against "update-initramfs.sh". If your distribution does not
require this send a patch with the '/usr/bin/lsb_release -i -s'
("Ubuntu") tag for your distribution to avoid this warning.

Your backported driver modules should be installed now.
Reboot.

make[1]: warning:  Clock skew detected.  Your build may be incomplete.

```
When I reboot, I don't see the Wifi at all. ```
 dmesg | grep ath 
``` also gives me nothing.
Any ideas?

UPDATE:  The problem is solved. I don't know how. This is getting quite annoying. I have to struggle with this once every two weeks or so.

---

### Post by jeremy31 on 2016-03-07
It is recommended that you run the commands like the following after a kernel update
```
cd backports-20151120
make clean
make defconfig-ath10k
make
sudo make install
```

The only errors that aren't normal involve the time skew and clock

---

### Post by chili555 on 2016-03-07
> **mohammadsamani2 said:**
> ```
DEPMOD  4.2.0-30-generic
```
UPDATE:  The problem is solved. I don't know how. This is getting quite annoying. I have to struggle with this once every two weeks or so.I believe the driver ath10k_pci is included in 4.2.0-xx. Does it not cover your exact device or what? I'm not sure I see why it is necessary to compile at all.

---

### Post by jeremy31 on 2016-03-07
> **chili555 said:**
> I believe the driver ath10k_pci is included in 4.2.0-xx. Does it not cover your exact device or what? I'm not sure I see why it is necessary to compile at all.

Poster has the 0042 Atheros device, even in 4.2.0-30 ath10k_pci only covers the 003c and 003e

---

### Post by Bigdoodle on 2016-03-20
Just reporting that the solution proposed at the beginning of this thread (post #2) also works for the **ASUS TP200SA-FV109T**, running Ubuntu 15.10. Many thanks for your support! :D

---

### Post by manfred7 on 2016-04-07
I also managed to get wifi working on an Acer E15 E5-573-P62E. Thanks to chili555 :D

There are only two small problems...  The wifi-connection refuses to get an IP via DHCP from the router (fritzbox7360). I have to set a fixed IP to get IPv4 working. What could be the problem?

Second problem is, that the connection info shows only a speed of 1MB/s. On my other (older) Laptop there is 130MB/s

greetings
Manfred

---

### Post by gyates100895 on 2016-04-20
I've managed to get this working on SteamOS and the fork VaporOS. Here are the commands necessary and in sequence for my case:

NOTE!!: If you you either of the above OS's, and this is a fresh install, I highly recommend letting steam do its full update process before proceeding. I did not, cut the update short, and ended up needing to reinstall, which prompted me to make this guide. Also, since i prefer VaporOS and given the nature of said OS (being a fork of a young OS), I can not stress enough, do not do what i did above. let it do its thing before you do your thing. patience is a virtue ;).
```

sudo apt-get update
sudo apt-get install linux-headers-$(uname -r) build-essential git

```
Here is when I personally make a folder in the current user's root folder to contain my personal system mods:
```

mkdir ~/mods
cd ~/mods

```
Back to the essential steps:
```

wget [URL="https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz"]https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz
[/URL]tar -zxvf backports-20151120.tar.gz 
cd backports-20151120
make defconfig-ath10k
make
sudo make install

```
do what it says and reboot. you should not have working wireless yet, since we still must add the firmware files:
```

git clone https://github.com/kvalo/ath10k-firmware.git

```
lets prepare the direstories where the firmware files will be placed:
```

sudo mkdir /lib/firmware/ath10k/QCA9377
sudo mkdir /lib/firmware/ath10k/QCA9377/hw1.0

```
and now to copy the files:
```

cd ./ath10k-firmware/QCA9377/hw1.0
sudo cp board.bin  /lib/firmware/ath10k/QCA9377/hw1.0/board.bin
sudo cp board-2.bin  /lib/firmware/ath10k/QCA9377/hw1.0/board-2.bin
sudo cp firmware-5.bin*  /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin

```
Now reboot and see if it worked. If you do not want to reboot you may try:
```

sudo modprobe -r ath10k_pci
sudo modprobe ath10k_pci

```

---

### Post by pavneet on 2016-05-08
The following instructions given in Post #8 worked for me for my Asus TP200SA-UHBF while doing a fresh install of Xubuntu 16.04LTS, with the only modification being that I copied the *firmware.bin* file to **firmware-5.bin** rather than *firmware5.bin*.

Should I, instead, be following chili555's instructions in Post #2?

Many thanks!

> **chili555 said:**
> It looks like you need some firmware. Please open a terminal and do:```
sudo mkdir /lib/firmware/ath10k/QCA9377/
sudo mkdir /lib/firmware/ath10k/QCA9377/hw1.0
```If it reports that the file already exists, that's fine, just continue.

With a temporary working internet connection:```
sudo apt-get install git
git clone https://github.com/kvalo/ath10k-firmware.git
cd ath10k-firmware/QCA9377/hw1.0
sudo cp board.bin  /lib/firmware/ath10k/QCA9377/hw1.0
sudo cp firmware-5.bin_WLAN.TF.1.0-00267-1   /lib/firmware/ath10k/QCA9377/hw1.0/firmware5.bin
sudo modprobe -r ath10k_pci
sudo modprobe ath10k_pci
```Your wireless should be working; if not,try a reboot.

---

### Post by chili555 on 2016-05-08
> **pavneet said:**
> The following instructions given in Post #8 worked for me for my Asus TP200SA-UHBF while doing a fresh install of Xubuntu 16.04LTS, with the only modification being that I copied the *firmware.bin* file to **firmware-5.bin** rather than *firmware5.bin*.

Should I, instead, be following chili555's instructions in Post #2?

Many thanks!Nope. You did it correctly but I made a typo. Sorry about that!

I've corrected my erroneous post so that the searchers won't follow the wrong path.

---

