---
title: "ndiswrapper seemed to install but no internet?"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by K.Morgan on 2008-05-27
Hi, when i installed Ubuntu 8.04 it recognized my WG111v2 wireless card and set it up for me, but i started playing around with the settings as i wasn't getting great download speeds and now I've lost all my settings and Ubuntu doesn't even recognize that there's a wireless adapter attached to the computer.

I then decided to go the Ndiswrapper route.  I seemed to have done everything right as the blue light is now flashing on my wireless adapter which it never did before and in System - Administrator - Network it sees that there's a wireless signal and gives me the signal strength.  I've set up the correct encryption but can't connect to the internet.  Gnome network manager and Wicd can't find the wireless adapter at all.  I can't even connect to the router eventhough in Network it seems to recognize that my wireless adapter is there.

any ideas?

---

### Post by K.Morgan on 2008-05-28
Is there a way maybe to just forget Ndiswrapper and do whatever the Ubuntu installation did when finding and installing my wireless adapter again?  reverting back to the settings i had without having to re-install Ubuntu.

Kristian

---

### Post by nicedude on 2008-05-28
I did some research on this for you and while I don't have this model wifi nor do I use Ndiswrapper to manage my wifi drivers I can help inform you on what is going on. The XP driver for your wifi apparently has not worked for people when using Linux but they report the Windows 98 version does work here is a download link for that driver

[ftp://downloads.netgear.com/files/wg111v2_1_3_0.zip](ftp://downloads.netgear.com/files/wg111v2_1_3_0.zip)

extract that and use the .inf file in the win98 directory with Ndiswrapper.

You will most likely need to figure out how to uninstall the drivers you have already used with Ndis so as I have never used it I have no idea how to do that ( it may be in the ndiswrapper program itself I just have no idea ) But here is a link to a thread ( but its older and ndis may have changed since then ) that someone in post #3 tells about this, so it might give some help to you.

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/netgear-wg111v2-ndiswrapper-installation-problems-460124/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/netgear-wg111v2-ndiswrapper-installation-problems-460124/)

Heres one final link on how to use Ndis with WPA
[http://ubuntuforums.org/showthread.php?t=31418](http://ubuntuforums.org/showthread.php?t=31418)

Although I would strongly suggest you turn your encryption off at first until you can successfully connect to the router in this way, since that will rule out non driver related setup problems from your equation. Once you can connect and say bring google page up with no encryption then just begin trying to enable your encryption at that point.

Hope this helps you get a grip on your problem.

nicedude

---

### Post by K.Morgan on 2008-05-28
Thanks for the reply, i was already using the win98 driver and it appears that removing the encryption from my router now allows me to connect to the internet.  Can't seem to get it to work with WPA encryption at all, and for some reason can't get a signal strength above 30%

Kristian

---

### Post by kevdog on 2008-05-28
The lack of WPA might actually be due to the driver itself.  WPA authentication is handled through the wpasupplicant package.  You could try to perform a manual connection without network manager to see if you are getting any errors that might confirm that wpa is not supported with the win98 driver.

---

