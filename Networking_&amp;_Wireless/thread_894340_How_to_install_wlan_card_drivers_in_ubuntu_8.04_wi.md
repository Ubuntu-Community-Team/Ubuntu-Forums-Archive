---
title: "How to install wlan card drivers in ubuntu 8.04 without ndiswrapper??"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by shredder12 on 2008-08-19
I have dell wireless mini card 1395 on my laptop and i have installed its drivers using ndiswrapper in Ubuntu..
there is no problem with its woking it works very well...but i want to use aircrack and ndiswrapper is not compatible with it..
so is there a way to directly install the drivers of wlan card in ubuntu...without using ndiswrapper..

---

### Post by Ayuthia on 2008-08-19
> **shredder12 said:**
> I have dell wireless mini card 1395 on my laptop and i have installed its drivers using ndiswrapper in Ubuntu..
there is no problem with its woking it works very well...but i want to use aircrack and ndiswrapper is not compatible with it..
so is there a way to directly install the drivers of wlan card in ubuntu...without using ndiswrapper..

Can you post your lspci -nn from the Terminal?  It will help us see what wireless card you have.

---

### Post by shredder12 on 2008-08-19
the result of lspci -nn is..
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M GS [10de:0427] (rev a1)
06:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
08:05.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
08:05.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 02)
08:05.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)

```

---

### Post by jimv on 2008-08-19
EDIT: nevermind

---

### Post by Ayuthia on 2008-08-19
> **shredder12 said:**
> 
06:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
[/CODE]

You have a 4315 chipset so you do have the Broadcom wl driver available.  As long as your kernel version is greater than 2.6.24-17-generic, you should be able to enable it by doing the following in the Terminal:
```
sudo modprobe -r b43 b43legacy b44 ssb ndiswrapper wl bcm43xx
sudo depmod -ae
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```

To see what kernel version you are using do the following in the Terminal:
```
uname -r
```

---

### Post by shredder12 on 2008-08-21
the command uname-r gives the result

2.6.24-19-generic

so what should i do now??

---

### Post by Ayuthia on 2008-08-21
> **shredder12 said:**
> the command uname-r gives the result

2.6.24-19-generic

so what should i do now??

Were you able to do these commands in the terminal:
```
sudo modprobe -r b43 b43legacy b44 ssb ndiswrapper wl bcm43xx
sudo depmod -ae
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```

If not, can you do the following for me:
```
sudo updatedb
locate wl.ko
```
These commands will update the search database and then it will look for the wireless module.  If it can't find it, you might try:
```
sudo /etc/init.d/linux-restricted-modules-common start
sudo depmod -a
modprobe wl
```

---

### Post by shredder12 on 2008-08-22
yes the 5 commands that u asked to type worked..
and for the iwlist scan ..
it showed 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

though my wireless is still working...
so what m i supposed to do now..

---

### Post by shredder12 on 2008-08-22
yes the 5 commands that u asked to type worked..
and for the iwlist scan ..
it showed 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

though my wireless is still working...
so what m i supposed to do now..

---

### Post by Ayuthia on 2008-08-22
> **shredder12 said:**
> yes the 5 commands that u asked to type worked..
and for the iwlist scan ..
it showed 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

though my wireless is still working...
so what m i supposed to do now..
If it is working and you want to keep it:
```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist
echo blacklist ndiswrapper | sudo tee -a /etc/modprobe.d/blacklist
sudo update-initramfs -u
```

I am not for sure about why the scan did not work.  I know that there is another update coming soon and hopefully that will fix the problem.  The current one that is being tested is adding more Broadcom cards to the driver and I know that the scan works on mine, but I have a 4311 card.

---

### Post by shredder12 on 2008-08-22
Hey the iwlist scan command worked...
actually i was a fool..i didn't checked whether the wireless was on or not..
well since everything is working..
but still i m a bit confused about what has happend till now and what have we achieved till now..
can u please clarify some of my doubts..

---

### Post by armine on 2008-09-20
> **shredder12 said:**
> I have dell wireless mini card 1395 on my laptop and i have installed its drivers using ndiswrapper in Ubuntu..
there is no problem with its woking it works very well...but i want to use aircrack and ndiswrapper is not compatible with it..
so is there a way to directly install the drivers of wlan card in ubuntu...without using ndiswrapper..

 
Hi. I have a question and I think you can help me. 

I am a very very beginner in Ubuntu. I have Dell Vostro 1500 and the same wireless mini card that you have on your PC. The issue is that I do not have wireless connection when I am signed in Ubuntu and the WiFi/wireless light is not on even. But everything is ok when I am using XP. May be I do not have drivers for Ubuntu? Seems your wireless is working with Ubuntu. Please, could you help me with my drivers if it is the problem. 

Thanks in advance.

Thanks a lot

---

### Post by shredder12 on 2008-09-20
there is no problem with it..
actually ubuntu has a really good software called ndiswrapper...which you can download easily using synaptic...(System->administration->synaptic manager). Synaptic will automatically install it..after the installation you will se an option "windows wireless drivers" in (System->administration->synaptic) there you just follow the instruction and your job is done..Actually ndiswrapper makes use of windows drivers to run wireless on ubuntu..so as you are saying that your wireless works fine on xp....so you are not gonna have any problem running it on ubuntu..
for more information you can always look in the help section.. 
(System->administration->Help and support) search for ndiswrapper or wireless there and you will get all the required information..

---

### Post by Ayuthia on 2008-09-21
> **shredder12 said:**
> Hey the iwlist scan command worked...
actually i was a fool..i didn't checked whether the wireless was on or not..
well since everything is working..
but still i m a bit confused about what has happend till now and what have we achieved till now..
can u please clarify some of my doubts..

All that has been done for you is that the wl driver was built for your card.  From what I have read, it sounds like Broadcom made this driver in Linux for Dell.  Because of this (and Dell using Ubuntu for some of their computers), Ubuntu has packaged the wl driver in linux-restricted-modules.  The only problem was that the driver did not work well in Ubuntu until 2.6.24-19 which is used in 8.04.1.

Since you were trying ndiswrapper, we ended up blacklisting that module along with the b43 module (in case the b43 module was being loaded).  They are drivers that can cause conflicts with the wl module.  The commands I gave you removed any conflicting wireless drivers for your card and then we blacklisted them to make sure that they would not be loaded.  The initramfs command updates the module loading process during the time when the system is booting.  If it is not updated, sometimes unwanted drivers can be loaded and will end up causing problems.  The command updates the boot process so that it will match up with the information in the blacklist.

Hope that is not too confusing.

---

### Post by phwhitley on 2008-10-01
> **Ayuthia said:**
> Can you post your lspci -nn from the Terminal?  It will help us see what wireless card you have., 

:( [INDENT][/INDENT]Help pleeeeeasse!  I really want to us Ubutu without being plugged in to the router.  I have followed your request above and believe I have properly installed the firmware for this BCM 4311.  Please let me know what is next.

phwhitley@phwhitley-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
phwhitley@phwhitley-laptop:~$ [http://ftp.us.dell.com/comm/R159896.EXE](http://ftp.us.dell.com/comm/R159896.EXE)

---

### Post by Ayuthia on 2008-10-01
> **phwhitley said:**
> , 

:( [INDENT][/INDENT]Help pleeeeeasse!  I really want to us Ubutu without being plugged in to the router.  I have followed your request above and believe I have properly installed the firmware for this BCM 4311.  Please let me know what is next.

phwhitley@phwhitley-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
phwhitley@phwhitley-laptop:~$ [http://ftp.us.dell.com/comm/R159896.EXE](http://ftp.us.dell.com/comm/R159896.EXE)

If you installed the firmware for the b43 driver, we should check and make sure that the card is seeing the firmware.  Please post the results of lshw -C network.  If it does not show UNCLAIMED, you can try the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx wl
sudo modprobe b43
sudo iwconfig wlan0 up
sudo iwlist scan
```
This will remove all the possible wireless modules for your wireless.  It will then load the b43 module, bring it up, and then scan for wireless sites.

---

### Post by phwhitley on 2008-10-02
> **Ayuthia said:**
> If you installed the firmware for the b43 driver, we should check and make sure that the card is seeing the firmware.  Please post the results of lshw -C network.  If it does not show UNCLAIMED, you can try the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx wl
sudo modprobe b43
sudo iwconfig wlan0 up
sudo iwlist scan
```
This will remove all the possible wireless modules for your wireless.  It will then load the b43 module, bring it up, and then scan for wireless sites.


Very Cool!  Thanks Ayuthia - I followed your advice and I am now sending you this message within Firefox on Ubutu - and wireless!!!  When I check the speed, it is only showing 1 Mp/s.  When I was plugged in today I was getting much higher speeds.  Is there anyway to speed up the wireless connection?  Also, when I initially ran your recommendations, Windows Wireless Drives (Ndiswrapper) was installed - earlier I was trying all possible combinations earlier and had left it installed.  Having it installed didn't effect wireless connectivity.  I've just uninstalled it and connection remains.  Do I need it, or is it in the way?  Thanks again for your expertise.  Below are the results from your recommendations.  One more question.  Do you know if Evolution Mail will interface with gmail through the POP as I have with Outlook?

I can't thank you enough for getting me this far - thank you, thank you, thank you, 

Dr. Phil

phwhitley@phwhitley-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:fc:c6:9d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:60:48:43:53
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.100 multicast=yes wireless=IEEE 802.11g
phwhitley@phwhitley-laptop:~$ sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx wl
[sudo] password for phwhitley: 
phwhitley@phwhitley-laptop:~$ sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx wl
phwhitley@phwhitley-laptop:~$ sudo modprobe b43
phwhitley@phwhitley-laptop:~$ sudo iwconfig wlan0 up
iwconfig: unknown command "up"
phwhitley@phwhitley-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

phwhitley@phwhitley-laptop:~$

---

### Post by phwhitley on 2008-10-02
I'll try rebooting and see if that increases speed.

Best, 

Doc pw

---

### Post by Ayuthia on 2008-10-02
> **phwhitley said:**
> Very Cool!  Thanks Ayuthia - I followed your advice and I am now sending you this message within Firefox on Ubutu - and wireless!!!  When I check the speed, it is only showing 1 Mp/s.  When I was plugged in today I was getting much higher speeds.  Is there anyway to speed up the wireless connection?  Also, when I initially ran your recommendations, Windows Wireless Drives (Ndiswrapper) was installed - earlier I was trying all possible combinations earlier and had left it installed.  Having it installed didn't effect wireless connectivity.  I've just uninstalled it and connection remains.  Do I need it, or is it in the way?  Thanks again for your expertise.  Below are the results from your recommendations.  One more question.  Do you know if Evolution Mail will interface with gmail through the POP as I have with Outlook?


You don't need to keep ndiswrapper unless you want to see if it works better.  The b43 driver should automatically adjust the speed for you.  I does seem that the newer kernel produces better results (I am an Arch user and they are using 2.6.26).  The wl driver works well also, but does have some problems when using any type of security.

As for Evolution, I am sure that it will work with POP, but I am not positive on it.  I am a KDE user so I am using KMail (which does work with gmail) but most of the mail applications do support POP.

---

### Post by phwhitley on 2008-10-02
> **Ayuthia said:**
> [QUOTE=phwhitley;5891821]Very Cool!  Thanks Ayuthia - I followed your advice and I am now sending you this message within Firefox on Ubutu - and wireless!!!  When I check the speed, it is only showing 1 Mp/s.  When I was plugged in today I was getting much higher speeds.  Is there anyway to speed up the wireless connection?  Also, when I initially ran your recommendations, Windows Wireless Drives (Ndiswrapper) was installed - earlier I was trying all possible combinations earlier and had left it installed.  Having it installed didn't effect wireless connectivity.  I've just uninstalled it and connection remains.  Do I need it, or is it in the way?  Thanks again for your expertise.  Below are the results from your recommendations.  One more question.  Do you know if Evolution Mail will interface with gmail through the POP as I have with Outlook?

/QUOTE]
You don't need to keep ndiswrapper unless you want to see if it works better.  The b43 driver should automatically adjust the speed for you.  I does seem that the newer kernel produces better results (I am an Arch user and they are using 2.6.26).  The wl driver works well also, but does have some problems when using any type of security.

As for Evolution, I am sure that it will work with POP, but I am not positive on it.  I am a KDE user so I am using KMail (which does work with gmail) but most of the mail applications do support POP.

Thanks again, I was able to get Evolution going with a little tweaking.  What are the "newer kernel products" and can I use them with my WLAN card?  Sorry for the green, newbie questions and thanks a million for the fixes!!

---

### Post by Ayuthia on 2008-10-02
> **phwhitley said:**
> [QUOTE=Ayuthia;5893163]

Thanks again, I was able to get Evolution going with a little tweaking.  What are the "newer kernel products" and can I use them with my WLAN card?  Sorry for the green, newbie questions and thanks a million for the fixes!!

Well, you can always compile your own kernel, but it is probably not recommended when you are first learning Linux.  I am using a different distribution (Arch Linux) and they tend to use the most resent stable kernel that is available (you can see the most recent one at [http://kernel.org](http://kernel.org)).

If you want to use a pre-release kernel, you can always enable hardy-proposed, but there is always a chance of something breaking if you use it.  Once again, it is not recommended unless you know what you are doing or getting yourself into.

So what I am trying to say is that it might be better to keep the current kernel that you have right now until you have a better understanding of Linux.  Of course, you could always try other distributions of Linux where they are running newer versions, but you will find that Ubuntu does keep a fairly new kernel.  Intrepid is looking like it will be using 2.6.27 and it is coming out in a few weeks.

---

