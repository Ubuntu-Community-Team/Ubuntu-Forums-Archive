---
title: "Servers often have timeouts"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by Wild-Storm on 2006-11-19
Hi,
first of all, i searched a lot to solve this problem..but it was not possible for me :(
My configuration:
Ubuntu Edgy with GNOME.
WLAN Card: WG311T (108MBiT)
My internet "System": DSL 6000 (750kb down/~70kb up).
I have 2 routers. It looks like this:
My PC (ip: 192.168.1.2) -> Router 2 (WGT624v3, 108MBiT, no modem, host: 192.168.1.1, ip: 192.168.2.102) -> Router 1 (TSinus 111 DSL, 11MBiT (thats not enough..so I'm using the 2. Router), host: 192.168.2.1, ip: given by provider) -> Internet
The whole system is using MTU 1454.
The DNS-Server on my system: 192.168.2.1. 192.168.1.1 is possible as well, but it's the same problem.
So now the problem: The internet generally works, but very often pages don't work. They just time out, alltough they are still ping-able!
When these pages get a time-out, other pages are working!
E.g.: I want to go to google..doesnt work..but yahoo does!
After a time google works again and [www.rofl.com](www.rofl.com) (example xD) does not work any more! The time varies..
But not only HTTP dosn't work..ftp or smpt/pop3 don't work either!
About 20% of the Pages i want to visit are affected.

I would be very happy, if you could help me to get that thing working...

greets,

wild-storm

---

### Post by Wild-Storm on 2006-11-20
Sorry for pushing..But this problem realy suxx! :(
Has nobody an idea how to solve it?
I hope you can help me

---

### Post by stream303 on 2006-11-21
Wow.  Ping ok but no browsing suggests dns issues.  Can you place your isp's dns servers addresses into your router(s) setup pages?

I'd take a look at your /etc/resolv.conf before and after this change.  Instead of configuring your isp dns addresses in the router(s), you could force the issue - tips in this thread (although I don't use the OpenDNS option mentioned)

[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf)

You may also want to disable IPV6 and see if your routers aren't choking.

This might help:
[http://www.ubuntuforums.org/showthread.php?t=303603](http://www.ubuntuforums.org/showthread.php?t=303603)

---

### Post by Wild-Storm on 2006-11-21
Hi, thanks for your help :)

My resolv.conf:
domain domain.com
nameserver 192.168.2.1

But I don't think, that there are any DNS-Problems, because that would affect the whole internet, not just some websites, or?

IPv6 is in FireFox allready disabled. But I can test to disable IPv6 in the whole system!

---

### Post by Wild-Storm on 2006-11-21
Disabling IPv6 on the whole system worked, but didn't solve the problem :|

---

### Post by stream303 on 2006-11-23
Yep, just your router's address in resolv.conf, not any of your isp's.  Welcome to timeouts. :(  I don't know where you are getting that domain.com line, looks generic.  I'd just leave that blank if  you added that manually.

I just updated some material you might find useful:

[http://www.ubuntuforums.org/showthread.php?t=305275](http://www.ubuntuforums.org/showthread.php?t=305275)

---

### Post by Wild-Storm on 2006-11-23
Well, nothing worked..i have to live with it...whatever...
Thanks anyhow!

---

### Post by Wild-Storm on 2006-11-27
But i've got one Question. Where or how can i change the time, a DNS-Server is used?
Example:
I have 2 DNS-Entries:
127.0.0.1
127.0.0.2

I want, that Server 1 is used for 20 secs and Server 2 for e.g. 10 secs (or 20 secs)

Where can i change that?

---

### Post by Wild-Storm on 2006-12-07
Works now!
How?
I have 2 Routers. Internet -> T-Sinus Data 111 -> Netgear WGT624v3.
My mom had her internet on the T-Sinus Data 111, changed now to the Netgear thing. Works fine!

---

### Post by shimmyshack on 2006-12-07
this sounds like an MTU issue, intermittent internet, timeouts some work some dont etc... using IP doesnt help, yep MTU size.
MTU of ubuntu versus MTU of router, it was solved by changing routers, but you could lower the MTU on your eth card this way:

Fix:

    * go to your routers web interface, note the MTU setting
    * open a terminal
    * type sudo su (and enter your password, you are now root)
    * type ifconfig (is the MTU set in there?)
    * type nano /etc/network/interfaces (settings here work after a reboot)
    * move around until you are underneath your active Network Card
    * if you only have one network card (wired) it will probably be eth0
    * (if your routers MTU was 1492) then add the line MTU 1490 somewhere
    * just make sure Ubuntu has a slightly smaller MTU than your router.
    * press [ctrl]+o [return] [ctrl]+x (to save, confirm and exit from nano)

this is what the settings look like on my computer, (I have set a static IP address, although you might have DHCP there instead)

iface eth0 inet static
address 192.168.0.7
netmask 255.255.255.0
gateway 192.168.0.1
mtu 1490

Now you just need to reboot your network card to notice the change, if you had no internet before or it was very bad, it should then be fine.
in the terminal, type

    * ifdown eth0
    * ifup eth0
    * ifconfig

and now you should see the results, there somewhere will be the MTU setting.

ok, thats it, you have changed the MTU, permanently, or until you change it again ;)

---

