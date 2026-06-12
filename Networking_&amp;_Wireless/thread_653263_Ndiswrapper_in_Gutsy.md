---
title: "Ndiswrapper in Gutsy"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by darthchaosofrspw on 2007-12-29
I have no problem getting ndiswrapper installed and configured and getting my wireless to work (using the instructions made for Dapper/Edgy/Feisty). I should point out I have the Broadcom 4306 chipset.

Anyway, when I reboot, the wireless isn't enabled, but if I go into a console and sudo modprobe ndiswrapper, it works.

My question is this : How do I fix this?

---

### Post by Blutack on 2007-12-29
You need to add ndiswrapper to the /etc/modules file.

---

### Post by darthchaosofrspw on 2007-12-29
> **Blutack said:**
> You need to add ndiswrapper to the /etc/modules file.

Thanks. It works like a charm now.

---

### Post by drgatsby on 2007-12-29
I am having a similar problem with my D-Link wireless card.  I am able to get it to work using ndiswrapper and installing the driver.  Like the previous user I need to enter sudo modprobe ndiswrapper followed by iwconfig into the terminal every time I restart to activate the wireless connection.

To solve this problem I entered this into the terminal:

echo ndiswrapper | sudo tee -a /etc/modules

upon restart my computer crashes and fails to boot.  It gets stuck at the same point every time.  I am able to use ctrl-alt-F1 to get to a command prompt but I am not able to use the gedit command to remove ndiswrapper from the /etc/modules file.  I have tried everything I know how to do to get it to boot.  Is anyone able to help.

I'm a total newbie so be gentle.  It's an old desktop that I wanted to learn to use linux on.  I'm running gutsy and it is a current version of ndiswrapper.  The wireless card is a D-Link DWL-G510.  It is running using the Win98 driver mrv8k51.inf.

Thanks

---

### Post by ascendant on 2007-12-29
> **drgatsby said:**
> I am able to use ctrl-alt-F1 to get to a command prompt but I am not able to use the gedit command to remove ndiswrapper from the /etc/modules file.
ThanksSince you are in the command line, x-windows applications won't work.  Try using a command-line text editor like nano.

e.g.```
sudo nano /etc/modules
```
nano will load the file for editing.  Instructions on how to use it are at the bottom of the screen, or use man nano for the manual page.

---

### Post by drgatsby on 2007-12-29
Thanks ascendant nano worked great.  Any ideas about how to get ndiswrapper to load at startup without crashing my system.

---

