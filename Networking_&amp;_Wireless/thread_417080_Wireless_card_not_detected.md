---
title: "Wireless card not detected"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by jrlander on 2007-04-21
Hi,
I just upgraded to Feisty today, and now when i go to System->Administration->Network, my wireless network does not show up.  I'm using a generic wireless card, I'm not sure of the brand because I've never had problems using it before.  I was using Dapper before and the network connection had no problems, after the upgrade to Edgy everything was still working fine, but once I updated to Feisty, no network connection.

I'm fairly new to the linux world, so I don't know a lot about how to troubleshoot issues like this.  Also, I don't have a hard wired connection on my PC (it's a desktop upstairs and my router is downstairs).  So a solution that doesn't require downloading directly from that computer would be a great help.

When I run iwconfig, I get the following

lo            no wireless extensions.
eth0       no wireless extensions.

Any help would be great.  Thank you,

Jason

---

### Post by smartboyathome on 2007-04-21
Would you tell me what you see in the "Restricted Drivers List"? (system/administration/restricted drivers list)

---

### Post by jrlander on 2007-04-21
Restricted drivers list contains the follow:

Lucent/Agere linmodem controller driver
NVIDIA accelerated graphics driver

---

### Post by smartboyathome on 2007-04-21
ok, so it IS supported. Is there a way to turn it on outside of your computer (button, switch, ect)?

---

### Post by jrlander on 2007-04-21
Nope.  It is always on (it's a PCI card).

---

### Post by smartboyathome on 2007-04-21
Ok. I think that it is plain undetected then.

---

### Post by jrlander on 2007-04-21
Any thoughts on what I can do from here?  Why would it be detected in the other versions but not this one?

Is there a way to do a downgrade to Edgy without have to format and do a clean install (I'm assuming no)?

---

### Post by smartboyathome on 2007-04-21
I don't know. I know I have a similar problem (but it is detected in Restricted Drivers Manager). I think that you may want to try to get the CD, and follow the upgrade instructions to downgrade your system.

---

### Post by jrlander on 2007-04-21
Well thanks for the help.  I'll either give that a try, or get a new wireless card (mine is an old 'b' card, I've been thinking about upgrading anyway, so I guess now might be a good time).

---

### Post by jrlander on 2007-04-21
OK, I figured it out (well, it works anyway, but probably isn't the best solution).  After a little investigation, I discovered my wireless card was a Realtek RTL8180L.  Apparently the driver for this card has been blacklisted in Feisty.  The blacklist file lists the following reason: "# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)".

I modified /etc/modprobe.d/blacklist and commented out the following line:

blacklist r818x

There is also a ESSID workaround that needs to be completed too.

I found the information on the following post:

[http://ubuntuforums.org/showthread.php?t=407853&page=2]("http://ubuntuforums.org/showthread.php?t=407853&page=2")

I realize that it is probably not a good idea to use a blacklisted driver, but it is working now until I get around to upgrading.

---

