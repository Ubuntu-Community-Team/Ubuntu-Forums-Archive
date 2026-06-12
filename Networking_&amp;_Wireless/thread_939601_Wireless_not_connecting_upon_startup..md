---
title: "Wireless not connecting upon startup."
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by mark|dvlboy on 2008-10-06
Ok now I am well aware that there is probably something somewhere about this exact probem but I really do not have the time sorry. I don't even have the time to be messing with this problem at the moment either.

Anyway.

My problem is that it seems my wireless is not connecting properly upon startup of my ubuntu system. I configured my Compaq Presario C742TU's Atheros AR5006/7 [windows says different to ubuntu] wireless adapter following [_THESE INSTRUCTIONS_]("http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/") and connected it to my home network with the help of [_THIS_]("http://ubuntuforums.org/showthread.php?t=202834") post.

Generally, it all works fine...until I restart my laptop. When I log in my browser doesn't load any pages so I go to Terminal and enter ifconfig. My Network Cards appear but there are two wlan0's [the second says wlan0:avahi]. I check my

*/etc/network/interfaces*

file to find that it is the same as it was when I shut the computer down. I try to restart the network using

*gksu /etc/init.d/networking restart*

but when it reaches the point of _DHCP*RENEW??*_ it is searching on *255.255.255.255* and does not achieve anything. after a while of *ifdown*-ing and *ifup*-ing I finally get the thing connected but it takes too long and is really annoying. Occasionally also the interfaces file changes during network restarting. Luckily I made a backup of the file when it worked one day and I simply copy its contents across.

However annoying this may be though I am reluctant to go back to booting off my laptops HDD into [dare I speak its dreadful name] _*Vista*_.:|

I am highly uneducated in the area of Ubuntu but am going to make an effort to learn a hell of a lot more and will hopefully then be able to help others and more importantly myself.

I apologise for so much text and if I have missed any information you feel is needed please ask for it.

Thanx, Mark

---

### Post by lisati on 2008-10-06
[http://ubuntuforums.org/showpost.php?p=1351902&postcount=2](http://ubuntuforums.org/showpost.php?p=1351902&postcount=2) has some ideas for dealing with networking not properly starting on boot-up

---

### Post by mark|dvlboy on 2008-10-06
> **lisati said:**
> [http://ubuntuforums.org/showpost.php?p=1351902&postcount=2](http://ubuntuforums.org/showpost.php?p=1351902&postcount=2) has some ideas for dealing with networking not properly starting on boot-up

I was gonna say nah tried it already but decided to just try it again. And once again no win.

Any ideas?

I am confused as to why it is saying:

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval # [#=ranges from 3 to 14]

:when I *ifup wlan0*

Also do you have any idea what *wlan0:avahi* would mean?

this is my *ifconfig*:

```
mark@mark-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2425 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:125985 (123.0 KB)  TX bytes:125985 (123.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:6e:19:9f  
          inet6 addr: fe80::21f:3aff:fe6e:199f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:465 errors:0 dropped:0 overruns:0 frame:0
          TX packets:799 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:259154 (253.0 KB)  TX bytes:137671 (134.4 KB)
          Interrupt:22 Memory:91300000-91310000 

wlan0:avahi Link encap:Ethernet  HWaddr 00:1f:3a:6e:19:9f  
          inet addr:169.254.5.93  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Memory:91300000-91310000 
```

---

### Post by mark|dvlboy on 2008-10-13
Ok well I have semi solved my problem but not entirely sure how.

All I remember is that I stuffed around with my

```
/etc/network/interfaces
```

file a got it set up for *one* of my networks. Then uninstalled NM because it wasn't working for me. I then got Network Selector??? and now I just have to restart networking on the laptop and wait a minute or two. I think I did something else in there too but no idea what because i got to the point of not caring what happened and tried alot of things.

Now I have another problem [should probably make another post for it]. I use my laptop in two different places and therefore have two different wireless networks. Is there a way I can set my interfaces file to basically run an IF statement???

```
IF network1 = available, connect
ELSEIF network2 = available, connect
ELSE /etc/init.d/networking stop
```

Something like that anyways.

I will search for it myself for a while and return with a yay or nay. [basically just thinking out loud]

Thank you

---

### Post by Kiefer Rodriguez on 2008-10-13
> **mark|dvlboy said:**
> Ok well I have semi solved my problem but not entirely sure how.

All I remember is that I stuffed around with my

```
/etc/network/interfaces
```

file a got it set up for *one* of my networks. Then uninstalled NM because it wasn't working for me. I then got Network Selector??? and now I just have to restart networking on the laptop and wait a minute or two. I think I did something else in there too but no idea what because i got to the point of not caring what happened and tried alot of things.

Now I have another problem [should probably make another post for it]. I use my laptop in two different places and therefore have two different wireless networks. Is there a way I can set my interfaces file to basically run an IF statement???

```
IF network1 = available, connect
ELSEIF network2 = available, connect
ELSE /etc/init.d/networking stop
```

Something like that anyways.

I will search for it myself for a while and return with a yay or nay. [basically just thinking out loud]

Thank you

I will give you a hint, mainly because I am supposed to be working and dont have time to fully help you out like I would prefer - When networking starts, the scripts in ```
/etc/network/if-up.d/
```
are ran, get what Im saying? :) Dont put your statement in /etc/network/interfaces, thats not its purpose :).

---

