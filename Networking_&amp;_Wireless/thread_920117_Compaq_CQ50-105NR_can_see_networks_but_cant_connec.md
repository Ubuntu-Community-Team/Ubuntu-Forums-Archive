---
title: "Compaq CQ50-105NR can see networks but cant connect"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by cus4fun on 2008-09-14
I've just installed a duel boot on the laptop with Vista. Installation went fine. Graphics were minimal and wireless was not working at all.

Searching the forums I decided to tackle graphics first and finally with success using the method [http://ubuntuforums.org/showthread.php?t=880787](http://ubuntuforums.org/showthread.php?t=880787) the "Tricky Tricky" version.

I used madwifi 0.10.5.6 driver and somehow got the wireless working. The first couple attempts I could see networks but couldn't make the connection. Then suddenly I look up and I'm online on my network. Mine is a WPA network and I had entered the password.

So after a reboot, my touchpad starts acting funny. I edit the xorg.conf to fix that and suddenly my graphics are back to nil. So all day I'm figuring out what silly thing I missed with the mouse, then I get the graphics back up, and now I can not get the wireless back up.

I have the Atheros 5007 card. Right now I can see mine and several other wireless networks. I cant connect to encrypted or non-encrypted networks with the Compaq, however I can connect to any number of them with my other laptop.

Another by the way, this is the 4th or 5th laptop I've installed Ubuntu on, I'm still very new, but I'm aware of the wireless issues and this is the first one that's really stumped me.

Thanks in advance.
Chris

---

### Post by cus4fun on 2008-09-14
Ok, just uninstalled everything madwifi and compiled and installed it again and poof, I have wifi.

Does Ubuntu run on gremlins and smoke? Or does it just install on them?

If anyone has thoughts, I'd love to hear them.

Now to figure out the crappy sound problem and how to make this little turn-off-the-touchpad-while-I'm-typing button. I looked it up, that's really what it's called.

---

