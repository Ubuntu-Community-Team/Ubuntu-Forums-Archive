---
title: "How do you connect to wireless network in Ubuntu Server?"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by FireFreek on 2009-04-11
With my past experiences with my wireless adapter, I was able to get the driver working with ndiswrapper. I'm just messing with my computer learning about how to work a server. I plan on using the comp for torrentflux-b4rt, so i dual-booted Win2k and Ubuntu server 8.10.

In one sentence my question is: How do you connect to a wireless network through Ubuntu Server 8.10? (router uses MAC address filtering, but i don't think it should be a problem since the adapter is already in the filter. No password)

---

### Post by MrWES on 2009-04-11
> **FireFreek said:**
> With my past experiences with my wireless adapter, I was able to get the driver working with ndiswrapper. I'm just messing with my computer learning about how to work a server. I plan on using the comp for torrentflux-b4rt, so i dual-booted Win2k and Ubuntu server 8.10.

In one sentence my question is: How do you connect to a wireless network through Ubuntu Server 8.10? (router uses MAC address filtering, but i don't think it should be a problem since the adapter is already in the filter. No password)

[http://blog.tplus1.com/index.php/2008/06/13/how-to-connect-to-a-wireless-network-from-the-ubuntu-command-line/]("http://blog.tplus1.com/index.php/2008/06/13/how-to-connect-to-a-wireless-network-from-the-ubuntu-command-line/")

---

### Post by FireFreek on 2009-04-11
Thanks, i'll see if it works.

---

### Post by FireFreek on 2009-04-11
Okay, i did the first three commands that were in the guide, and it didn't work.(on another note, it takes for ever to write this stuff down)

**sudo iwlist wlan0 scan**
wlan0        Interface doesn't support scanning : Network is down

**sudo iwconfig wlan0 essid "Saffinet"**
**sudo dhclient wlan0**
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
wmaster0 : unknown hardware address type 801
wmaster0 : unknown hardware address type 801
Listening on LPF/wlan0/00:0f:b5:70:b5:42
Sending on LPF/wlan0/00:0f:b5:70:b5:42
Sending on Socket/fallback
DHCPREQUEST of 192.168.2.3 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.3 from 192.168.2.1
bound to 192.168.2.3 -- renewal in 39565 sec

So after all that, i tried to apt-get something, and it didn't work.

**sudo apt-get install build-essentials**
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package build-essentials

---

### Post by The Cog on 2009-04-11
It's build-essential (singular not plural). And you wil probably have to do **sudo aptitude update** first, to find out what is in the repositories.

If DHCP is working then your wireless is wroking nicely. Excellent.

---

### Post by FireFreek on 2009-04-12
When I typed "sudo aptitude update" it returned this a few times
(replace XXXXXXX with the update packages, and repeat)

```
Writing extended state information... Done
Err http://us.archive.ubuntu.com intrepid-XXXXXXXX
      Could not connect to us.archive.ubuntu.com:80 (91.189.88.31) - connect (113 No rout to host [IP:91.189.88.31 80]
```

And then it returned this for a bit

```
Ign http://us.archive.ubuntu.com intrepid-XXXXXXXX
```

But then when it got to 20% it started failing again like the first code block, and with the same packages as in these code blocks.

I also tried sudo apt-get update, just to see what would happen, and I took a picture of some of the output.
[http://i40.tinypic.com/i2pvyv.jpg](http://i40.tinypic.com/i2pvyv.jpg)
[http://i39.tinypic.com/2utpz14.jpg](http://i39.tinypic.com/2utpz14.jpg) (sorry this one is sideways)


(sudo apt-get install build-essential doesn't work still)

---

### Post by The Cog on 2009-04-14
No route to host suggests to me that you son't have a working internet connecton so can't connect to the repository servers. In know - chicken and egg - you're trying to fix your wireless. You will have to use a wired connection to download the required software.

If you can't get wired internet working either, you will have to download the packages from here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and transfer them on a USB stick, but be warned that you could spend ages tracking down the dependencies of the packages, and their dependencies, and their dependencies, ad nauseum.

---

