---
title: "Wireless network not working on boot up"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by sefs on 2007-04-26
Hi all.  I have a problem that I can't seem to solve.

When my computer boots up the network icon and stauts looks ok but I cant connect to the internet. I can only connect if i clear my /etc/networking/interfaces restart networking.  Then Put back in what was there before and then restart networking again.  Only then does the wireless become available.

Does this sound familiar to anyone?

Thanks.

---

### Post by tjansson on 2007-04-26
To som extend. I was annoyed by network-manager I ended up removing it. I am not sure if the way I did it is the recomended way to do and will not eventually destroy your system - but that aside see my post: [http://ubuntuforums.org/showthread.php?t=423759](http://ubuntuforums.org/showthread.php?t=423759)

---

### Post by sefs on 2007-04-26
Thanks for your reply.  I also wonder if my wireless adapter is going bad.  Does WPA2 depend solely on router and computer/wpa_supplicate or does the wireless dongle has a play in that as well.

---

### Post by sefs on 2007-04-26
What would cause this problem.

When I boot up the network applet looks connected but I cant'd browse networks or internet.  But then if i do a 

sudo /etc/init.d/networking restart

Then everything is good until the next time I reboot.

---

