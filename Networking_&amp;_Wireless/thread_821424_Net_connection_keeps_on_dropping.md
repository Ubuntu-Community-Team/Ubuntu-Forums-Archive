---
title: "Net connection keeps on dropping"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by kartiksinghal on 2008-06-07
I installed Ubuntu 8.04 from the official Canonical disk a day before yesterday. Then, I updated the system with all the updates using Update Manager.

The problem I am facing is that after installing the updates my internet connection drops after a minute or two. Then, I have to reconnect using 'pon dsl-provider' and in a few minutes the connection again drops. I have also noticed that my net speed has also dropped during those 2-3 minute intervals. I have an ADSL connection and set it up using the usual 'pppoeconf' procedure.

I faced a similar problem with 'Linux Mint', a derivative of Ubuntu a month ago. The problem comes only after installing the updates.

Please help on this. I searched on the forums but couldn't find anything relevant.

I have freshly installed Ubuntu Hardy Heron (this time from the DVD) today and haven't updated the system yet. I want to see my system fully updated, so I am just holding back to update it.

---

### Post by kartiksinghal on 2008-06-07
Hey, no help from here!!:(

---

### Post by superprash2003 on 2008-06-07
if its a DSL connection it could be due to a bad telephone line.. ensure that all telephones are connected after the splitter

---

### Post by kartiksinghal on 2008-06-07
Its working fine on XP. It worked fine on Fedora. And it works fine before installing updates. I face this problem after installing updates.

I have installed updates on my new installation just today but haven't restarted the system and that's why I am able to use internet on Ubuntu.

If I restart I know I will get into trouble again, please suggest something.

---

### Post by superprash2003 on 2008-06-08
when your connection isnt working.. type ping 192.168.1.1 in your terminal and post output.. are you connecting via usb or lan?

---

### Post by kartiksinghal on 2008-06-08
So, I finally restarted my system. :( (power failure, quite common in my area). And I am in trouble again:sad:

I received the following output just once after several retries:
> kartik@PlatiniumV2:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=6.24 ms
.64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.656 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.641 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.657 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.648 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=0.661 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=0.617 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=0.639 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=0.619 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=0.641 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=64 time=0.631 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=64 time=0.639 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=64 time=0.618 ms

--- 192.168.1.1 ping statistics ---
13 packets transmitted, 13 received, 0% packet loss, time 11999ms
rtt min/avg/max/mdev = 0.617/1.070/6.243/1.493 ms


And this one almost all of the time, before and after I received the previous one:
> kartik@PlatiniumV2:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 192.168.1.1 ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 4999ms

I am using LAN not USB. Hey, didn't I tell you this problem is because of installing updates (maybe becoz of new kernel, well i am not sure). I was happily using my net before updating, after installing updates and restarting I faced the same problem again.
:sad:

---

### Post by kartiksinghal on 2008-06-08
Posted the previous post and this one using XP. See no internet working on linux.

---

### Post by kartiksinghal on 2008-06-08
hey superprash, got something?

---

### Post by kartiksinghal on 2008-06-09
Please help guys, I cannot use my new Ubuntu installation without internet connection. :sad:

---

### Post by superprash2003 on 2008-06-11
try setting your router to ppoe mode instead.Then there is no need of dialing in ubuntu..Which router do you have?

---

### Post by kartiksinghal on 2008-06-11
Actually I have BSNL broadband connection, so an ADSL modem (UT300R2U)

Its already set in PPPOE mode.

---

### Post by superprash2003 on 2008-06-12
i dont think its in ppoe mode mate.. otherwise you wouldnt require to use the pon dsl-provider command .. follow this tutorial [http://prash-babu.blogspot.com/2008/04/how-to-setup-ppoe-mode-automatic.html](http://prash-babu.blogspot.com/2008/04/how-to-setup-ppoe-mode-automatic.html)

---

### Post by kartiksinghal on 2008-06-12
thanks for help, friend.
I will follow the tutorial. And hey you maintain a really nice and useful blog.

---

### Post by kartiksinghal on 2008-06-12
just one question, this automatic dialling doesn't work on xp?

and my router was previously set in PPPOE mode (it said 'Enabled' in the status) but i agree not in automatic dialling mode

---

### Post by kartiksinghal on 2008-06-12
Thanks a lot, buddy! :)

Its working fine now. But I have another question to ask:
The download/upload speeds as shown by netspeed_applet on my upper panel are often downgraded to 0 b/s (which are supposed to be in more than 256 kb/s), is this normal (maybe this applet measures the speed on the fly as some bytes are transferred)?

And it is taking a lot of time to open up a page :(

---

### Post by superprash2003 on 2008-06-12
yes could only during byte transfer..try changing DNS servers to opendns to improve browsing speed [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

Thankyou so much for the feedback on the blog!!Really Appreciate it :D

---

### Post by kartiksinghal on 2008-06-12
Thanks a lot Prashanth

Its working like never before. I am so happy with my Ubuntu now. :)

And my automatic dialling is working fine on XP also (I don't have to connect using bsnl shortcut) :guitar:

---

