---
title: "Help Atheros AR5418 and Aircrack-ng .."
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by usb007 on 2008-05-22
Hello guys .. This is my frist post here ... I just want to say thanks at all this beautiful stuff :) I actually Installed xubuntu on my macbook C2d in dualboot with macosx leopard ..now I just got my Atheros AR5418 wireless card work with xubuntu, but, I am wondering how make my wireless card work with xubuntu and aircrack-ng ... I already used linux before, but, I am still a newbie :) I just want to figure out if my wireless card can work with xubuntu and aircrack-ng and if it can work, how ... I am looking on google, but, I really dont know what do to .. someone told me I need to patch the madwifi driver, but, how ?? I tried this before [http://www.aircrack-ng.org/doku.php?id=madwifi-ng](http://www.aircrack-ng.org/doku.php?id=madwifi-ng)  , but my wireless card didn't work with this patch ... I also want to apologize about my english, I am trying to improuve it :) anyway, below some information about my hardware

```

Linux pietro-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

```

```

02:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)

```

here my dmesg [http://pastebin.com/m66b758cf](http://pastebin.com/m66b758cf) .. is too long to past here :lolflag:

```

ath0      Link encap:Ethernet  HWaddr 00:19:E3:D9:92:C2  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:e3ff:fed9:92c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:74362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56594 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:106027956 (101.1 MB)  TX bytes:4482418 (4.2 MB)

eth0      Link encap:Ethernet  HWaddr 00:19:E3:34:29:C8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-19-E3-D9-92-C2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146810 errors:0 dropped:0 overruns:0 frame:4346
          TX packets:56961 errors:343 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:129879026 (123.8 MB)  TX bytes:5742180 (5.4 MB)
          Interrupt:16 

```

Thanks

---

### Post by usb007 on 2008-05-22
nobody has any idea ??? :(

---

### Post by kzeouki on 2009-02-17
Full tutorials can be found:

[http://www.aircrack-ng.org/doku.php](http://www.aircrack-ng.org/doku.php)

---

