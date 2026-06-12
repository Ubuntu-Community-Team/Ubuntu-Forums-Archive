---
title: "Toshiba Satellite A505 S6033"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by Rybandt on 2010-06-29
I've been searching for about six hours now. I need to know how I can get my wireless card working on my Toshiba Satellite A505 S6033, I installed 9.10 because 10.04 I wasn't able to see anything but a black screen after install. but I see nothing to help me. And I don't understand terminal code either, can someone put it into completely Ubunutu illiterate terms? I love Linux, watched a friend use it and now I just can't stand windows! Any help would be awesome!!!:confused:

---

### Post by Rybandt on 2010-06-29
looks like everyone is having problems with wireless cards and toshibas :\

---

### Post by Matt__ on 2010-06-29
my sat pro works great, out of the box.
lets try and identify your wireless

can you open a terminal and use these commands pls & post output
```
lspci -nn
``````
iwconfig
``````
[FONT=arial][SIZE=2][COLOR=black]sudo lshw -c   network[/COLOR][/SIZE][/FONT]
```

Have you connected via wired connection and updated/looked in system/admin/hardware drivers?

---

### Post by Rybandt on 2010-06-29
> **Matt__ said:**
> my sat pro works great, out of the box.
lets try and identify your wireless

can you open a terminal and use these commands pls & post output
```
lspci -nn
``````
iwconfig
``````
[FONT=arial][SIZE=2][COLOR=black]sudo lshw -c   network[/COLOR][/SIZE][/FONT]
```Have you connected via wired connection and updated/looked in system/admin/hardware drivers?



ryan@ryan-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI [8086:d132] (rev 11)
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express Root Port 1 [8086:d138] (rev 11)
00:08.0 System peripheral [0880]: Intel Corporation Core Processor System Management Registers [8086:d155] (rev 11)
00:08.1 System peripheral [0880]: Intel Corporation Core Processor Semaphore and Scratchpad Registers [8086:d156] (rev 11)
00:08.2 System peripheral [0880]: Intel Corporation Core Processor System Control and Status Registers [8086:d157] (rev 11)
00:08.3 System peripheral [0880]: Intel Corporation Core Processor Miscellaneous Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI Link [8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI Routing and Protocol Registers [8086:d151] (rev 11)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 05)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0a75] (rev a2)
01:00.1 Audio device [0403]: nVidia Corporation Device [10de:0be3] (rev a1)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)
04:00.0 SD Host controller [0805]: Ricoh Co Ltd Device [1180:e822] (rev 01)
04:00.1 System peripheral [0880]: Ricoh Co Ltd Device [1180:e230] (rev 01)
04:00.2 System peripheral [0880]: Ricoh Co Ltd Device [1180:e852] (rev 01)
04:00.3 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Device [1180:e832] (rev 01)
3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers [8086:2c52] (rev 04)
3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2c81] (rev 04)
3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2c90] (rev 04)
3f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2c91] (rev 04)
3f:03.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller [8086:2c98] (rev 04)
3f:03.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder [8086:2c99] (rev 04)
3f:03.4 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Test Registers [8086:2c9c] (rev 04)
3f:04.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers [8086:2ca0] (rev 04)
3f:04.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers [8086:2ca1] (rev 04)
3f:04.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers [8086:2ca2] (rev 04)
3f:04.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers [8086:2ca3] (rev 04)
3f:05.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers [8086:2ca8] (rev 04)
3f:05.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers [8086:2ca9] (rev 04)
3f:05.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers [8086:2caa] (rev 04)
3f:05.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers [8086:2cab] (rev 04)
ryan@ryan-laptop:~$ 




________



ryan@ryan-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ryan@ryan-laptop:~$ ^C
ryan@ryan-laptop:~$ 

----------------------


ryan@ryan-laptop:~$ sudo lshw -c   network
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:26:6c:3b:bc:1f
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.1.10.10 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:35 ioport:4000(size=256) memory:d3110000-d3110fff(prefetchable) memory:d3100000-d310ffff(prefetchable) memory:d3120000-d313ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:d9100000-d9103fff
ryan@ryan-laptop:~$ 
ryan@ryan-laptop:~$ 




____

And yes, I am running wired and connected just fine.  I just need to figure this out and my nvidia 310m. I'm brand new to linux, and I just love it...If I could figure it out...:lolflag:

---

### Post by philinux on 2010-06-29
rybandt,

Make sure to start a separate thread for the nvidia problem.

---

### Post by Rybandt on 2010-06-29
> **philinux said:**
> rybandt,

Make sure to start a separate thread for the nvidia problem.



I know :p Only stating that these are the two things in my way!

---

### Post by Matt__ on 2010-06-29
you have exactly the same network card as mine, which has worked  flawlessly out of the box with 8.10, 9.04 and 10.04.
 
 On the top panel icon, do you get a list of wireless networks shown? is  "enable wireless" checked? is the wireless switch on the front of your  laptop turned on, or is it soft key enabled? (I dont see a hardware wireless switch on that unit)

**Phil...maybe you can jump in here and help..i bow to your greater wisdom** :)

---

### Post by sydbat on 2010-06-29
Are there any "restricted drivers" for that wireless card? System > Administration > Hardware Drivers. There might also be nVidia graphics drivers there too.

---

### Post by Rybandt on 2010-06-29
> **Matt__ said:**
> you have exactly the same network card as mine, which has worked  flawlessly out of the box with 8.10, 9.04 and 10.04.
 
 On the top panel icon, do you get a list of wireless networks shown? is  "enable wireless" checked? is the wireless switch on the front of your  laptop turned on, or is it soft key enabled? (I dont see a hardware wireless switch on that unit)

**Phil...maybe you can jump in here and help..i bow to your greater wisdom** :)

Yes, everything that matters is on and happening, but no, it isn't discovering any networks, I click up at the panel icon and it only shows my ethernet cable. I even tried entering wireless info, but all those other options confuse me!

---

### Post by Rybandt on 2010-06-29
> **sydbat said:**
> Are there any "restricted drivers" for that wireless card? System > Administration > Hardware Drivers. There might also be nVidia graphics drivers there too.


Hey thanks! That installed the nvidia driver!  :guitar:

---

### Post by Matt__ on 2010-06-29
Ive looked around and found a few old bug reports but they seem to be  for wired interface only.

I suggest you look at this post first, same adapter...successful fix.
[http://ubuntuforums.org/showthread.php?p=9049962](http://ubuntuforums.org/showthread.php?p=9049962)

if that fails work through  [>this  post]("https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/99966")<

or try  >[ndiswrapper<]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").  You may need to mess around trying different driver releases for that  I'm afraid.

I personally had issues with the wireless on a dell mini and no end  of tweaking would fix it..until one day (i had been using older ubuntu  from usb) I booted 10.04 and wifi connected automatically.

---

### Post by S.R on 2010-06-29
Are you using KDE by chance?

---

### Post by Rybandt on 2010-06-30
> **Matt__ said:**
> Ive looked around and found a few old bug reports but they seem to be  for wired interface only.

I suggest you look at this post first, same adapter...successful fix.
[http://ubuntuforums.org/showthread.php?p=9049962](http://ubuntuforums.org/showthread.php?p=9049962)

if that fails work through  [>this  post]("https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/99966")<

or try  >[ndiswrapper<]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").  You may need to mess around trying different driver releases for that  I'm afraid.

I personally had issues with the wireless on a dell mini and no end  of tweaking would fix it..until one day (i had been using older ubuntu  from usb) I booted 10.04 and wifi connected automatically.

Matt this looks very promising. Although, I did what he said, downloaded it, then ran that code and it says it can not find file...stop. :\ Let me post it....

ryan@ryan:~$ tar xzf rtl8192se_linux_2.6.0010.1211.2009.tar.gz
tar: rtl8192se_linux_2.6.0010.1211.2009.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
ryan@ryan:~$ cd rtl8192se_linux_2.6.0010.1211.2009
bash: cd: rtl8192se_linux_2.6.0010.1211.2009: No such file or directory
ryan@ryan:~$ sudo make
make: *** No targets specified and no makefile found.  Stop.
ryan@ryan:~$

---

### Post by soad6 on 2010-08-18
i have a quick question... has anyone got 10.04 to install on a toshiba satellite a505-s6033 or any i7 toshiba laptop? i ask because i have this same laptop and i can't stand to keep using windows. If anyone has gotten this to install fine or a previous version to install simply please let me know. Im going to try to install 9.10 with marleyfan68 's instructions but im not sure if everything will work afterwards. I hope this works i tried different things with 10.04 and still got nothing more then a black screen with a flashing prompt. It just stay like that for a while so i rebooted it, and gave up. Was i supposed to let it go past that point or what? Thank you for any help in advance. Also with modifying the apic and other stuff does this affect how the cpu runs or do you still get the intial 4 cores that you should. I dont care if i dont get 8 cores, i just need 4 so that i can run virtual box and linux for some of my class applications, for programing. thank you if anyone has anything that helps

.](*,) where's the entrance?

---

### Post by Alver on 2010-08-18
> **soad6 said:**
> i have a quick question... has anyone got 10.04 to install on a toshiba satellite a505-s6033 or any i7 toshiba laptop? i ask because i have this same laptop and i can't stand to keep using windows. If anyone has gotten this to install fine or a previous version to install simply please let me know. Im going to try to install 9.10 with marleyfan68 's instructions but im not sure if everything will work afterwards. I hope this works i tried different things with 10.04 and still got nothing more then a black screen with a flashing prompt. It just stay like that for a while so i rebooted it, and gave up. Was i supposed to let it go past that point or what? Thank you for any help in advance. Also with modifying the apic and other stuff does this affect how the cpu runs or do you still get the intial 4 cores that you should. I dont care if i dont get 8 cores, i just need 4 so that i can run virtual box and linux for some of my class applications, for programing. thank you if anyone has anything that helps

.](*,) where's the entrance?
I have a Toshiba Satellite L 505 10M with W7 in dual boot with 10.04.1. I also have the same Realtek wireless nic. Initially I had no wireless connection but after I installed wicd I had my wireless up and running. After a couple of weeks with the 2 wireless apps (wicd and the normal applet) I uninstalled wicd and I noticed no more problems with wireless connections. Unfortunately I cannot offer any explanation for this behaviour. Hope this helps (a bit).

---

### Post by soad6 on 2010-08-19
ok, so i see some people get 10.04 1 to boot but its not with the same kinda machine as mine. Thats the issue ive exhausted every situation i can think of to boot off the 10.04 disk i have with no luck just a black screen with a command prompt that you can't type at though. So i reinstalled 9.10 back into my satellite a505 s6033. Now im gonna try to upgrade to 10.04 after installing the restricted Nvidia drivers does anyone know if this works or if it doesnt because if it doesnt all cancel now. Thank you for any advice. And does anyone know if this will be fixed with 10.10?

---

### Post by protpisys on 2010-08-19
I have a Satellite and it connected to my wireless network w/o an issue, that's been the least of my worries

---

