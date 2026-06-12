---
title: "connect to internet hp zd7000"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by puppetj on 2007-06-29
well after searching and not finding anything that makes sense to me, i need your help i have a hp zd7000
and my wifi nic is installed in the system , so it supported...but i not sure if i'am connecting to my linksys wap "WAP54G" correctly i goto create new wireless network, and enter the network name, which is the ssid right? if so i enter that, and none for security, b/c i have none for it setup, then i hit connect bit all the bars are white and if i hover over the bars connection "wireless network connection to "(the name)" (0%), 
why i'am i not getting any signal or connection is beyond me?! i'am of course in range...i tried the manual way but that doesnt help, and as for the network encryption i can put none, why???

---

### Post by puppetj on 2007-06-30
ok, so can you please help me?

---

### Post by kevdog on 2007-06-30
What kind of wireless NIC do you have in your system??  If you do not know then please post

lshw -C network
lspci

Did you do anything special to install drivers for your built-in NIC?

---

### Post by puppetj on 2007-06-30
first of thanks for replying, ye sorry i didnt post that, well it's broadcom 4306 b/g wifi nic , i didnt do anything different it just installed  ubuntu... let me know if you need anything from the "device manager"..

---

### Post by puppetj on 2007-07-02
Help!

---

### Post by puppetj on 2007-07-02
correction ubuntu shows my wifi card as broadcom 4306, but windows shows it as broadcom 4320 hope this help

---

### Post by kevdog on 2007-07-02
Run the following commands in a terminal "type them" and then post the output.  You can cut and paste.  I cant help you if you cant help me!

lshw -C network
lspci

---

### Post by puppetj on 2007-07-02
ok here it is: (btw the wired nic does work any more (the hardware died)

  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:30:bf:6d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:3000-30ff iomemory:d2007800-d20078ff irq:21
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 02
       serial: 00:90:4b:4c:96:8d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=32 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:d2004000-d2005fff irq:22






00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV31M [GeForce FX Go5600] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:01.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 02)
02:01.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
02:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

---

### Post by kevdog on 2007-07-02
Did you use any method to install drivers for this card??  There are only two methods --- ndiswrapper or bcm43xx-cutter.  If you dont know what Im talking about or didnt use either one of these two methods then you have not installed the driver for you card, and hence the reason it is not working.  If you did use either method, please tell me so we can troubleshoot the installation.

---

### Post by puppetj on 2007-07-02
i used neither, if it not installed then, why does it show up in the device manager? and i saw steps on the wrapper, but dont i need to be connected to a wired connection to follow the steps, i cant do that since my wired nic doesnt work anymore, it does show up, but it does work anymore, and it nor disabled, it just dead....
if this is a issue how can i go about installing the wrapper?

thanks

---

### Post by kevdog on 2007-07-02
Try this thread first -- I couldnt have written it any better:
[http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom)

---

### Post by puppetj on 2007-07-03
yes but in the post it's says
"In other words you should have your Ethernet cable plugged in before you try to install."

remember my wired doesnt work.

---

### Post by kevdog on 2007-07-03
What about the bash script installer method?  You may have to download the files to USB stick and then transfer to computer that way!

---

### Post by puppetj on 2007-07-03
ill try it, dont have usb stick but ill burn file

---

### Post by puppetj on 2007-07-04
ok, then kinda worked, but i get the wireless bars filled blue all of them, but still no internet, and it's 11mbps, this it a 802.11g it should be 54 at least, i check the connection info  and it's says 0.0.0.0 for ip address and everything else. and yes i did restart.

---

### Post by puppetj on 2007-07-06
please help i'am getting so close :)

---

### Post by puppetj on 2007-07-07
ok, i's working now, not sure why, but i'am grateful to get it working, but how do i get 54mps, it a b/g and i'am only getting 11mps

---

### Post by kevdog on 2007-07-08
Not that it matters but the bcm43xx drivers max out at 11Mb/sec.  If you want 54Mb/sec we are going to have to undo the installation, and install ndiswrapper.  Its slightly more complex, but it would give you want you want.  Worse case scenario, if the installation fails (not sure why it would), you could easily make one change in a file and then revert back to bcm43xx.

---

### Post by puppetj on 2007-07-08
1st of how do i uninstall what was done, then whats the next step???



well i can just install ndiswrapper, which i did with automitax, then just run it, browse the driver and thats it? there is an issue with that, the hp ws doesnt have the latest driver, but for some reason i can get the latest driver from windows update....so how would i get if from that source? what i mean is in xo where would the driver files go system32? what do i need for this to work, or maybe easiler would you know a safe place to get the latest drivers.?

---

### Post by puppetj on 2007-07-10
Hello?

---

