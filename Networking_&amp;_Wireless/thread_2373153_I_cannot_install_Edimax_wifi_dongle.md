---
title: "I cannot install Edimax wifi dongle"
date: 2017-10-03
forum: Networking &amp; Wireless
---

### Post by Artanis.ro on 2017-10-03
Hello,

I bot a new wireless dongle, an Edimax EW-7811UAC with very nice  theoretical hardware specs. The dongle works well on Windows, however  there are issues on Linux, raspbian and ubuntu.
I want to install it on my raspberry pi 3B. The problem consists in the fact that it is not listed in ifconfig/iwconfig, at all.

**lsusb** returns this line: *[COLOR=#0040FF]Bus 001 Device 004: ID 7392:a812 Edimax Technology Co., Ltd[/COLOR]*

I have tried to install it using the driver from edimax website and I have the following error when I get to the "make" part:

[I][COLOR=#0000FF]make ARCH=armv7l CROSS_COMPILE= -C  /lib/modules/4.9.41-v7+/build  M=/home/pi/test/rtl8812AU_8821AU_linux_v4.2.2_7502.20130517  modules
make[1]: *** /lib/modules/4.9.41-v7+/build: No such file or directory.  Stop.
Makefile:1041: recipe for target 'modules' failed
make: *** [modules] Error 2[/COLOR][/I]

Also if I try to install build-essential it says that *[COLOR=#0000FF]build-essential is already the newest version.[/COLOR]*
Where can I locate the build essential packages? The driver for this  edimax should also be there, again a "make" compiling part would be  required. 

In another driver package I have donwloaded there is an install script, I have runed it and it triggers this:
[I][COLOR=#4000FF]##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:

tar: Old option 'f' requires an argument.
Try 'tar --help' or 'tar --usage' for more information.
rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58
Authentication requested [root] for make clean:
/bin/sh: 1: bc: not found
cd hal/phydm/ ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal/phydm/ ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal/led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
cd hal ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd platform ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
Authentication requested [root] for make driver:
/bin/sh: 1: bc: not found
make ARCH=armv7l CROSS_COMPILE= -C /lib/modules/4.9.41-v7+/build  M=/home/pi/edimax/RTL8821AU_Linux_v4.3.19.5_17672_BTCOEX20150921-58.20160506_support_kernel4.4/driver/rtl8821AU_linux_v4.3.19.5_17672.20160506_BTCOEX20150921-58   modules
make[1]: *** /lib/modules/4.9.41-v7+/build: No such file or directory.  Stop.
Makefile:1625: recipe for target 'modules' failed
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################[/COLOR][/I]

I am kind o stucked with my new edimax wifi usb, what do you guys think?

Thank you

---

### Post by Artanis.ro on 2017-10-03
I searched in the forum for this problem and this solution doesn't work: [https://ubuntuforums.org/showthread.php?t=2362669&page=2](https://ubuntuforums.org/showthread.php?t=2362669&page=2)

---

### Post by Hadaka on 2017-10-03
Hi we notice...
 #I have tried to install it using the driver from edimax website and I have the following error when I get to the "make" part:
 #make ARCH=armv7  <- This is for ARCH Linux - NOT Ubuntu
 #In another driver package I have donwloaded there is an install script, I have runed it and it triggers this:
#Realtek Wi-Fi driver Auto installation script 
#Novembor, 21 2011 v1.1.0  <- This is from 2011, not likely to work in 2017
#I searched in the forum for this problem and this solution doesn't work:#[https://ubuntuforums.org/showthread.php?t=2362669&page=2](https://ubuntuforums.org/showthread.php?t=2362669&page=2)
#That link and chipset is for RTL8822bu...you have RTL8812au Totally different.[URL="https://ubuntuforums.org/showthread.php?t=2362669&page=2"][COLOR=#000000][/COLOR]
[/URL]
Let's see exactly what you have loaded and your kernel version.

Please open a terminal ctrl/alt/t then Copy and Paste the following command
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is **wireless-info.txt**
From your directory please copy,paste and post the **wireless-info.txt**
Thanks

---

### Post by Artanis.ro on 2017-10-03
Ok, you caught me, kinda :) I pasted some details from my microserver.

Here is the file from my ubuntu installation. If you help me and solve this many communities will benefit from it. This is a general issue on the internet with 
some drivers for edimax dongles. I know my driver files were for another type of edimax, but believe when I tell you that I tried them all. Also what I don't understand is why the "make" command triggers errors and says 
that there are missing files, even if the drivers are for another dongle, they should work I guess.

Thank you

---

### Post by Artanis.ro on 2017-10-03
Well, I think I found the driver, for this Edimax AC 600 wi-fi USB adapter: [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux)
Using this command:*sudo make -f Makefile.dkms install* (from the driver's directory of course)
Triggers this:
[I]make clean
make[1]: Entering directory '/home/kevin/rtl8812AU_8821AU_linux-master'
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.4.0-96-generic/build M=/home/kevin/rtl8812AU_8821AU_linux-master clean
make[2]: Entering directory '/usr/src/linux-headers-4.4.0-96-generic'
make[2]: gcc: Command not found
make[2]: Leaving directory '/usr/src/linux-headers-4.4.0-96-generic'
make[1]: Leaving directory '/home/kevin/rtl8812AU_8821AU_linux-master'
mkdir -p '/usr/src/rtl8812au-4.3.14'
cp -r dkms.conf Kconfig Makefile.dkms Makefile platform core hal include os_dep '/usr/src/rtl8812au-4.3.14'
cp Makefile '/usr/src/rtl8812au-4.3.14/Makefile'
sed 's/#MODULE_VERSION#/4.3.14/' dkms.conf > '/usr/src/rtl8812au-4.3.14/dkms.conf'
dkms add -m rtl8812au -v 4.3.14 2>/dev/null || true
dkms build -m rtl8812au -v 4.3.14
make: dkms: Command not found
Makefile.dkms:18: recipe for target 'build' failed
make: *** [build] Error 127
[/I]

---

### Post by Hadaka on 2017-10-03
Hi Kevin, not alot of info in your wireless file, like lsmod output and 
other information.. 
Im not sure this will work..
```
##### resolv.conf ##### 
nameserver 192.168.0.170
```
*you should also have..
```
nameserver 127.0.0.1
```
*If this is correct ->     Europe/Bucharest...Please do..
```
sudo iw reg set RO
sudo sed -i 's/=.*/=RO/' /etc/default/crda
```
Here is a link to correctly install the driver you need.
[https://ubuntuforums.org/showthread.php?t=2340769](https://ubuntuforums.org/showthread.php?t=2340769)
I have no further suggestions.

---

### Post by albert_wesker2 on 2017-10-05
Since you're missing the dkms command, should you install the dkms package first.

Know there is a newer driver out there, which can be found here: [https://github.com/zebulon2/rtl8812au](https://github.com/zebulon2/rtl8812au)

The original driver by Edmiax is just an outdated version of RealTek's OEM driver, version 4.x.y. The one that's been going around latest is 5.1.5 and works with the latest stable kernel (i.e. 4.13.5).

I'm also using the Edimax EW-7811 dongle. It works nice and with the latest driver does also the LED (blue) work. Like I didn't have enough blue LEDs at my desk already. :D

Cheers

---

