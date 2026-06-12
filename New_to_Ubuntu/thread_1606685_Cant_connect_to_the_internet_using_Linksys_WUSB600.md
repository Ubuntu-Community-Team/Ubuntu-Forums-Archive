---
title: "Cant connect to the internet using Linksys WUSB600N wifi router"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by Jables2121 on 2010-10-26
I just installed Ubuntu 10.04 and I can't connect to the internet I am using a liksys wusb600n wifi router and I am very new to ubuntu I am also running windows 7 I don't know what to do so please help asap I would like to be able to use Ubuntu thank you

---

### Post by anewguy on 2010-10-26
First off my research shows the WUSB600N is a USB wifi adapter, not a router.  I have seen some posts on the net that indicate it should work out of the box, and others have talked about getting a driver.

So, to further help you we need more information:

- if you right-click on the network manager icon, is the "Enable Wireless" checked?  If not, check it to enable wireless.

- if you left-click on the network manager icon does it show any available wireless networks?

It would also help us if you could provide the following:

- open a terminal window (Applications/Accessories/Terminal)
- type:

lsusb <press enter>  Post the output back here

lshw -C network <press enter>  Post the output back here

ifconfig <press enter>  Post the output back here

iwconfig <press enter>  Post the output back here

Thanks
Dave ;)

---

### Post by Jables2121 on 2010-10-26
[SIZE=3][FONT=Calibri]                -when I right clicked both enable networking and enable notifications were checked[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]                -when I left clicked it did not show any networks, but it did yesterday[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri] jables@ubuntu:~$ lsusb[/FONT][/SIZE]
[FONT=Calibri][SIZE=3]Bus 002 Device 008: ID 043d:013f Lexmark International, Inc. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Bus 002 Device 007: ID 0bc2:2120 Seagate RSS LLC [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Bus 002 Device 006: ID 1737:0071 Linksys [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Bus 002 Device 005: ID 0424:2524 Standard Microsystems Corp. USB MultiSwitch Hub[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Bus 002 Device 004: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Bus 002 Device 003: ID 0461:4d80 Primax Electronics, Ltd [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]Bus 002 Device 002: ID 8087:0020  [/FONT][/SIZE]
[FONT=Calibri][SIZE=3]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Bus 001 Device 003: ID 05e3:0716 Genesys Logic, Inc. [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]Bus 001 Device 002: ID 8087:0020  [/FONT][/SIZE]
[FONT=Calibri][SIZE=3]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]jables@ubuntu:~$ lshw -C[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Hardware Lister (lshw) - B.02.14[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]usage: lshw [-format] [-options ...][/SIZE][/FONT]
[SIZE=3][FONT=Calibri]       lshw -version[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]                -version        print program version (B.02.14)[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]format can be[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]                -html           output hardware tree as HTML[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]                -xml            output hardware tree as XML[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]                -short          output hardware paths[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]                -businfo        output bus information[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]options can be[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]                -class CLASS    only show a certain class of hardware[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]                -C CLASS        same as '-class CLASS'[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]                -c CLASS        same as '-class CLASS'[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]                -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]                -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]                -quiet          don't display status[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]                -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]                -numeric        output numeric IDs (for PCI, USB, etc.)[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]jables@ubuntu:~$ ifconfig[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]eth0      Link encap:Ethernet  HWaddr 00:01:6c:58:cf:af  [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]          collisions:0 txqueuelen:1000 [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]          Memory:fe400000-fe420000 [/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]lo        Link encap:Local Loopback  [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]          inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]          RX packets:208 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]          TX packets:208 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]          collisions:0 txqueuelen:0 [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]          RX bytes:19042 (19.0 KB)  TX bytes:19042 (19.0 KB)[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]jables@ubuntu:~$ iwconfig[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]lo        no wireless extensions.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]eth0      no wireless extensions.[/SIZE][/FONT]

---

### Post by Jables2121 on 2010-10-26
i also cannot use an ethernet cable because my router is too far away from my computer
 
 
:guitar:

---

