---
title: "ipw3945 delay"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by musasabi on 2006-10-28
my laptop is an hp pavillion dv1650us.

```
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

im using a stock (havent even recompiled the kernel yet) install of 6.10.

the driver is loaded and everything works, sort of. every time a new server is sought (be it browsing, logging on to gaim, ftp, etc), theres a delay of about 10 seconds before anything happens. after the connection has been established, however, everything goes as quickly as it should. this happened under my previous install of gentoo and doesnt occur at all under windows. um...

it might be the AP im tapping into... but due to the nature of my access, im not really at liberty to try a different router or try a wired connection.

so anyway... has anyone ever had this problem? or, more interestingly, what programs might i use to see whats going on locally thats causing the delay?

thanks guys. :)

---

### Post by Taigrr on 2006-10-28
If you configured your network manualy, IE added your own gateways, netmask, etc, you'll want to make sure the DNS ip's are what you want. If you use DHCP, it shouldn't be an issue.

But, in networking, try looking at what yo uhave for DNS addresses. If you don't know what they should be, check what they are on another computer (Maybe a windows box?) 

cmd in "Run", then ipconfig/all. Should find the windows' box DNS servers from there!

---

### Post by Erik Sternerson on 2006-10-28
I have the exact same problem. Fresh install of Ubuntu 6.10. Getting IP from a DHCP server.
My network card is a Broadcom BCM440x. Worked flawlessly under Ubuntu 5.10, 6.10 RCx Live CD and Windows XP.

Haven't checked if I get the correct DNS settings yet, will check that later.

Just wanted you to know you're not the only one.

And if you want to do some serious network debugging my personal recommendation would be Ethereal, but only if you have some knowledge about networking.

I'll keep looking for a solution too.

EDIT: It's a wired network

EDIT2: Browsed around the forums, found a whole bunch of related links:
[http://www.ubuntuforums.org/showthread.php?t=284630](http://www.ubuntuforums.org/showthread.php?t=284630)
[http://www.ubuntuforums.org/showthread.php?t=286183](http://www.ubuntuforums.org/showthread.php?t=286183)
[http://www.ubuntuforums.org/showthread.php?t=286144](http://www.ubuntuforums.org/showthread.php?t=286144)

They seem to be discussing disabling IPv6...

EDIT3: Come to think about it, when 6.10 LiveCD worked, it was in a different network. Maybe it's the combination of Ubuntu 6.10, my DSL modem (XAVI X8222r) and possibly my ISP.

---

### Post by Erik Sternerson on 2006-10-28
I found a temporary solution to my problem. When I get my IP from DHCP, it sets the nameserver in /etc/resolv.conf to the adress of my DSL modem. If I change that to the DNS server of my ISP, everything is back to normal. I fear that I need to do this after every reboot though...

Anyhow, the process would be:
> sudo gedit /etc/resolv.conf

change "nameserver 192.168.1.1" (or equivalent) to
"nameserver 96.15.3.25" (DNS server of ISP, usually found by accessing DSL/cable modem)

---

### Post by musasabi on 2006-11-01
well, now ive got a wired connection, and theres no longer any delay... we'll see what happens when i get a router of my own. :)

thanks guys.

---

### Post by zapcome on 2006-11-01
I have the same problem, same wireless card.. I've already disabled the IPv6 but I still have the problem.

I figured out that possibly the problem is that NetworkManager is setting the default DNS server as my router IP - because Im using DHCP - and my router is redirecting the DNS call to my ISP's servers and that is taking much longer that it is supposed to...  

Now, I want to use a fixed local IP address and set my own dns servers, but I cant do it... Im using NetworkManager and I dont know how to do it. NetworkManager always is using DHCP by default.

I've already create a thread asking for the solution...

this is the thread :

[http://ubuntuforums.org/showthread.php?t=290986](http://ubuntuforums.org/showthread.php?t=290986)

---

### Post by zapcome on 2006-11-02
I fixed my problem using a static IP... I forgot about using NetworkManager since this doesnt support statics IP or DNS configuration...

I set up the fixed IP and my custom DNS servers in System->Administration->Networking and problem fixed.

Now, if you wanna use other kind of authentication different from the WEP... you WILL have to use NetworkManager

---

