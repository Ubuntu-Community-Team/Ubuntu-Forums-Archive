---
title: "Got an IP through DHCP via wireless, but internet not working"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by limefrogyank on 2008-02-12
I've got a problem with my internet.  I've been using the Network manager to connect my wireless card to my router with few problems for the past couple of weeks (occasionally, it will fail to connect and a reboot helps).  

When I removed Firestarter and installed Apache, the connection worked fine, too.  I even got apache set up and working correctly.  However, after I rebooted the computer, I get no internet anymore.

Specifically, I can still use the network manager to connect to my router (no security, completely open).  Ifconfig and iwconfig both confirm that I'm connected to my router and that I'm receiving an IP address via DHCP.  However, I can't connect to any websites via firefox, I can't connect to my router, and I can't even ping my router.

The router is working as I'm on it using my windows laptop.  Any ideas??

---

### Post by KCPokes on 2008-02-12
You are receiving an IP address from your router, which is positive.  What is the IP address you are receiving?  Is it within the range of IPs that your router would assign?  Just need to validate as a lot of times you tend to get an ip address but it'll be within the 169.XXX.XXX.XXX range, which is not valid.

---

### Post by limefrogyank on 2008-02-12
Yes, I have it set to assign my MAC address a preferred IP address of 192.168.1.24... and I'm seeing it under ifconfig.


FYI, while I can follow directions and get something like apache to work, i'm still a noob when it comes to using netstat, route, iptables, and arp (whatever that is).  I've looked at the route's output and it seems normal compared to what other people post on these forums.  I have no idea what to do about the rest of it.

---

### Post by PurposeOfReason on 2008-02-12
I've had that trouble before and disabling ipv6 worked.

---

### Post by limefrogyank on 2008-02-12
Will try disabling ipv6... is this the best way to do it?
Link: [http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

---

### Post by PurposeOfReason on 2008-02-12
For Ubuntu I always did this.
[http://ubuntuforums.org/showthread.php?t=202838](http://ubuntuforums.org/showthread.php?t=202838)

But after reading, your way is better.

---

### Post by limefrogyank on 2008-02-12
Well, i edited the line in /etc/modprobe.d/aliases to say 

alias net-pf-10 off

but that didn't help any.  I'm still getting the same symptoms.  Funny thing is:  when I first try to connect after a reboot (selecting my router with the network manager), ubuntu tries to connect for a minute (the swirly thing goes with one green light) and then stops.  Ifconfig does NOT show my IP address, but when I log onto the router, I can see my computer as an attached device with the correct IP address.

When I click on my router for the 2nd time using network manager, then it works (shows the 4 bars).  Ifconfig then shows the correct IP address.  However, I still can't ping the computer from my laptop I can't ping the router from my computer.  No internet :(

---

### Post by limefrogyank on 2008-02-12
Well after some more investigating, when I leave it alone for a few minutes, ifconfig will STILL show the correct IP address, iwconfig will still show me associated with the router, but my router does NOT see me as an attached device.  

???

---

### Post by PurposeOfReason on 2008-02-12
Grab a terminal and type

ping -c 3 [www.google.com](www.google.com)

If you're able to ping a site, then we'll know if something deeper is up.

---

### Post by limefrogyank on 2008-02-12
I get "unknown host".

Pinging my router (192.168.1.1) gives me "sendmsg: operation not permitted"

---

### Post by PurposeOfReason on 2008-02-12
I think the end of this thread may help.
[http://www.linuxquestions.org/questions/linux-networking-3/ping-sendmsg-operation-not-permitted-307848/](http://www.linuxquestions.org/questions/linux-networking-3/ping-sendmsg-operation-not-permitted-307848/)

---

### Post by limefrogyank on 2008-02-12
Thanks for your help so far.

In any case, I don't have any DENY setting in my iptables. I don't think I have shorewall installed because I don't have a folder for it in my /etc folder.  However, I don't know how to check if it's running.  I don't have the "service" command and I can't install it (easily).

Do any other firewalls get installed with apache?

---

### Post by limefrogyank on 2008-02-12
well i just flushed the input and output portions of my iptables.  Hopefully, I'm not breaking anything further.

---

### Post by limefrogyank on 2008-02-13
still nothing.  I connect to my router and "route -n" suddenly sets everything up correctly (as far as I can tell).  But I still get no internet access.

actually, there's a line in the route -n output that bothers me.  The first one starts with 192.168.1.0 and is tied to wlan0 which seems fine.  The second line starts with 169.254.0.0 and it is also tied to the wlan0 adapter.  (The third line for the gateway is correct)

Is the 2nd line a problem?

---

### Post by Rogers on 2008-02-15
I'm having this issue in Ubuntu 7.10 desktop.  I have an Ubuntu 7.10 server doing routing and DHCPD and the 7.10 desktop won't get a gateway from the router and when I go to manually add it I get **SIOCADDRT No such process** errors.

I can't even manually add the route.

---

### Post by Rogers on 2008-02-15
Changing the DHCP server in /etc/dhcpd.conf

**option broadcast-address 192.168.0.1;**

to

**option broadcast-address 192.168.0.255;**

Fixed my problem!!!!!!!!!!!! HURRAY!

---

