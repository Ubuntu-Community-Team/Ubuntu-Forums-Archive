---
title: "help! Internet pages don't want to load"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by furoido on 2010-05-17
Upgraded both my system to Lucid and my internet connection. Since then, on Firefox pages often (but not always) refuse to load (Yahoo mail is especially bad), and I have to try again from scratch (clicking the 're-load' tab doesn't help).
Can anybody help? Its driving me up the wall!!!
Thanks!
PS Complete pc ignoramus here, so please give very clear step-by-step instructions!!!

---

### Post by Blutkoete on 2010-05-17
Hello!

What kind of error message does Firefox supply to you (it's a number, like "404") when it doesn't load the page?

---

### Post by dineshs on 2010-05-17
How is it connected ?ethernet?If yes pl check MTU.pl post the result of
```
ifconfig -a
```

---

### Post by furoido on 2010-05-17
andrew@andrew-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1b:b9:f4:c2:dc  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:b9ff:fef4:c2dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:445585 errors:0 dropped:0 overruns:0 frame:0
          TX packets:401110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:471162664 (471.1 MB)  TX bytes:84781454 (84.7 MB)
          Interrupt:30 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)


I don't get any error messages, just a partly-loaded page, or sometimes a white screen...and, as I said, some websites seem to be worse than others....usually, re-trying to re-load the oppage fom scratch (as opposed to clicking the re-load tab)solves the problem, but its just so annoying having to always do that...

---

### Post by vivek40 on 2010-05-17
Well it might be DNS resolution issue .. just check if the sites open using the ip address instead of the url...

---

### Post by prshah on 2010-05-17
> **furoido said:**
> Since then, on Firefox pages often (but not always) refuse to load (Yahoo mail is especially bad), 

Hi, please see this thread ([Firefox/Epiphany/Lynx not loading certain websites]("http://ubuntuforums.org/showthread.php?t=718709")) If you feel the problem is similar to yours, the solution is posted near the end of page 2. Please give it a try and post back.

If you need more help, please post back with details.

---

### Post by furoido on 2010-05-17
prshah, that looks hopeful...but sorry I don't see what the actual solution is!! Sorry, I'm a complete pc noob! be grateful if you could point it out to me!

---

### Post by vivek40 on 2010-05-17
furoido.. before you do anything just check if the site opens with the ip address of a site

---

### Post by furoido on 2010-05-17
how do i found out a site's ip address?

---

### Post by vivek40 on 2010-05-17
just go to the terminal and type  ping -c 3 [www.google.com]("http://www.google.com") Here replace google.com with the site that is not opening for you.. there will be a ip number which will appear there for eg:-208.67.216.230 comes to me for google.. just open the browser and type_ http://_[208.67.216.230]("http://www.208.67.216.230")  and see if the site opens or not and please post back

---

### Post by furoido on 2010-05-17
andrew@andrew-desktop:~$ ping -c 3 [www.yahoo.com](www.yahoo.com)
PING any-fp.wa1.b.yahoo.com (98.137.149.56) 56(84) bytes of data.
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=1 ttl=52 time=127 ms
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=2 ttl=52 time=126 ms
64 bytes from ir1.fp.vip.sp2.yahoo.com (98.137.149.56): icmp_seq=3 ttl=52 time=140 ms

--- any-fp.wa1.b.yahoo.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 126.683/131.612/140.709/6.446 ms


tried [http://98.137.149.56](http://98.137.149.56) and got 'Your requested URL was not found'.
then tried [http://98](http://98). 137. 149. 56 and got a whole list of websites, none of which were Yahoo.

I re-read PRshah's link and the original poster's problem seem to be SO similar to my own....be curious to know how I can change my pmtu from 1500 to 1492, just to see if that helps...

---

### Post by julio_cortez on 2010-05-17
> **furoido said:**
> be curious to know how I can change my pmtu from 1500 to 1492, just to see if that helps...
I think you can change it by running
```
sudo pppoeconf
```
and following the instructions.

I'm not sure if there's a simplier method.. I'm still a kind of noob in this kind of things, so maybe I'm totally wrong :)

---

### Post by mechro on 2010-05-17
> **furoido said:**
> Upgraded both my system to Lucid and my internet connection.

What did you upgrade re your internet connection?

---

### Post by furoido on 2010-05-17
Nothing on the pc beyond moving up to ubuntu 10.04...my ISP installed a new box that apparently provides greater bandwidth/speadier connection...

---

### Post by mechro on 2010-05-17
> **furoido said:**
> my ISP installed a new box that apparently provides greater bandwidth...

The new box may not be configured correctly e.g. the DNS servers may be incorrect and the MTU settings may be wrong. Do you have instructions supplied by your ISP to configure the box or would you rather contact your ISP's support?

---

### Post by furoido on 2010-05-17
Actually, I live in Japan so wouldn't be able to read the instructions anyway, Mechro!! But I will take your advice and hold off doing anything until I have had a chance to chat with my ISP tomorrow about my DNS and  settings! Hopefully, I will not be back!! LOL!!!

---

### Post by furoido on 2010-05-17
Actually, I live in Japan so wouldn't be able to read the instructions anyway, Mechro!! But I will take your advice and hold off doing anything until I have had a chance to chat with my ISP tomorrow about my DNS and  settings! Hopefully, I will not be back!! LOL!!!

---

### Post by furoido on 2010-05-17
Actually, I live in Japan so wouldn't be able to read the instructions anyway, Mechro!! But I will take your advice and hold off doing anything until I have had a chance to chat with my ISP tomorrow about my DNS and  MTU settings! Hopefully, I will not be back!! LOL!!!

oh bollocks, here we go again...now this message doesn't want to load....

---

### Post by mechro on 2010-05-17
Three bollocks! Cool! :D :D

---

### Post by lovinglinux on 2010-05-17
Have you tried to disable ipv6? See the fifth item on [this list](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html).

---

### Post by furoido on 2010-05-17
yes, disabled it, but didn't really seem to help at all

---

### Post by dineshs on 2010-05-18
You can try changing MTU
[http://ubuntuforums.org/showthread.php?t=1376506](http://ubuntuforums.org/showthread.php?t=1376506))
ie
```
sudo ifconfig eth0 mtu 1492
```assuming that you use eth0
And for changing DNS
```
gksudo gedit /etc/resolv.conf
```
edit the file so that it contains only this
```
nameserver 4.2.2.1
```
other open DNS servers are 8.8.8.8   8.8.4.4
(pl back up a copy before editing)

---

