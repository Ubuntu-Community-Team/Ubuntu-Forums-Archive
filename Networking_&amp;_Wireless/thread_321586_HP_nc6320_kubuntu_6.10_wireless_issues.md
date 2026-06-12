---
title: "HP nc6320 kubuntu 6.10 wireless issues"
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by devilears on 2006-12-19
I have kubuntu 6.10 installed on a brand new HP nc6320 which I use at the office as well as at home. At the office I have a fixed IP address and connect to the office network via LAN cable. At home I have a wireless accesspoint through which i want to connect to the internet. Problem is, it just does not work properly. I would like to leave the office and switch on the laptop at home and it should automatically log onto my wireless accesspoint, but I always have to "fiddle" to get it to log on. I restart the networking, do ifdown  & ifup, reboot, set my fixed IP to dhcp etc etc in order to EVENTUALLY get onto my home network. This is extremely irritation for me. Does anyone else have similar problems?

---

### Post by disabled_20220313 on 2006-12-19
I've not had this problem, but I think its a problem with linux in general that it cannot switch between wireless networks using pre-configured information.

But.

I think this may help, [iwconfig guide]("http://www.gentoo.org/doc/en/handbook/handbook-ppc.xml?part=4&chap=4#doc_chap3"). Its for Gentoo but it looks like it could help you.

I'm also pretty sure there are projects out there that are trying to remedy this problem with a more user friendly GUI interface. Though at the moment the name escapes me.

Good luck

---

### Post by axel112 on 2007-02-05
> **devilears said:**
> I have kubuntu 6.10 installed on a brand new HP nc6320 which I use at the office as well as at home. At the office I have a fixed IP address and connect to the office network via LAN cable. At home I have a wireless accesspoint through which i want to connect to the internet. Problem is, it just does not work properly. I would like to leave the office and switch on the laptop at home and it should automatically log onto my wireless accesspoint, but I always have to "fiddle" to get it to log on. I restart the networking, do ifdown  & ifup, reboot, set my fixed IP to dhcp etc etc in order to EVENTUALLY get onto my home network. This is extremely irritation for me. Does anyone else have similar problems?

I don't have any problems, with my nc6320, switching from work, wired connection, to home wireless. It works great. My wireless router is configured:
*open
*shared key 128
*macadress controll

Are you sure that the problem isn't the router?

/axel

---

