---
title: "Hi... please help with wireless..."
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by Nnako2 on 2008-02-16
Hi everyone...

I'm Spanish so sorry if my English is bad, but I need your help 8-[



I had lots of problems with installing Ubuntu 7.10 having Windows Vista at the same PC, but I finally could.


But at the moment I'm at my Windows... That's because I couldn't connect to any wireless with Ubuntu yet.


First of all:
- I'm very very newbie at this stuff, please explain as simple as possible. I'll do all I can, thanks a lot. Don't use difficult English, please, I need explanations for children :(
- I know there are lots of threads like this in the Internet, I've searched and I've tried but nothing works to me.



My PC is an HP laptop.

At Windows I used to connect to the Internet with a wireless connection from a router connected to another PC with Windows XP.

The router is a Belkin 54g and I need to use it for both PCs, for Windows and Ubuntu.



The matter is that I don't know how to connect to the Internet with Ubuntu. I've never done it but with Windows and I don't know what's normal and what's wrong with my Ubuntu. I write my SSID and WAP password at wireless connections but nothing ever happens and I wonder why... :lol:

I've tried to change things from my router at 192.168.2.1 but nothing happens again. It seems as Ubuntu doesn't recognize any connections, any wireless connections, and Windows usually finds mine, the neighbourd's, and much more... but Ubuntu doesn't.

---

### Post by Nnako2 on 2008-02-16
I don't know if this will help but I let you all:





ubuntu@ubuntu:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
10:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
ubuntu@ubuntu:~$

ubuntu@ubuntu:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1A:4B:62:74:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2400 (2.3 KB)  TX bytes:2400 (2.3 KB)

ubuntu@ubuntu:~$

ubuntu@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:~$

---

### Post by Nnako2 on 2008-02-16
Here you have some screenshots of what happens to me:

The matter is that when I write my SSID, I can't choose anyone, there are no SSIDs to choose, I have to write it manual and it seems as it doesn't find anyone, and when I "connect" my wireless it doesn't recognize anything and nothing happens... I don't know, I hope you will help me.

[[img]http://i27.photobucket.com/albums/c181/Nnako2/th_0a23f3fb.png[/img]](http://i27.photobucket.com/albums/c181/Nnako2/0a23f3fb.png)
[[img]http://i27.photobucket.com/albums/c181/Nnako2/th_afa4b73c.png[/img]](http://i27.photobucket.com/albums/c181/Nnako2/afa4b73c.png)
[[img]http://i27.photobucket.com/albums/c181/Nnako2/th_fd8567c5.png[/img]](http://i27.photobucket.com/albums/c181/Nnako2/fd8567c5.png)
[[img]http://i27.photobucket.com/albums/c181/Nnako2/th_5e6bf782.png[/img]](http://i27.photobucket.com/albums/c181/Nnako2/5e6bf782.png)
[[img]http://i27.photobucket.com/albums/c181/Nnako2/th_8bb775d2.png[/img]](http://i27.photobucket.com/albums/c181/Nnako2/8bb775d2.png)
[[img]http://i27.photobucket.com/albums/c181/Nnako2/th_1a928ee2.png[/img]](http://i27.photobucket.com/albums/c181/Nnako2/1a928ee2.png)
[[img]http://i27.photobucket.com/albums/c181/Nnako2/th_8c1cc468.png[/img]](http://i27.photobucket.com/albums/c181/Nnako2/8c1cc468.png)

---

### Post by Nnako2 on 2008-02-16
Anyway, since this below, I've been told that my wifi card is recognized  :roll: 

ubuntu@ubuntu:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
10:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
ubuntu@ubuntu:~$

ubuntu@ubuntu:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1A:4B:62:74:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2400 (2.3 KB)  TX bytes:2400 (2.3 KB)

ubuntu@ubuntu:~$

ubuntu@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0




I've also tried this but I can't scan...


paula@paula-laptop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11b/g ESSID:off/any Nickname:"Broadcom 4311"
Mode:Managed Access Point: Invalid
RTS thr:off Fragment thr:off
Link Quality=0/100 Signal level=-256 dBm Noise level=-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

paula@paula-laptop:~$ sudo iwlist eth1 scan
[sudo] password for paula:
eth1 Interface doesn't support scanning : No such device

paula@paula-laptop:~$ sudo iwlist eth1 scan
eth1 Interface doesn't support scanning : No such device

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:~$ 






Thanks a lot, I'm anxious to try the whole Ubuntu and forget about Windows!! :D

---

### Post by rustybronco on 2008-02-16
>  BCM94311MCG 
See...
[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

---

### Post by Nnako2 on 2008-02-16
> **rustybronco said:**
> See...
[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)


Can I install this without Internet? :confused:

---

### Post by rustybronco on 2008-02-16
Yes you could but you would need to download the necessary packages/files on another machine from the repository/sources then transfer them to your machine. do you have a ethernet cable the you can connect from your machine to the router?, that would be easier.
***EDIT*** WITH ONE EXCPTION "sudo apt-get update" (not to sure on this one)

---

### Post by Hightide on 2008-02-16
Hi Nnako2

you will need internet for rustybronco's link.

tell me if you can see a **wireless connection** entry in System>administration>network


regards

:)

---

### Post by rustybronco on 2008-02-16
[https://help.ubuntu.com/7.10/add-applications/C/offline.html](https://help.ubuntu.com/7.10/add-applications/C/offline.html)

---

### Post by Nnako2 on 2008-02-17
> **Hightide said:**
> Hi Nnako2

you will need internet for rustybronco's link.

tell me if you can see a **wireless connection** entry in System>administration>network


regards

:)

I can only see this 
[[IMG]http://i27.photobucket.com/albums/c181/Nnako2/th_f894ce67.png[/IMG]](http://i27.photobucket.com/albums/c181/Nnako2/f894ce67.png)
but it doesn't recognize any wireless connection...

> **rustybronco said:**
> [https://help.ubuntu.com/7.10/add-applications/C/offline.html](https://help.ubuntu.com/7.10/add-applications/C/offline.html)
I understand nothing of that web but i'll try   

EDIT: I don't know how to do it, sorry



Thank you both

---

### Post by Nnako2 on 2008-02-17
By the way... I don't know what Wireless card I have... :(

---

### Post by rustybronco on 2008-02-17
Your card is a broadcom bcm94311mcg 
[http://www.laptopking.com/boards/958891.jpg](http://www.laptopking.com/boards/958891.jpg)

---

### Post by Nnako2 on 2008-02-17
> **rustybronco said:**
> Your card is a broadcom bcm94311mcg 
[http://www.laptopking.com/boards/958891.jpg](http://www.laptopking.com/boards/958891.jpg)
OK o.o thanks, tell me what to do then please

thanks

---

### Post by rustybronco on 2008-02-17
I'm working on it.
***edit*** i'm not to fast and as time permits
***solution found in the mean time***

---

### Post by Nnako2 on 2008-02-17
> **rustybronco said:**
> I'm working on it.
Thanks thanks :) sorry, take your time, thanks again!!

---

### Post by rustybronco on 2008-02-17
To any one with the same problem the solution was found in this thread 
[http://ubuntuforums.org/showthread.php?t=698506&page=2](http://ubuntuforums.org/showthread.php?t=698506&page=2)

---

