---
title: "ntpdate reply [what is offset ?]"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by shuaibe on 2007-07-24
Hello,

when I run:

# ntpdate 192.168.12.100

I usually get a reply like:

**10 Jul 11:45:48 ntpdate[10059]: adjust time server 192.168.12.100 offset 0.057667 sec**

In this reply, does the offset = 0.057667 mean that ntp client time is 0.057667 sec ahead of the ntp server (in this case 192.168.12.100) ? or vice versa ?

or Does it mean that that time difference between two PCs was 0.057667 and has been taken care of ?

I couldnt figure that out from man page.

Thank you for your time!

---

### Post by chili555 on 2007-07-24
> time difference between two PCs was 0.057667 and has been taken care ofThis is the meaning of offset. ntpdate assumes the server, whether it's a homebuilt server in your closet, or ntp.ubuntu.com or the atomic clock attached to a government maintained server, is always right. Thus, your local client is adjusted to the ntp server.

---

### Post by shuaibe on 2007-07-24
so that means that they had a time difference of "offset" as indicated in reply and now are in sync ... correct ? how much precision does ntp give us ? are they in sync upto micro second precision ?

thanks again!!

---

### Post by chili555 on 2007-07-24
> they had a time difference of "offset" as indicated in reply and now are in sync ... correct ?Correct.> how much precision does ntp give us ? are they in sync upto micro second precision ?Well, you saw an adjustment of *less than* 6/100ths of a second. That's very precise.

As much as we may not want to accept it, computers are imperfect, if only to a slight degree. That's why you can syncronize perfectly today and have a slight, a few thousandths, offset tomorrow.

Also, it takes a finite amount of time for the signal to get from server to server across the internet. It may be fast, but it's not instantaneous.

For the purposes most of us use, it's constructively perfect. I'd assume if you are involved in scientific operations requiring precision of .00000000001 second, you are not asking on Ubuntu forum! If, like me, you are trying to invent time travel in order to manipulate the stock markets, you may be here.

---

### Post by shuaibe on 2007-07-24
Iam a little confused, when i run ntpdate from the client, for first time i get :

10 Jul 11:45:57 ntpdate[10143]: adjust time server 192.168.12.100 offset 0.054205 sec

they were at a offset of 0.054205 sec but now are in sync but when i run it a 2nd time it gives

10 Jul 11:45:58 ntpdate[10144]: adjust time server 192.168.12.100 offset 0.054136 sec

There is only difference of a second in running the two ntpdate calls ... and 2nd time it shows an offset of 0.054136 secs ... this means they were not in sync after the 1st call ... am i interpreting the information wrongly ? I want to understand this offset thing :) ....
thank you for ur patience and help!

---

### Post by chili555 on 2007-07-24
I believe this means that using the ntp server you are using, and more importantly, the server 192.168.12.100 is using, and given the type of connection you are using, dial-up, DSL, cable, T1, fiber or satellite, that 6/100ths of a second is as good as you can get.

Here, for your amusement, is my own result:```
chili@LAPTOP60:~$ sudo ntpdate ntp.ubuntu.com
24 Jul 09:35:43 ntpdate[8790]: adjust time server 82.211.81.145 offset -0.000765 sec
```My connection is DSL to a wireless 54Mb/s router then wirelessly to my laptop.

---

