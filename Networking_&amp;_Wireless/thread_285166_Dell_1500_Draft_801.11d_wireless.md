---
title: "Dell 1500 Draft 801.11d wireless"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by rrryyyaaannn on 2006-10-26
Okay, so I setup ndiswrapper on my Dell Inspiron 640m with a Dell 1500 Draft 802.11n/b/g WLAN mini card in it. According to Ubuntu, "the driver is intalled, and the hardware is present," and yet I get no indication of it's presence in the network window, etc. My ethernet card works just fine. I was talking to someone who knows more about this than I, and he gave me the following commands, and said I should post them here. Here's what I got:

ryan@Weakling:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:6C:1E:2C
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:672 (672.0 b)  TX bytes:672 (672.0 b)

ryan@Weakling:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ryan@Weakling:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present





Any thoughts?
-Ryan

---

### Post by rrryyyaaannn on 2006-10-27
nothing?

---

### Post by atenlaugh on 2006-10-30
I got it to work by compiling the latest version of ndiswrapper (1.28) and using the official Dell drivers. For the record, this is a Broadcom 4321 chip.

Download the driver from here: [http://ftp.us.dell.com/network/R129083.EXE]("http://ftp.us.dell.com/network/R129083.EXE")

Unzip R129083.EXE, and it'll output a bunch of files, including a "DRIVER" folder, which contains the .inf and .sys files needed. 

Use ndiswrapper as directed here: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation"), being sure to remove any of your previous attempts before trying another.

The latest version of ndiswrapper can be found here: [http://sourceforge.net/projects/ndiswrapper/]("http://sourceforge.net/projects/ndiswrapper/")

---

### Post by theotherjoey on 2007-05-23
I've been having this same problem with this same chip on an HP. :(

---

