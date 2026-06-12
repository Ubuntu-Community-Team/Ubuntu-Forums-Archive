---
title: "Wireless Connection Dropping"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by mattywarr on 2008-07-29
Hello,

I'm having regular problems with my wireless connection on Ubuntu 8.04.

I'm using an Acer Aspire 5020 with a Broadcom wireless card, with proprietary drivers/bwcutter installed.

Sometimes it works fine for hours, other times it only works for 10 minutes.

What happens is, I boot the machine, and after a while the connection just stops working. The wireless signal strength bar drops to zero and the list of wireless networks is totally empty.

Has anyone seen this/have a fix for it?

Thanks,
Matt

---

### Post by trigsenior on 2008-07-29
hello,

I had this problem in 7.10 and found no fix , had to upgrade to hardy and it worked fine. This is not a permanent fix but just to save you rebooting
you this command ifup. Man ifup to find out how it works.

Could you run this command when your internet dies 
 
ifconfig -a

and paste the results here ?

ps : have a look round forums quite a few people have same problem =)

---

### Post by kurrier on 2008-07-30
i've been having the same issue with 8.04. sometimes wireless will work no problem for hours, other times will just freeze up and have to (ifdown wlan0, ifup wlan0). never had this issue with 7.10, kind of regret upgrading everything runs a lot worse with this newer version. also tried different cards, same issue.

---

### Post by mattywarr on 2008-07-30
Thanks for the tips. Had a nose around the forum and kept finding failures!

I tried ifup -a and it did nothing. I havent tried ifdown-a first, will try that when it goes down again (probably within the hour!)

Here is the results from my ifconfi -a

> matt@matt-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:e0:60:4d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x8400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2086 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2086 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:114450 (111.7 KB)  TX bytes:114450 (111.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0e:9b:b9:5e:3f  
          inet addr:192.168.3.10  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:9bff:feb9:5e3f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:43237 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47546 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35105580 (33.4 MB)  TX bytes:23425904 (22.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-0E-9B-B9-5E-3F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Thanks for your help this far :)

---

### Post by cdtech on 2008-07-30
I had problems using the Network Manager and switched to wicd, I haven't lost a connection so far on my wireless.....

---

### Post by mattywarr on 2008-08-03
I've now installed WICD and will see how it goes!

---

### Post by mattywarr on 2008-08-05
Just thought i'd post to say this has done the trick so hopefully someone else will find this useful!

---

### Post by ilanesh on 2008-08-05
I can not find WICD in the repository, from where can I get this?
thanks.

---

### Post by cdtech on 2008-08-05
Add this to your "sudo gedit /etc/apt/sources.list"
```
deb http://apt.wicd.net **hardy** extras
```
Be sure to change **hardy** to whatever flavor your using.

Then do "sudo apt-get update"
Then "sudo apt-get install wicd"

---

