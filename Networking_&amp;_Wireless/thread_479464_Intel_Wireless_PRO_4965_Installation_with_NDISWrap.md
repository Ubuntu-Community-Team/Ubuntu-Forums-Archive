---
title: "Intel Wireless PRO 4965 Installation with NDISWrapper, Driver installed but!...."
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by S15_88 on 2007-06-20
Hey I finally got my Intel Wireless PRO 4965 working using NDISwrapper but there's still a little problem.  Even though the driver is recognized and everything should be good my wifi light isn't on and in my network manager there's nothing for wireless? any ideas?? i've been trying to get this wireless working for a while now and i am so close , thanks for all the help so far!

Thanks, Alain

---

### Post by ndube on 2007-06-20
Assuming you get a "device present" message when you do the following in the terminal

ndiswrapper -l

Did you run the following command to activate the wireless card?

sudo modprobe ndiswrapper

If you did and you still get nothing, do an 'ifconfig' in the terminal and see if the wireless card is listed. If it is, 'ifdown' the card and then 'ifup' the card. If you still get nothing, read the man page for the iwconfig command and try to configure your wireless network manually.

---

### Post by S15_88 on 2007-06-20
Still nothing! Here are all the steps listed and my output, if anyone sees something out of the ordinary please let me know! i've been trying to tackle this wireless for a while and right now it's kicking my butt!  
> 
alain@S15:~$ ndiswrapper -l
netw4v32 : driver installed
        device (8086:4229) present
alain@S15:~$ modprobe ndiswrapper
alain@S15:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:7A:3C:13  
          inet6 addr: fe80::215:c5ff:fe7a:3c13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2091469 (1.9 MiB)  TX bytes:629690 (614.9 KiB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:400 (400.0 b)  TX bytes:400 (400.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:65.94.130.221  P-t-P:64.230.197.229  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:2273 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2019843 (1.9 MiB)  TX bytes:571094 (557.7 KiB)

alain@S15:~$ 



so no wifi light and no wireless connection listed in  the network manager!  what do i do now??

---

### Post by S15_88 on 2007-06-20
ya i've still been unable to get her workin even after tinkering with her all afternoon, wats the deal!?!?!

---

