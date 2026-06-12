---
title: "How to install Link dot Net Broad band Internet in Ubuntu 8.04 LTS Desktop Edition"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by shameel on 2008-06-12
I am from Pakistan.I am using Link dot Net Broad band internet in windows xp professional.  I just installed Ubuntu 8.04 in my PC. I now want to configure my Paradine Router provided by the Link dot Net in my Ubuntu 8.04. I am not able to configure it in Ubuntu 8.04 of my own. So please help me in doing this.

---

### Post by superprash2003 on 2008-06-12
do you require to use a dialer in windows to connect to the internet? or does the internet work as soon as you switch on your modem?

---

### Post by shameel on 2008-06-13
I am using paradiyne router. this router is connect through a Ethernet Lan card by my PC for connecting me to Link dot Net. I am not using any dialer for connecting to this internet. As i start my PC my internet connection start working in Windows XP Professional. Help line agent of my internet provider don't know how to configure there serves in Ubuntu. 

While in Windows xp, help line agent of that company helped me in changing IP and DNS settings in Internet Protocol (TCP/IP) Properties dialog box. The IP and DNS setting I use to connect to my  Internet are shown in the following figures.

 [img]http://farm4.static.flickr.com/3033/2574174423_8b68cfd2ef_o.jpg[/img]

[img]http://farm4.static.flickr.com/3137/2575000016_2bb2bc77fc_o.jpg[/img]

After these settings my broad band Internet service works smoothly on my Windows XP Professional PC. Now i wanna configure it in Ubuntu as well.

---

### Post by superprash2003 on 2008-06-13
ok.. go to the terminal(Applications->Accessories->Terminal) and type ifconfig and paste the output here

---

### Post by shameel on 2008-06-13
i did this. and the out put is as follows. 
[INDENT]
shameel@shameel-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:b3:9a:3c:cf  
          inet6 addr: fe80::202:b3ff:fe9a:3ccf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5920 (5.7 KB)

eth0:avahi Link encap:Ethernet  HWaddr 00:02:b3:9a:3c:cf  
          inet addr:169.254.8.50  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2470 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:123692 (120.7 KB)  TX bytes:123692 (120.7 KB)

shameel@shameel-desktop:~$ [/INDENT]

---

### Post by superprash2003 on 2008-06-13
go to system->administration->network-> eth0 properties->Select Static ip( instead of roaming mode or dhcp).. and as ip address enter 192.168.1.10 .. gateway as 192.168.1.1 ..click on ok.. and close all windows.. you might need to reboot.. post results after this

---

### Post by shameel on 2008-06-14
I did the followings. But internet is not working again. Please help me.

---

### Post by superprash2003 on 2008-06-14
post an ifconfig output one more time.. and also type ping 192.168.1.1 and post output .. also type ping google.com and post output

---

### Post by shameel on 2008-06-15
dear friend thanks for your help. now my net connection is working properly.

---

