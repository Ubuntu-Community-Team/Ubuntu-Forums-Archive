---
title: "Connection Problems"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by illusionz on 2007-05-06
The first time running Feisty live, I could connect to the internet fine. The second time, it just hung on "Configuring IP".

I've tried going into some options and changing things, but it doesn't do anything. 


I'm not a total noob to computers and the such, I just really haven't played around with Linux alot. Any suggestions to fix my problem?

EDIT: I'm using an ethernet card, forgot to mention that.

---

### Post by jazzman on 2007-05-07
I had a similar problem with my wireless card. Try running this in the terminal:

dhclient eth0

I did this once and it solved the problem

Goog Luck!

Jazzman

---

### Post by arlingtonva on 2007-05-07
I'm having network problems as well.  

If I reboot, the client gets a new dhcp lease - no problem.  But, if I suspend the system, when it restores, there is no longer a  connection to the router.  I tried 'dhclient eth0' and 'ifconfig eth0 up'.

I also tried installing network-manager-gnome and then starting nm-applet and no luck, the applet would not start.  Maybe that's another problem.

It must be something easy to fix because I can just reboot and get a new lease fine.

---

### Post by illusionz on 2007-05-07
> **jazzman said:**
> I had a similar problem with my wireless card. Try running this in the terminal:

dhclient eth0

I did this once and it solved the problem

Goog Luck!

Jazzman

That didn't help, I just got some errors.


I mean it used to work the first time, now it no longer works.

---

