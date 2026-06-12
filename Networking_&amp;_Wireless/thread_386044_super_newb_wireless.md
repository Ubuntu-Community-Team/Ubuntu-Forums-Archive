---
title: "super newb wireless"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by wclement7 on 2007-03-16
I am a first time Linux user. I am kinda sorta skilled with windows and i am having trouble getting wireless working. I had some guys at my job recommend Ubuntu so i downloaded it and installed it. I have Ubuntu version 6.10 ?edgy?. I have a Dlink gw 510 wireless pci card in my Desktop.

I tried checking the networking interface, and it does not show the wireless connection. So it does not have the correct drivers.. correct? I then fell back on this tutorial...
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
i got confused and nothing seems to be the same so here i am. 

I took this screen shot of device manager-
[IMG]http://i8.photobucket.com/albums/a12/wclement7/Screenshot.png[/IMG]
shows it recognizes the card but is not installed in any way right?

and i also did a ifconfig, not knowing if it would help any? 

eth0      Link encap:Ethernet  HWaddr 00:08:74:BF:28:E8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1284 (1.2 KiB)  TX bytes:1284 (1.2 KiB)


i also downloaded a spare driver for my card for install but i really do not understand where to go from here. I really want to learn and would really enjoy getting the interweb working so i can browse and try things without having to reboot over and over. 
if you can offer any help it would be great! :) 
Thanks,
Willis

---

### Post by Freiburg05 on 2007-03-16
Hi! 

    I've followed a little bit the tutorial you post here, it seems your card it's not natively supported in linux, so your alternative is to use a software called ndiswrapper. I'm not familiar with it, but I think you need the windows drivers for your card, and this software make available to use them in linux. This is the link to ndiswrapper: [http://ndiswrapper.sourceforge.net/]("http://ndiswrapper.sourceforge.net/") You have there a wiki where you can get help.

    That's as far as I can go. May be someone can help you a bit more. Or you can try to follow the tutorials.

    Bye!

---

