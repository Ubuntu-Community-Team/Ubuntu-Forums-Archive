---
title: "Ubuntu Wireless &amp; Hotspots [Please Help]"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by cnich23 on 2008-07-11
I have been unable to access the internet with Ubuntu at all.  This has mad it impossible for me to quit using Windows or really use Ubuntu at all.

Scenario:  I am only able to access the internet using a login page, which in Windows Firefox directs to when I open it.  In Ubuntu I can connect to the network, am assigned an IP, but I can not access the login page at all.  I was able to go home on leave for the 4th and use my friends wifi (wpa) without a problem.

I've search extensively through the forums and it seems lots of people are having this problem when it comes to Hotspots.  There has to be a way to fix this.  Please help so I can quit dual booting.

---

### Post by cnich23 on 2008-07-12
I am being assigned all the same information in Ubuntu that I am in windows except windows redirects to the login page.

I am beings assigned the following info.
ip: 192.168.3.76
mask: 255.255.255.255
gate/dns/dhcp: 192.168.3.1

I pinged the login page in windows and get the following address
192.168.4.1

But i cannot ping this address or the gateway address in ubuntu!

Why is this!?
It works with regular wireless but not hotspot logins ...
my primary way to access the internet is through a hotspot

---

### Post by cnich23 on 2008-07-12
I am stumped and have been searching for a while and find that tons of people have this problem but I have found no way to fix it

---

### Post by cnich23 on 2008-07-13
on bended knee

---

### Post by jualin on 2008-07-13
I have two suggestions. The first one try going directly to the address of the login screen (192.168.4.1) and my second suggestion maybe the hotspot doesn't want to run with Ubuntu. Try installing Firefox User Agent Switcher Plugin so you can appear that you are runnning "Windows Vista and Internet Explorer 7" rather than Ubuntu and Firefox. Hope this helps!

---

### Post by jualin on 2008-07-13
or maybe installing IEs4Linux will solved the problem. Some other user suggested that running a virtual machine within Ubuntu connects with no problem. Therefore it's not a problem with wireless drivers or configurations. It should be a problem with the Hotspot not wanting to connect to a Ubuntu computer since it connects through the Virtual Machine. Keep us posted on your progress on this issue.

---

### Post by cnich23 on 2008-07-13
Thanks for the reply!

Unfort ... both do not work.  I cannot ping the login page or gateway for some reason.  I also changed the useragent in firefox but no luck... Im thinking of downloading another distro and trying

---

### Post by jualin on 2008-07-13
try installing Ie4slinux, it's a internet explorer clone for linux

---

### Post by cnich23 on 2008-07-14
I have not tried this option yet, but seems maybe it could work.

I tried downloading all the packages and cabs manually since I dont have a connection and I cant get one. 

But I am having problems with installing ies4linux.

Anyone know where I can find a guide to manual installtion?

I tried downloading the windows cabs manually but it didnt seem to work.  Says that DCOM98.exe does not exist, but it does

---

### Post by cnich23 on 2008-07-22
I was never able to successfully able to get this to work.  I have to continue to use windows.  I am going to try openSuse. Would anyone else recommend another distro that is good to start out on?

---

### Post by sputnikkk on 2008-07-22
Not sure what the issues are exactly on your system.

Ubu UBER-newb here - I searched and tried all sorts of things for days - Wicd solved my issues.

It scans and shows all the wireless access points in the area.

Your issue seems like a DNS nameserver resolution issue.

If your using the network gui that comes with Ubu 8.04

System  | Administration | Network ... thats the NetworkManager GUI Im referring to ... I replaced that app by using wicd

[www.wicd.net](www.wicd.net)

How to get Wicd - [http://www.wicd.net/wiki/doku.php?id=faq](http://www.wicd.net/wiki/doku.php?id=faq)

---

