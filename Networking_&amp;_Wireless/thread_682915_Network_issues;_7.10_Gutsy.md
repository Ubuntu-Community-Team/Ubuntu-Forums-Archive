---
title: "Network issues; 7.10 Gutsy"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by wuxarn on 2008-01-30
Hi,


I'm pretty new to ubuntu and Linux.

Anyway, I had a Kubuntu installation and for some reason it stopped working, so I reinstalled it and here comes to problem: I no longer have an internet connection through ethernet, haven't tried wireless since I don't have that at home... Any clues? If it matters, I'm using 7.10 Gutsy edition and dualboot XP. 

Regards, Patrik

---

### Post by TheWizzard on 2008-01-30
> **wuxarn said:**
> Hi,


I'm pretty new to ubuntu and Linux.

Anyway, I had a Kubuntu installation and for some reason it stopped working, so I reinstalled it and here comes to problem: I no longer have an internet connection through ethernet, haven't tried wireless since I don't have that at home... Any clues? If it matters, I'm using 7.10 Gutsy edition and dualboot XP. 

Regards, Patrik

please open a terminal and type:
```
ifconfig
```
and
```
route -n
```
and 
```
cat /etc/network/interfaces
```

post the output of the commands here

---

### Post by jan quark on 2008-01-30
and perhaps the following two commands too

lspci

sudo iwlist scan

---

### Post by wuxarn on 2008-01-30
This feels pretty weird, I tried rebooting before, but now when Ubuntu booted, everything worked perfectly. Thanks anyway

/Wuxarn

---

### Post by Feebz on 2008-02-05
Hello there,

I have the same problem.  The unplug and restart worked once, but since then (i've installed a new video card) the same problem occurs.
Here's the output i'm getting from the above mentioned commands (I'm using DHCP)

feebz@tom-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:76:B8:12:27  
          inet6 addr: fe80::204:76ff:feb8:1227/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6058 (5.9 KB)  TX bytes:7223 (7.0 KB)
          Interrupt:9 Base address:0x4c00 

eth0:avah Link encap:Ethernet  HWaddr 00:04:76:B8:12:27  
          inet addr:169.254.4.36  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:9 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1499 (1.4 KB)  TX bytes:1499 (1.4 KB)





feebz@tom-ubuntu:~$ route - n
Usage: route [-nNvee] [-FC] [<AF>]           List kernel routing tables
       route [-v] [-FC] {add|del|flush} ...  Modify routing table for AF.

       route {-h|--help} [<AF>]              Detailed usage syntax for specified AF.
       route {-V|--version}                  Display version/author and exit.

        -v, --verbose            be verbose
        -n, --numeric            don't resolve names
        -e, --extend             display other/more information
        -F, --fib                display Forwarding Information Base (default)
        -C, --cache              display routing cache instead of FIB

  <AF>=Use '-A <af>' or '--<af>'; default: inet
  List of possible address families (which support routing):
    inet (DARPA Internet) inet6 (IPv6) ax25 (AMPR AX.25) 
    netrom (AMPR NET/ROM) ipx (Novell IPX) ddp (Appletalk DDP) 
    x25 (CCITT X.25) 




feebz@tom-ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


feebz@tom-ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 81)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bu
 IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controlle
0)
00:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
00:0a.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 GS] (rev a1)
feebz@tom-ubuntu:~$ 



I hope you guys can help. I'm using a wired connection.

---

### Post by Feebz on 2008-02-05
My issue has been resolved thanks to the irc forums.  It appears it was my NIC (3com) I installed another NIC i had lying around and it worked fine.

---

