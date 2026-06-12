---
title: "Different WIfi Applet?"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by msch on 2007-12-30
Hello All-

I finally switched from debian sid to Ubuntu 7.10 on my Dell d820 and man that install was slick.  Everything just works and after a little tweaking I've got the laptop I've wanted for 8+ months.  Suspend, easy wifi, etc...

One thing though, the wifi applet that was active after the default install showed me a signal strength and a right click on it showed the other available ssid's.  It disappeared after a suspend, and I can't seem to get it back.  I added Network Manager applet but it is very different, not nearly as helpful as what I had to start with.  I'm fairly new to Gnome, so it could be something insanely easy, but I haven't been able to find anything searching around.

Thanks for any tips!

---

### Post by Whiffle on 2007-12-31
Try hitting Alt+F2 and then running

nm-applet

---

### Post by msch on 2007-12-31
Nothing happens at all when I do that.  It is the same whether or not the current applet is in the panel.

ps shows me that the nm-applet is running, but it doesn't show up anywhere.

---

### Post by msch on 2007-12-31
Though that did lead me to figuring out the new applet is gnome-netstatus-applet.  Now to find out what happened to nm-applet...

---

### Post by msch on 2008-01-02
Ok, I finally figured this out.  The notification area applet needed to be loaded.  This includes battery, nm-applet information, and pidgin information for me.

---

