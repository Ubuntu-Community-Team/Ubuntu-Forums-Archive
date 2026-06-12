---
title: "No connection to internet! Please help."
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by Bedde on 2008-01-03
Hi, i'll get straight to the point. I've been searching everywhere for answers but im no good at finding them. This is what i need from the ubuntu community, some help to connect to the internet.
I have three other pc:s running at home with xp/vista with no problems, but i recently decided to try the woderful world of ubuntu, but regular ubuntu was to demanding so i installed xubuntu and it works fine.
Just the on thing, connecting to the internet. (I can go online with the install cd but not without it)

My other computers are using dhcp (wired),

Please help me, i need step by step instructions to be able to connect to the network.

If there is special info you need about my system tell me.

/thanks for reading and replying

---

### Post by Old *ix Geek on 2008-01-03
You're going to have to provide more info in order to get meaningful help. For example, is the Ubuntu box using wireless or is it wired like your other PCs? Start with that, and also the computer's brand.  If this is a dual boot setup [with windoze], does the Internet connection work if you're booted up under 'doze?

---

### Post by hsweet on 2008-01-03
A bit of info you can send back is what comes back to you from the ifconfig command. (Type it into a terminal (that's in application menu/accessories)

Here is what mine says about my (wired) ethernet connection

eth2      Link encap:Ethernet  HWaddr 00:04:61:9C:85:8F  
          inet addr:192.168.254.3  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::204:61ff:fe9c:858f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40536 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50266 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19747722 (18.8 MB)  TX bytes:48178967 (45.9 MB)
          Interrupt:18 Base address:0xec00 

You will at least see if you have an address.  You can send that back here and somebody will probably know something.
good luck

---

### Post by Bedde on 2008-01-04
Its an old laptop, with wired connection, and its not using dual boot only xubuntu 7.10 (dont know what doze is?)

This is some info i get out of it:

eth0          Link encap:Ethernet  HWaddr 00:02:3F:B0:63:2D
                 inet addr: 192.168.0.117  Bcast:192.168.0.225  Mask:225.255.255.0
                 inet6 addr:  fe80::202:3fff:feb0:632d/64 Scope: Link
                 UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
                 RX packets:1 errors:0 dropped:0 overruns:0 frame:0
                 TX packets: 12 errors:0 dropped:0 overruns:0 carrier:0
                 collisions:0 txqueuelen:1000
                 RX bytes:342  (342.0 b)  TX bytes: 2516  (2.4 kb)
                Interrupt:11 Base address:0x6800


lo             Link encap:Local Loopback
                inet addr: 127.0.0.1  Mask:255.0.0.0
                inet6 addr:  ::1/128 Scope:Host
                UP LOOPBACK RUNNING MTU:16436 Metric:1
                RX packets:16 errors:0 dropped:0 overruns:0 frame:0
                TX packets: 16 errors:0 dropped:0 overruns:0 carrier:0
                collisions:0 txqueuelen:0
                RX bytes:1408  (1.3 k b)  TX bytes: 1408  (1.3 kb)

---

### Post by Bedde on 2008-01-04
i get get a ip address wth both roaming mode and dhcp, dont know what to do??

---

### Post by Dogalot on 2008-01-04
I have a simular question.

I have Ubuntu 7.10 on a Toshiba Satelite 4600 (only - no other system) (dose - is another system - like Windows XP). 

Except - my issue is a little different.  Yesterday, I brought the computer into work, and connected the cable, and was online fine.  But when I got home, I connected wireless - but only two websites (my Juno email, and to ubuntu forum link from my email) worked, and going to yahoo, google and others timed out (actually after getting to the forum, it started to time out as well... Then I connected it directly to the router -- but still timed out.

Sorry, I am not at home at the moment, so I can not do the Ipconfig to give you more, but will when I can...

Thanks!!

---

### Post by Dogalot on 2008-01-04
I connected the cable from the router to the computer.  If I type 192.168.0.1, I pull up the router just fine.  And like I said, Juno.com works (a bit slower, but works), but no other site seems to work.

---

### Post by Bedde on 2008-01-05
Could someone help me please?

---

### Post by WedgeHG on 2008-01-05
Dogalot: sounds like it could be a DNS issue. Go to System -> Administration -> Network and click on the DNS tab and tell us what is there.

Bedde: are you able to log into your router? It looks like you are getting an IP address so try putting 192.168.0.1 into the address bar of your browser.

---

### Post by sdide on 2008-01-05
Seems like you are connected to your router fine, at least it seems like it is providing you with a IP-address.
try a few things; 
1: 
$ ping -c 3 192.168.0.1
2:
$ ping -c 3 [www.google.com](www.google.com)
3:
$ ping -c 3 66.249.93.99

and post the output of those commands. please.

---

### Post by Dogalot on 2008-01-07
Thanks!

I'll have to get this to you... But actually I think I have it working.  I found I needed the DNS (primary and secondary) numbers supplied by my ISP.  Sorry to have bothered you.  I would like to do those Ping tests just to see the results.  Thanks again for your information, maybe there is something that can be tweeked to make it better...

David

---

