---
title: "Problem accessing majority of internet sites"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by andyros on 2008-04-13
**SOLVED :]**

Hi

I have installed Ubuntu 7.10 onto a portable usb hard drive and have a wired connection to the internet using the pre-installed Firefox browser.

I can access google OK, but the majority of other sites simply time out and I am greeted with a **Connection reset by peer** message.

I've seen a few other forum posts regarding this issue which refer to removing IST from the the useragent.firefoxcomment in the firefox config. This is not applicible in this case as that property does not exist in my version of firefox (2.0.0.6).

Has anyone else had a similar problem, its strange that I can access google :confused:

Thanks

---

### Post by jgt157 on 2008-04-13
I have a similar issue.  I can access the Internet, download files, stream video.  Then all of a sudden performance will degrade, files will stop downloading in midstream and videos stop in midstream and finally I won't be able to access the Internet any longer.  I can access the other computers on the network.  I can access my router and dsl modem, but no Internet.  I reset the dsl modem and all works fine for a short period of time and the problem starts all over again. I'm dual booting vista/kubuntu on my laptop and vista doesn't have this problem.  ??? Weird.

---

### Post by Trollslayer on 2008-04-13
Do you have a router?
If something is accessing lots of hosts in the background (P2P applicaitons are a good example or maybe software updates?) it can overload the MAC address tables in the router.

---

### Post by superprash2003 on 2008-04-13
try changing your DNS servers to opendns. [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by andyros on 2008-04-14
Seems to be sorted - ran in rescue mode from the install cd and let it reconfigure DHCP automatically and it seems to be working now strange :confused:

thanks guys

---

