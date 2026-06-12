---
title: "Just did an update..."
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by n8dude on 2008-10-15
I just did an update for ubuntu 8.10, and now when I run
sudo ifconfig wlan0 up
I get this error message:
SIOCSIFFFLAGS: No such file or directory

Anybody know the solution/cause?

---

### Post by adaptr on 2008-10-15
Did the update include a new kernel image ?

If so, you did not update the proprietary driver modules (linux-restricted-modules) that your Wifi card needs.

---

### Post by n8dude on 2008-10-15
Yeah it was a new kernel image, i'll try that now.

---

### Post by n8dude on 2008-10-15
Yep, the linux-restricted-modules didn't automatically upgrade, had to run sudo apt-get get dist-upgrade to get them to install. Thanks for your help.

---

### Post by AFMac on 2008-10-15
All-

I've got a similar issue.  Just updated my own Hardy system, and after rebooting discovered that I'd lost my wireless.  Was able to get it back with a modprobe ath_pci, but seems that I've got to do this every time I reboot.  I'm still an extremely new Linux convert, and I have no idea what file(s) I might need to modify to ensure that this module is loaded automatically on every startup.  Can someone give a hand?

Thanks,

mac

---

### Post by n8dude on 2008-10-15
I have a similiar issue, after every reboot I have to do:
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
and then I have to switch the wireless off and back on to get it to work.

---

