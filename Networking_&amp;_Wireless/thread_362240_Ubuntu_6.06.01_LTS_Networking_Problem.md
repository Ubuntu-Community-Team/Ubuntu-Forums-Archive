---
title: "Ubuntu 6.06.01 LTS Networking Problem"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by jmatthews82 on 2007-02-15
Hi,
  I am fairly new to the Ubuntu world.  I am attempting to run the Live CD of Ubuntu 6.06.01 LTS on my pc.  I currently have a DSL internet provider that requires PPPOE.  Here is my setup: My pc is hooked via CAT5 cable to my wired Linksys router (Model: BEFSR41), my Linksys router is hooked up to my DSL modem (Westel Wirespeed 2100), my modem is connected to the phone line for my connection.  

When I run the PPPOE setup I can see the IP address that my computer is trying to use.  It is a valid IP issued from my router; however, I can't connect to the internet.  If I reboot into Windows XP I can connect with the same setup and same IP address.  Does anybody have any ideas?  I have followed the PPPOE Article from this site with no luck.  Any help would be appreciated!  Thanks!

---

### Post by louis_nichols on 2007-02-15
Can you give us some details? Like, what didyou try to do on the web? Browsing, messaging? And what was the exact error you got?

---

### Post by chili555 on 2007-02-15
I don't think you have to set up PPOE on your Ubuntu computer, I think it's all set up for you in your router. The evidence is your XP machine works fine.

The router should hand you a 192.168.x.x address via DHCP. You have an ordinary ethernet connection between your Ubuntu machine and the router.

I would go into System -> Administration -> Networking and highlight your wired connection, probably eth0, check Enable, set it to DHCP and you should be all set.

Post back if you need more help.

---

### Post by jmatthews82 on 2007-02-15
Chilli,
   I'll give that a try.  Thanks!  I'll post what happens.

---

### Post by jmatthews82 on 2007-02-16
Chilli,
  I worked, all I needed to do was switch on DHCP.  I guess sometimes the easiest fix are the easiest ones to look over.   Thanks for the help!

---

