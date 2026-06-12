---
title: "TP-LINK TG-3269 Gigabit PCI Network Adapter not recognised by Ubutu"
date: 2016-11-26
forum: Networking &amp; Wireless
---

### Post by rwmingis on 2016-11-26
Hi Everyone,

I've just updated my ASUS barebones PC from Windows xp to Ubuntu to breath new life into it.  The install went smoothly (once i replaced a corrupted downloaded install file) but I cannot get the Ethernet adapter working, and was hoping someone who has experienced this issue could help me out.  I've not been able to figure it out based on my searches through the forums.  

Here's a bit of background info:


[LIST]
[*]The network card is a TP-LINK TG-3269 Gigabit PCI Network Adapter (PCI card)
[*]It was bought to replace the on-motherboard atheros LAN adaptor which was damaged in a storm and now I've just disabled in the BIOS and use the new PCI card.
[*]It worked completely fine under Windows XP, only quit working upon switching to Ubuntu.
[*]During startup, the lights on the  back of the adapter light up fine showing network connectivity, but once Ubuntu loads, they all turn off.
[*]The pulldown menu at the top says 'Ethernet Network Disconnected' and is greyed out.
[*]I have a USB wifi adapter to get me by in the mean time, and that works OK, but slow
[*]I have managed to download the drivers here [http://www.tp-link.com.au/download/TG-3269.html#Driver](http://www.tp-link.com.au/download/TG-3269.html#Driver)  but don't really know what to do with them in Linux.
[/LIST]

When I do an lspci command, i get all the bits, but I believe this is the card:


[LIST]
[*]02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller (rev 10)
[/LIST]

When I do an ifconfig -a command i get this:

```
enp2s0    Link encap:Ethernet  HWaddr 30:b5:c2:03:30:fd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:11795 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11795 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:1149374 (1.1 MB)  TX bytes:1149374 (1.1 MB)

wlx00146caf826c Link encap:Ethernet  HWaddr 00:14:6c:af:82:6c  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2183:f618:954e:783f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:122493 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97447 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:129790355 (129.7 MB)  TX bytes:11936630 (11.9 MB)
```

I am quite new to linux, so am not great at the commands in the terminal.  Does anyone have any ideas?

Many thanks!

Rob

---

### Post by jeremy31 on 2016-11-26
*Thread moved to **Networking & Wireless**.*
welcome to the forums

please post results for ```
lscpi -nnk | grep -iA2 net
```

---

### Post by rwmingis on 2016-11-26
Thanks Jeremy!  Results below:


[FONT=courier new]rob@TheServer:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller [10ec:8169] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8169/8110 Family PCI Gigabit Ethernet NIC [10ec:8169]
    Kernel driver in use: r8169
    Kernel modules: r8169
[/FONT]

---

