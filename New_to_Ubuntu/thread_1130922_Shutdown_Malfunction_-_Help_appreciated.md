---
title: "Shutdown Malfunction - Help appreciated"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by alienbroth on 2009-04-20
Hey all,

I have the 8.04 Hardy heron version of Ubuntu.  I am very much a beginner.

I am experiencing a problem with Ubuntu....my only one really.  When I want to shut my computer down it always restarts!  If I go to the upper right of the screen and select the shutdown option from the window that pops up, it restarts.  If i chose the "Quit" option from the System Menu and chose shutdown from the window that pops up, it restarts.  So, what I end up doing is selecting shutdown, wait until the computer starts to boot up again, then press and hold my power button to force it off.  I know this is not a good way to do it.

I wonder if anyone can help me with this.  I would say that this started happening somewhere around the time i installed Urban Terror, or around the time I set this computer up on a wireless network.  I don't think it ever happened before that, but i could be wrong (those are just a couple of the recent changes I have made to my computer).

Thanks,

Alienbroth

---

### Post by rustutzman on 2009-04-20
It may not be related but what is your BIOS setting for behavior after loss of power? If it is set to always turn on try setting it to leave it off. This shouldn't make any difference but I figured it might be worth a shot to try it.

Russ

---

### Post by cmnorton on 2009-04-20
What happens when you go to a command line (X-term) and enter 

sudo shutdown -h "now"

Does it shutdown then?

Sounds like your shutdown menu is goofey. Try uninstalling and re-installing the  fast-user-switch-applet. You can do that in System --> Administration --> Synaptic Package Manager.

---

### Post by svennam on 2009-04-20
I don't have a cure.  But I have something to share with you.  Yesterday I re-installed my Ubuntu 8.10 Server.  I am experiencing the same problem since re-install.  Could you please share solution to this, if you get one.  Please.

> **alienbroth said:**
> Hey all,

I have the 8.04 Hardy heron version of Ubuntu.  I am very much a beginner.

I am experiencing a problem with Ubuntu....my only one really.  When I want to shut my computer down it always restarts!  If I go to the upper right of the screen and select the shutdown option from the window that pops up, it restarts.  If i chose the "Quit" option from the System Menu and chose shutdown from the window that pops up, it restarts.  So, what I end up doing is selecting shutdown, wait until the computer starts to boot up again, then press and hold my power button to force it off.  I know this is not a good way to do it.

I wonder if anyone can help me with this.  I would say that this started happening somewhere around the time i installed Urban Terror, or around the time I set this computer up on a wireless network.  I don't think it ever happened before that, but i could be wrong (those are just a couple of the recent changes I have made to my computer).

Thanks,

Alienbroth

---

### Post by Sef on 2009-04-20
> It may not be related but what is your BIOS setting for behavior after loss of power?Check the power management setting in the BIOS.  

>  When I want to shut my computer down it always restarts!

I had the opposite problem (reboot = shutdown), but changing a setting in the BIOS got things working right.

---

### Post by MysticGold04 on 2009-04-20
I had this exact same problem with an older Gateway PC running Windows... I had to update the Bios to the latest available release, and then the issue stopped.  You may want to check to see if there is an available Bios update for your machine, and upgrade it to see if that helps any.

---

### Post by gonkyouka on 2010-08-14
this happened to me too. i set my bios to its defaults settings and everythings ok now

---

### Post by LewRockwell on 2010-08-14
Couple of random thoughts:

In BIOS and elsewhere in some operating systems there are selections for whether or not you want the system to restart automatically after a failure.

If your operating system is failing to shut down properly this may be occurring.

We don't allow our units to restart after failures.

.

---

