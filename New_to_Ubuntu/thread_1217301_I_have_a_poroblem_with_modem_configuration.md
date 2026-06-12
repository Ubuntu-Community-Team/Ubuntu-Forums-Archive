---
title: "I have a poroblem with modem configuration"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by hadi3457 on 2009-07-19
Hi all I have a problem. please help me! My modem is DSL 200 III  I downloaded an ECIADSL package and install it (with double click on it) and do eciadsl-config-text successfully.
when I write eciadsl-start and ubuntu start to work will arrive to a line:
 waiting for tap0
 and I write pppeoconf tap0 and a new blue window will open and ask some question and tell me it made a connection. 
then I write pon dsl-provider and it answer:

 Plugin rp-pppoe.so loaded. RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5 /usr/sbin/pppd: In file /etc/ppp/peers/dsl-provider: unrecognized option 'nic-tap0'

 when I write ifconfig answer: 
root@ubuntu:~# ifconfig lo        Link encap:Local Loopback             inet addr:127.0.0.1  Mask:255.0.0.0           inet6 addr: ::1/128 Scope:Host           UP LOOPBACK RUNNING  MTU:16436  Metric:1           RX packets:72 errors:0 dropped:0 overruns:0 frame:0           TX packets:72 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:0            RX bytes:5544 (5.5 KB)  TX bytes:5544 (5.5 KB)  pan0      Link encap:Ethernet  HWaddr 96:c3:1f:a1:99:d4             inet6 addr: fe80::94c3:1fff:fea1:99d4/64 Scope:Link           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1           RX packets:0 errors:0 dropped:0 overruns:0 frame:0           TX packets:12 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:0            RX bytes:0 (0.0 B)  TX bytes:636 (636.0 B)

 and in other comand:

 root@ubuntu:~# route -n Kernel IP routing table Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

 and I have not any conecting. please help me. In my area are't any linux group. thanks all

---

### Post by ZhuaSD on 2009-07-22
why do you have a virtual ethernet connection there?  That is what a tap0 usually means, I guess.

Pls look at:

[http://ubuntuforums.org/showthread.php?t=1176117](http://ubuntuforums.org/showthread.php?t=1176117)

[http://ubuntuforums.org/showthread.php?t=1147360](http://ubuntuforums.org/showthread.php?t=1147360)

Run sudo pppoeconf, sudo ifconfig, sudo lspci, post output.

---

### Post by hadi3457 on 2009-08-13
[B]really sorry for my late! We are between a really war here and ... some times gun and some times pencil! really sorry!!!

OK I start it again and read up link carefully and test some ideas in there but I can,t connect still. This commands results are:

[/B]```


ifconfig

lo        Link encap:Local Loopback  
    
      inet addr:127.0.0.1  Mask:255.0.0.0
    
      inet6 addr: ::1/128 Scope:Host
     
     UP LOOPBACK RUNNING  MTU:16436  Metric:1
     
     RX packets:12 errors:0 dropped:0 overruns:0 frame:0
     
     TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
     
     collisions:0 txqueuelen:0 
     
     RX bytes:832 (832.0 B)  TX bytes:832 (832.0 B)

pan0   
   Link encap:Ethernet  HWaddr 52:c9:0e:a0:cb:b7  
   
       inet6 addr: fe80::50c9:eff:fea0:cbb7/64 Scope:Link
     
     UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
     
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     
     TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
     
     collisions:0 txqueuelen:0 
    
      RX bytes:0 (0.0 B)  TX bytes:636 (636.0 B)


```

 and other command is:

```


lspci

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 630 Host (rev 30)
00:00.1 
IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 
ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:01.2 
USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:01.3 
USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.0 
PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:05.0 
Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0e.0 
Communication controller: Agere Systems V.92 56K WinModem (rev 02)
01:00.0 
VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA 
Display Adapter (rev 21)


```


thank you very much for your answer my friend. I think I follow all commands truly and I think I havea problem with some thing who named "nic-tap0" !!! I have this error:

```


pon dsl-provider

Plugin rp-pppoe.so loaded.

RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
/usr/sbin/pppd:
 In file /etc/ppp/peers/dsl-provider: unrecognized option 'nic-tap0'


```

---

### Post by hadi3457 on 2009-08-14
Tonight I test some things that think may be useful for everybody that like help me:
I run eciadsl-doctor for 3 step. between every step I turn off and turn on modem again. in two first step nothing happened but in three step I had a tap in pppoeconf command but scan couldn't find that. I run "pppoeconf tap0 "   and in multimode scan it fined some data and I could make a connection with that and when I run "pon dsl-provider" it was run but wasn't connect!

unfortunately I remove pppoeconf pakage with:
```

apt-get --purge remove pppoeconf

``` 

some body in this forum said it may be answer! I don't know how I must repair it if this is mistake!!! please tell it too!!!
my experience codes are here(I hope it can help to you for help to me!!!):

```

eciadsl-doctor
You are using pppd version 2.4.5 (untested)

No existing PPP connection... trying to make one (please wait)

.........( and it started to search for chanels of 1 and 2 and 3 and ....).......

using channel 19

Using interface ppp0
Connect: ppp0 <--> /dev/pts/1

Modem hangup


...............!!!



Connection terminated.

PPP: very bad ... usermode driver just crashed

```
and now I had a tap0 in "pppoeconf" but couldn't scan it. I run "pppoeconf tap0" and then:
```

pon dsl-provider

Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5

root@ubuntu:~# ping www.google.com

ping: unknown host www.google.com

```

I wasn't conect! but it seem all things are good!

and this in additional:
```

ifconfig


lo        Link encap:Local Loopback  
    
      inet addr:127.0.0.1  Mask:255.0.0.0
     
     inet6 addr: ::1/128 Scope:Host
    
      UP LOOPBACK RUNNING  MTU:16436  Metric:1
     
     RX packets:204 errors:0 dropped:0 overruns:0 frame:0
     
     TX packets:204 errors:0 dropped:0 overruns:0 carrier:0
     
     collisions:0 txqueuelen:0 
    
      RX bytes:15456 (15.4 KB) 
 TX bytes:15456 (15.4 KB)

pan0   
   Link encap:Ethernet  HWaddr 1e:90:54:65:78:79  
    
      inet6 addr: fe80::1c90:54ff:fe65:7879/64 Scope:Link
     
     UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
     
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
    
      TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
     
     collisions:0 txqueuelen:0 
    
      RX bytes:0 (0.0 B)  TX bytes:1308 (1.3 KB)

tap0   
   Link encap:Ethernet  HWaddr ce:5f:dd:ff:bc:3a  
    
      inet6 addr: fe80::cc5f:ddff:feff:bc3a/64 Scope:Link
    
      UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
     
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     
     TX packets:447 errors:0 dropped:0 overruns:0 carrier:0
     
     collisions:0 txqueuelen:500 
     
     RX bytes:0 (0.0 B) 
 TX bytes:112563 (112.5 KB)


tap0:avahi
 Link encap:Ethernet  HWaddr ce:5f:dd:ff:bc:3a  
    
      inet addr:169.254.9.41  Bcast:169.254.255.255  Mask:255.255.0.0
     
     UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

```

Thank you all

---

### Post by hadi3457 on 2009-08-16
Hi all again!
tonight I tested another things. I reinstalled my ubuntu and my pppoeconf package come back! I go to "/etc/ppp/peers/" and in "dsl-provider" file I changed "nic-tap0" with "nic-pan0" (without any information!) now I haven't "nic-tap0" unrecognized option error and pppoe.so package are loaded without any error but still I am not connect! 

Please help me if you understand what I must do!

I am pleasure that send us codes in this file if you are connect:
/etc/ppp/peers/dsl-provider

thank you so much!

---

### Post by hadi3457 on 2009-08-20
Help! Help! Help!
Please!!!

---

