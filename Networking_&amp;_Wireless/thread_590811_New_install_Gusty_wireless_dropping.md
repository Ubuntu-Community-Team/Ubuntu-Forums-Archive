---
title: "New install Gusty wireless dropping"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by comfortablynumb on 2007-10-25
I just did a clean install of Gusty to my laptop (IBM T23) wireless seems flaky at best right now. I have a Cisco Aironet 340 802.11B card, I've tried to create an existing connection and manual connection. Manual connection will not connect at all, if I connect to existing and input my ssid and hexadecimal code it will connect and drop, I've done that several times. Also when I reboot it doesn't keep the settings :mad:

Right now it's been up for about 15 minutes with out dropping (knock on wood) I'm not sure what else to do at this point

I've used this same laptop and card for several years on this same network using Windows.

Network:
Netgear 814 (802.11 B) 
**Broadcast SSID is disabled**
Wireless PCMCIA Cisco Aironet

---

### Post by fearevilleet on 2007-10-25
Hi,

A lot of us our having simular issues. [Check out this thread]("http://ubuntuforums.org/showthread.php?t=581055"). A bug report has been opened, but wireless still sucks :{.

---

### Post by comfortablynumb on 2007-10-25
Thanks for the reply, I've had the network up all day with no drops, but as soon as I reboot the connection is gone and I need to re-add all my settings. Really sucks, I didn't have this problem this problem with Feisty Fawn when I had it on here.

---

### Post by fearevilleet on 2007-10-25
Usually when my connection drops, I can restart networking to fix the issue without rebooting

```
/etc/init.d/networking restart

```

Currently wireless in gusty sucks, I really miss edgy and think I might down grade this weekend. I need wireless to work well; more then I need cool looking windows.

---

### Post by comfortablynumb on 2007-10-25
> **fearevilleet said:**
> Usually when my connection drops, I can restart networking to fix the issue without rebooting

```
/etc/init.d/networking restart

```

Currently wireless in gusty sucks, I really miss edgy and think I might down grade this weekend. I need wireless to work well; more then I need cool looking windows.

Heh, I can't even get cool looking windows with this laptop lol, running old S3 graphics.

Thanks for the code, my whole problem is settings them self they dissapear on any kind of restart it won't keep the settings.

I thought about maybe installing WCID and uninstall network manager but I didn't see anything for Gusty yet, looks like just Feisty.

I created a seperate /home with this install so maybe I can reinstall an older version. Except for 2 random lockups and this stupid wireless situation Gusty is running pretty good on this laptop.

---

