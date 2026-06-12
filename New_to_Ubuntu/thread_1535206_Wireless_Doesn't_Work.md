---
title: "Wireless Doesn't Work"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by bmx666 on 2010-07-20
Hi,
i dont know but my wireless doesn't work from last week.
i didn't install package(i think just Wine).
& it works in Windows 7,but not in Ubuntu 10.04.
this is some information that give from some command (iwlist wlan0 scan,iwconfig,ifconfig):
[PHP]
simo@simo-laptop:~$ iwlist wlan0 scan
wlan0     No scan results

simo@simo-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.

simo@simo-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:19:e5:f9:61  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4384 (4.3 KB)  TX bytes:4384 (4.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:c4:5c:04:c8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/PHP]
pls Help.

---

### Post by JackNocturne on 2010-07-20
First check you if you have the **right drivers** for linux.
What **wireless card** do u have?
```
lspci
```
By the way do you mean it worked recently in **linux** and doesn't work **anymore?**

---

### Post by bmx666 on 2010-07-21
> **JackNocturne said:**
> First check you if you have the **right drivers** for linux.
What **wireless card** do u have?
```
lspci
```By the way do you mean it worked recently in **linux** and doesn't work **anymore?**

Hi
yes,it worked recently,& work in windows 7 now!
it name is "Atheros Wireless Network".
& This is result of "lspci" :
> 
simo@simo-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
03:01.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
0c:00.0 Network controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)


Tnx

---

### Post by JackNocturne on 2010-07-21
From your lspci output i see you have **Atheros AR5001 wireless **network adapter.
Ok, it seems the **drivers for linux **aren't working properly,check this guide out and tell me if you still have problems

<a href="https://help.ubuntu.com/community/WifiDocs/Driver/Atheros" target="_blank">[HTML]https://help.ubuntu.com/community/WifiDocs/Driver/Atheros[/HTML]

---

### Post by bmx666 on 2010-07-21
> **JackNocturne said:**
> From your lspci output i see you have **Atheros AR5001 wireless **network adapter.
Ok, it seems the **drivers for linux **aren't working properly,check this guide out and tell me if you still have problems

<a href="https://help.ubuntu.com/community/WifiDocs/Driver/Atheros" target="_blank">[HTML]https://help.ubuntu.com/community/WifiDocs/Driver/Atheros[/HTML]

Hi
I do these command & tips,but doesn't work.
what can i do right now?

---

### Post by JackNocturne on 2010-07-21
hello again, i did some **little** search and found that some wireless drivers have issues with Ubuntu **10.4** (while in older version they work)

check this out

[http://ubuntuforums.org/showthread.php?t=1498245](http://ubuntuforums.org/showthread.php?t=1498245)



also
[http://madwifi-project.org/](http://madwifi-project.org/)      << Developers of Wireless drivers that support **atheros chipsets**

---

### Post by lkraemer on 2010-07-21
First of all, NO MIXING & MATCHING of METHODS.  Pick one and stay
with it.  If you don't have a good GUIDE, STOP!  Wait for someone
that can supply a good Guide, or until you locate one via SEARCHES.
After all, we can't see what you did two weeks ago......and don't have
a clue as to what you did yesterday........
  
What is the Ubuntu Version? 8.04x, 8.10, 9.04, 9.10, 10.04, ????
32 bit or 64 Bit? .....Yes, it makes a difference!...Depending....
Laptop or Desktop?
USB Wifi Dongle or onboard Wifi?
Are you using the Windows Drivers and Ndiswrapper?  Or how long has it
worked?  Maybe never?  Using Backports?  STA?  Madwifi?
If you are unsure answer all you can and post the output of the commands
below.

First we need to know what hardware your Laptop/Desktop has installed.

Just use "copy & paste" for the commands ONE AT A TIME!!!!!.
And, there is a difference in LSPCI and lspci.
```

uname -r
lspci
lspci -nn
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig
ifconfig

```

Just copy & paste the commands in a Terminal window,
one at a time, and post the results.
(If you are using versions earlier than 9.10, or 9.04 use:
cat /etc/modprobe.d/blacklist)

If you connect via Ethernet cable, SYSTEM -> ADMINISTRATION -> UPDATE MANAGER and then try connecting the Wifi it most likely will work.


Pick one method and stick with it. Don't mix-n-match.

Your options that can be used:
1. Ndiswrapper and a Windows Driver (32 Bit)....??????.inf & sys
Your M$ Windows experience should be used to locate the proper driver....
2. Madwifi Drivers
(you will need to install.....build-essential & headers file.......meaning you need to download & install)
3. Drivers provided by Version 10.04


AFTER YOU GET IT WORKING...........:
Here is a link to get it working after a Kernel Upgrade, or a new
release of Madwifi Drivers with NO Kernel Release:
[http://ubuntuforums.org/showthread.php?t=1142199&highlight=HOWTO%3A+Madwifi](http://ubuntuforums.org/showthread.php?t=1142199&highlight=HOWTO%3A+Madwifi)

madwifi - if yours is supported:
[http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)
Then go to the hal-0.10.5.6 at
[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)

REF:
[http://madwifi-project.org/](http://madwifi-project.org/)
[http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[http://linux.die.net/man/8/modprobe](http://linux.die.net/man/8/modprobe)


32 Bit - Reference URl'S:
[http://www.techmetica.com/howto/how-to-install-windows-wireless-network-device-drivers-in-ubuntu/](http://www.techmetica.com/howto/how-to-install-windows-wireless-network-device-drivers-in-ubuntu/)
[http://www.linuxforums.org/articles/wlan-cards-and-linux_58.html](http://www.linuxforums.org/articles/wlan-cards-and-linux_58.html)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[http://ubuntuforums.org/showthread.php?t=902860&highlight=Atheros+AR242+Driver](http://ubuntuforums.org/showthread.php?t=902860&highlight=Atheros+AR242+Driver)

lk

---

### Post by drpjkurian on 2010-07-21
Hi
I am having atheros card AR5001. Please follow my instruction only if others does not work.See my blog [www.ubuntucrack.blogspot.com]("http://ubuntucrack.blogspot.com/")

---

