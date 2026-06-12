---
title: "Wi-fi connecting problem"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by viditgoyal3009 on 2010-08-03
my laptop is hp mini 110, i installed a belkins router at my place and there is absolutely no problem connecting internet through windows 7 but i am unable to connect through ubuntu...

---

### Post by Gone fishing on 2010-08-03
Have you installed the wireless drivers?

System > Administration > Hardware drivers

---

### Post by viditgoyal3009 on 2010-08-03
ya..it works with college wi-fi nicely

---

### Post by Gone fishing on 2010-08-03
does the wireless network appear listed when click the networking applet? If it does and you select the network what happens what security are you using?

---

### Post by lotuscribe on 2010-08-03
I am having a similar problem. When I log in, the notification pops up that I am connected to the internet, but when I open firefox, the pages load slowly and nothing happens at all. I thought it was my router or even the cable company is performing maintenance on their servers, but my friend's computer is connecting just fine. 

When I turn on my machine, just before the log in screen, ubuntu gives me  a message that says something about failing to initialize something, but as ubuntu boots up so quickly (apparently this is sometimes a curse), I am unable to read it. Any suggestions? Thanks in advance.

---

### Post by Gone fishing on 2010-08-03
I think you need to find if you have an ip address and then if you can ping the router.

Try opening a terminal and ifconfig it should give your address something like

> wlan0     Link encap:Ethernet  HWaddr 00:21:63:da:80:be  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:63ff:feda:80be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:475 errors:0 dropped:0 overruns:0 frame:0
          TX packets:449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:484617 (484.6 KB)  TX bytes:75977 (75.9 KB)

If you have an address can you ping the router something like ```
ping 192.168.1.1
``` Obviously your router address may be different to mine.

---

### Post by viditgoyal3009 on 2010-08-03
> **Gone fishing said:**
> does the wireless network appear listed when click the networking applet? If it does and you select the network what happens what security are you using?
it shows connecting, it asks for network password and when i enter it it keeps on showing connecting. i am using wap2 security...

---

### Post by Gone fishing on 2010-08-03
OK seems to be WAP2 problem I use WEP (which I don't recommend) but look these links:

[http://ubuntuforums.org/showthread.php?t=1502902&highlight=wap2](http://ubuntuforums.org/showthread.php?t=1502902&highlight=wap2)

[http://ubuntuforums.org/showpost.php?p=9209394&postcount=8](http://ubuntuforums.org/showpost.php?p=9209394&postcount=8)

---

