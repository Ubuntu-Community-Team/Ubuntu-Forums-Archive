---
title: "Wireless card won't remain turned off"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by zcal on 2007-05-12
I recently did a fresh install of Feisty (was using Edgy).  In Edgy, I never had trouble with this.

The problem is, when I right-click on Feisty's network-manager and tell it to deactivate the wireless, it does so, but after a few minutes the wireless card turns itself back on.  I can tell because the laptop's wireless LED comes back on.  However, this does not register with network-manager, which still thinks it's turned off.  Also, my Fn+F5 hotkey, which should manually turn off the card, has no effect.  I never experienced this problem in Edgy.

I've got an IBM ThinkPad R40 with an integrated Cisco Aironet card.  Also, I've added
        # ThinkPad BIOS Hot Keys
        Option          "BIOSHotkeys" "on"
to the "Device" section of xorg.conf, which I thought might solve the non-functioning Fn key problem.  No such luck.  (The other Fn key combinations seem to work fine, by the way.)

---

### Post by zcal on 2007-05-13
Just did a fresh reinstall of Feisty for various reasons.  This problem still persists.  Any ideas?

---

### Post by netztier on 2007-05-14
> **zcal said:**
> Just did a fresh reinstall of Feisty for various reasons.  This problem still persists.  Any ideas?

Are you sure that the LED is WLAN-related only?

Ever since Feisty, the intertwined Bluetooth/WLAN function on my HP Compaq nc6000 (also with an Atheros miniPCI module) has started working for both technologies - and the "Wireless LED" is always-on, even if I "disable wireless" in Network-Manager. Using the wireless button now disables both functions.

best regards

Marc

---

### Post by zcal on 2007-05-14
> **netztier said:**
> Are you sure that the LED is WLAN-related only?

I do have an infrared port, but it's not on according to Gnome's network controls list.  And I'm not sure if the LED would light up if it was in use either.  I'll have to do some digging and try to figure that out...

---

