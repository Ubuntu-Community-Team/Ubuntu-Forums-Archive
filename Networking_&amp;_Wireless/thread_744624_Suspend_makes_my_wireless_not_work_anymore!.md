---
title: "Suspend makes my wireless not work anymore!"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by systemintheglitch on 2008-04-03
The nm-applet doesn't show any wireless networks after suspend!
I read a thread somewhere to remove /etc/udev/something/70-persistent-net-rules or something and reboot. That didn't help. 

Any suggestions?

---

### Post by systemintheglitch on 2008-04-03
actually now that I check, sometimes the networks show up but I can't connect
I think I have a thinkpad wireless card not intell. Could someone please help this is the one thing preventing me from using ubuntu

---

### Post by systemintheglitch on 2008-04-04
Can someone help with some advice? This is really horrible! Ubuntu takes forever to boot up and this means I have to reboot everytime I suspend just to reboot up the wireless. 

What is going on in a reboot that makes it work? Can't I just write a script that does whatever the reboot does?

thanks..

---

### Post by Whiffle on 2008-04-04
Hmmm, I'm guessing you've got madwifi, right?  Some more hardware info would be good.

Chances are you need to tell it to unload the module(s) for your wireless card on suspend, and then reload them on wakeup.  If I remember correctly, you can add the modules to a list in 

/etc/default/acpi-support

There should be a line about modules in there.

---

### Post by systemintheglitch on 2008-04-04
I read somewhere someone was able to fix this with the following commands after suspend.

sudo rmmod ath_pci
sudo modprobe ath_pci

Why do I have to do this?

And how do I do what you recomended? By making them unload on sleep automatically? What line do I edit? Thanks you so much! what is the name of the module?

---

### Post by Whiffle on 2008-04-04
ath_pci is the module.  

Look for this in /etc/default/acpi-support

```

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

```

and add ath_pci like this;

MODULES="ath_pci"

and hopefully that will take  care of it.

---

### Post by systemintheglitch on 2008-04-05
> **Whiffle said:**
> ath_pci is the module.  

Look for this in /etc/default/acpi-support

```

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

```

and add ath_pci like this;

MODULES="ath_pci"

and hopefully that will take  care of it.


Hmmm that didn't work. For some reason I have to run those lines of code everytime i suspend.

---

### Post by systemintheglitch on 2008-04-07
Any other suggestions?
I know there is some script that is run on resume, and I can just put those two lines in that script but I would like to get to the root of the problem

Thanks so much.

---

### Post by Whiffle on 2008-04-07
YEah I really don't know why they aren't getting run on suspend.  You miught try running the module unloading script in /etc/acpi/suspend.d/ from the command line and see if it returns any errors.

---

