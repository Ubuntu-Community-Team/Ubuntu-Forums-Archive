---
title: "wireless ubuntu 8.10-dellgx270 p4"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by snout71 on 2009-03-20
i installed ubuntu yesterday and was really suprised how it looks, added edubuntu today.

the only problem i have is trying to get the wireless card installed on my computer to work

below is the info i got from entering lspci,ifconfig etc

paul@paul-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
paul@paul-desktop:~$ 



paul@paul-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:1a:f7:63  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

paul@paul-desktop:~$ 





paul@paul-desktop:~$ sudo lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:01:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 02
       serial: 00:0d:56:1a:f7:63
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k3-NAPI firmware=N/A latency=64 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a4:43:f5:1c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fa:da:45:0f:05:e4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



hope this helps

paul-a very newbie

---

### Post by ivanvajar on 2009-03-20
1. Find WinXP driver for your wireless card
2. Install ndiswrapper with Synaptic (you'll probably find ndisgtk in filelist)
3. run System/Administration/Windows Wireless Drivers
4. Add driver (you select *.inf file)

---

### Post by snout71 on 2009-03-20
unfortunately i overwritten the driver by instaling ubuntu
cannot find disc :(

---

### Post by ivanvajar on 2009-03-20
Try [this]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/how-to-for-the-bcm4318-airforce-one-card-473194/").

---

### Post by ivanvajar on 2009-03-20
On that page there is a statement saying:

> 1) Open a text editor as root and click on File in the top left corner. Then click open. Now open up /etc/modprobe.d/blacklist

To do this open Terminal and type:

> sudo gedit /etc/modprobe.d/blacklist

---

### Post by bobbob1016 on 2009-03-20
Ivanvajar, don't you mean type:

gksu gedit /etc/modprobe.d/blacklist 

It's safer than doing sudo.  gksu sets the permissions for graphical programs the right way, sudo doesn't.  If the program is supposed to be run via command line then you use sudo, if it's a graphical program use gksu.

---

### Post by ivanvajar on 2009-03-20
Yes, it's true. But, this would work also. Don't worry :-) With this particular command you can edit /etc/modprobe.d/blacklist

---

### Post by snout71 on 2009-03-20
ok.

i entered sudo gedit /etc/modprobe.d/blacklist  into the terminal
then added 
#broadcom native driver
blacklist bcm43xx
to the bottom

saved it and closed then opened another terminal and entered 
1.
rmmod bcm4318

but after i entered 1. [enter]
message saying
bash: 1.: command not found

also tried
rmmod bcm4318

and got message 
ERROR: module bcm4318 does not exist in /proc/modules

????

---

### Post by ivanvajar on 2009-03-21
You don't enter

> bcm43xx

You should enter

> bcm4318

---

### Post by ivanvajar on 2009-03-21
> ok.

i entered sudo gedit /etc/modprobe.d/blacklist into the terminal
then added
#broadcom native driver
blacklist bcm43***_xx_***
to the bottom

saved it and closed then opened another terminal and entered
***_1._***
rmmod bcm4318

***_but after i entered 1. [enter]_***
message saying
bash: 1.: command not found

also tried
rmmod bcm4318

and got message
ERROR: module bcm4318 does not exist in /proc/modules

????

You didn't figure it out. You need to enter **bcm4318** instead of **bcm43xx**

---

### Post by ivanvajar on 2009-03-21
OK. I found [this]("http://ubuntuforums.org/showthread.php?t=285809"). Do exactly what it says. It's pretty good 'HOW-TO'

---

### Post by snout71 on 2009-03-21
sorry, i had pasted that bit from the web page

i actually did enter 4318 not 43xx

believe it or not, i am not that stupid??????

---

