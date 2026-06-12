---
title: "A patch broke bluetooth....need help"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by TalioGladius on 2009-09-14
I use Logitech MX5500 BT keyboard and mouse and I installed the latest round of patches this morning which included a bluetooth update.


After reboot, the keyboard stopped responding.  Strangely the mouse is still working.  Blueman said the bluez daemon wasn't running.  I uninstalled and reinstalled everything bluetooth in synaptec.

I finally figured out that the bluetooth service won't start.

> sudo /etc/init.d/bluetooth status
 * bluetooth is not running 
 ~ $ sudo /etc/init.d/bluetooth start
 * Starting bluetooth                                                                                            [ OK ] 
 ~ $ sudo /etc/init.d/bluetooth status
 * bluetooth is not running



Any ideas?  It's critical that I have this thing working.  I don't want anyone getting ideas that I'm unproductive due to fixing things because of having ubuntu on a work system.

---

### Post by TalioGladius on 2009-09-14
help?

---

### Post by ashwinhgtx on 2009-09-14
Try uninstalling blueman and everything related to bluetooth. Also purge the configuration files.
Then try reinstalling the default bluetooth applet that comes with Ubuntu.

I'm not sure if it will work but you could give it a shot.

---

### Post by TalioGladius on 2009-09-14
> **ashwinhgtx said:**
> Try uninstalling blueman and everything related to bluetooth. Also purge the configuration files.
Then try reinstalling the default bluetooth applet that comes with Ubuntu.

I'm not sure if it will work but you could give it a shot.Thanks for the response, but I've already done that...twice.

That's what I get for installing updates.  :oops:

---

### Post by ashwinhgtx on 2009-09-14
What all bluetooth related packages do you have installed right now?

---

### Post by TalioGladius on 2009-09-14
> **ashwinhgtx said:**
> What all bluetooth related packages do you have installed right now?A search for blue in synaptic told me these:


bluez
bluetooth
bluez-cups
libbluetooth3
bluez-alsa
bluez-gstreamer
bluez-gnome
bluez-utils
gnome-bluetooth

---

### Post by ashwinhgtx on 2009-09-14
> **TalioGladius said:**
> A search for blue in synaptic told me these:


bluez
bluetooth
bluez-cups
libbluetooth3
bluez-alsa
bluez-gstreamer
bluez-gnome
bluez-utils
gnome-bluetooth

Isn't there a force option in Synaptic to install a previous version of any software? It's also possible using apt. Have you tried reverting back to the previous version of the bluez package?

---

### Post by TalioGladius on 2009-09-14
> **ashwinhgtx said:**
> Isn't there a force option in Synaptic to install a previous version of any software? It's also possible using apt. Have you tried reverting back to the previous version of the bluez package?whew.....fixed it

You got me looking in the right direction.  In trying to get the earlier version installed, synaptec and apt-get were failing on removing bluez.  As a guess I just moved /etc/init.d/bluetooth to bluetooth-old and then it let me uninstall it.

Just had to install the older version and everything is connected.

What a relief.  Thanks for all your help.

---

