---
title: "ethernet connected then died"
date: 2006-12-18
forum: Networking &amp; Wireless
---

### Post by Jocka on 2006-12-18
Well I finally got my own office at this company and had an ethernet cord running to the computer. I had a connection and I could get online. I played around a little bit and downloaded a few things I use.

After restarting, it no longer works. I'm assuming this may be a problem with LAMP as it does the same thing when i'm signed onto windows and use WAMP.

I know I should've downloaded the server edition of Ubuntu, before anyone says that lol. But now it won't let me back on and i'm not sure how to get it to let me :(

It did this after installing apache, php, and mysql. I restarted and dual booted into windows because I needed something from my windows partition and when i botted back into Ubuntu, it no longer worked. Any suggestions?

---

### Post by Jocka on 2006-12-20
I didn't *bump* this because yesterday it my connection was working all day but now it's off again. The only way I can get on is through windows and I'd rather not use windows.

I dont' think it's thw lamp thing like I said because all that was working yesterday just fine. Any ideas? The ip it genereates is ipv6 which as I understand, my router doesn't know or comprehend.

---

### Post by Jocka on 2006-12-20
umm. ... *bump*

---

### Post by Ebiggs on 2006-12-20
Have you tried pinging any sites to see if you are getting out?

---

### Post by Jocka on 2006-12-20
Yes. I attempted all of the "Network Tools". None of them worked.

---

### Post by Iowan on 2006-12-20
Have you tried disabling **ipv6**?
Is it a static or DHCP address?

---

### Post by Jocka on 2006-12-21
dhcp and no, I don't know how to disable it.

---

### Post by mips on 2006-12-21
[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here

---

