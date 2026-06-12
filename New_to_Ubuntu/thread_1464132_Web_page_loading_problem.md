---
title: "Web page loading problem"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by furoido on 2010-04-27
Hi guys,
Yesterday I upgraded my internet connection package and have have loads of problems since loading web pages. They seem to take ages to load, and sometimes I have to go back and re-try before they're successfully upload. In particular, I am having real problems with my Yahoo mail and cannot seem to send messages...the 'send' tab just fades out and nothing happens...
Any suggestions on what I should check?

---

### Post by compiz addict on 2010-04-27
I used to have the same problem, well almost. What version of Ubuntu are you using? If you're not using 9.10, upgrading may solve the problem.

---

### Post by cuberts on 2010-04-27
> **furoido said:**
> Hi guys,
Yesterday I upgraded my internet connection package and have have loads of problems since loading web pages. They seem to take ages to load, and sometimes I have to go back and re-try before they're successfully upload. In particular, I am having real problems with my Yahoo mail and cannot seem to send messages...the 'send' tab just fades out and nothing happens...
Any suggestions on what I should check?
I had the same problem on Windows, but then it went away somehow. I really do not know how it did that. But for your problem I think that you should check out [this]("http://ubuntuforums.org/showthread.php?t=972100") thread

---

### Post by warfacegod on 2010-04-27
This Thread may also prove useful: [http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

Keep in mind though that it is entirely possible your ISP simply fragged the upgrade process. If what you try here doesn't work out, I'd give them a call.

---

### Post by _0R10N on 2010-04-27
I've read in another thread that it might be something related with IPv6. The solution proposed was to disabling it. I can't remember how to accomplish this. When I find that thread, I'll edit this.

Kind regards!

_0R10N >>

---

### Post by 2hot6ft2 on 2010-04-27
> **_0R10N said:**
> I've read in another thread that it might be something related with IPv6. The solution proposed was to disabling it. I can't remember how to accomplish this. When I find that thread, I'll edit this.

Kind regards!

_0R10N >>
Don't bother it's not worth the trouble. warfacegod gave you a good link.
Here's another.

Speed up Firefox by moving cache into RAM
[http://www.ultimateeditionoz.com/forum/viewtopic.php?f=23&t=216](http://www.ultimateeditionoz.com/forum/viewtopic.php?f=23&t=216)

What do you get from
```
ifconfig
```
In a terminal
Applications > Accessories > Terminal

---

### Post by furoido on 2010-04-28
eth0      Link encap:Ethernet  HWaddr 00:1b:b9:f4:c2:dc  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:b9ff:fef4:c2dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26624 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28292701 (28.2 MB)  TX bytes:6004620 (6.0 MB)
          Interrupt:217 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15516 (15.5 KB)  TX bytes:15516 (15.5 KB)

---

