---
title: "Wireless intialization problem"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by Zef_ on 2007-08-31
Hiya guys. As it is I'm typing this from the laptop that has the problem, which is intermittent. What happens is that wireless usually works on boot, and the default keyring manager asks me for my pass as it should. Problem is that sometimes when I boot up, keyring manager never comes up and I can not connect manually either. Also instead of the name of my network showing up in the wireless network list, a box with a few circular looking shapes in it is there along with the other wireless networks. So the card is seeing networks, but it cannot connect to them. Also, every time my computer comes back from a locked screen or standby or hibernate, the wireless will absolutely refuse to run. Sometimes even after I completely turn the laptop off and on again, it doesn't connect at startup. But usually a reboot allows me to connect.

The laptop is a hp dv1000 and the wireless is an intel 82801

---

### Post by noob12 on 2007-08-31
I've seen two similar problems which may be what you are seeing, but I am not sure.

(1) Sometimes the keyring window comes up behind the desktop background (!).  You will typically notice this by seeing the shape of the hidden window in the workspace manager in the bottom right panel (gnome/ubuntu).  This is a bug, but if this happens pressing ALT-TAB will generally bring it to front where you can type at it.

(2) I found the suspend and hibernate power states just don't seem to play well with networking.  I always found I had to restart networking after resuming from one of these.  I eventually changed the list STOP_SERVICES in **/etc/default/acpi-support** to include **networking**.   My line in this file now reads
```

STOP_SERVICES="mysql networking"

```
What this means is the acpi will always just stop my mysql and networking services on entry to a suspended state and restart it on resuming.  (If you don't run mysql you don't need that in there.)

---

### Post by Zef_ on 2007-08-31
Thanks for the reply. Next time it happens I'll try the 1st option by alt-tabbing, and if that doesn't work I'll give the second one a go.

Is there a console command to safely restart the networking subsystem without rebooting?

---

### Post by noob12 on 2007-08-31
These are really two separate issues.  The second solution won't address the first problem of not seeing the keyring.

---

### Post by Zef_ on 2007-08-31
Hmm I had the network just drop out now while I was using it, and it couldn't reconnect. Only option was to reboot. So I don't think the issue is necessarily to do with hibernate and suspend, though that may be part of it. It's also not just a simple problem with the keyring manager being invisible.

---

### Post by noob12 on 2007-08-31
OK.  I was just going by your first message.  I had seen two similar problems to what you had initially mentioned, but it looks like you are probably seeing something unrelated.

---

### Post by Zef_ on 2007-09-02
5 reboots and the wireless simply refuses to connect, even though I can see it in the list of wireless networks. The problem seems to be getting progressively worse now, and I have no idea why this is so.

Maybe I need to try another distro.

---

### Post by Zef_ on 2007-09-02
My wireless card is an intel 2200BG, and following these instructions, my wireless is now reinitialised. I really do not understand how doing this has unlocked it, as before even when I booted to the livecd the wireless still didn't work. This means that the hardware had been locked down somehow. Really weird stuff this linux :shock:

> **noob12 said:**
> 
Then do this.  It tells the driver to reload, and also to spit out some debugging info to
the kernel log.
```

sudo /etc/init.d/networking stop
sudo modprobe -r ipw2200
sudo modprobe ipw2200 debug=15
sudo /etc/init.d/networking start

```


---

