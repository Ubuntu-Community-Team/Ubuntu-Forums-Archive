---
title: "IPW2200 driver version question"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by Rebel Dragon on 2007-05-28
IR stoopid and this is a n00b question - 

How do I determine what version of the IPW2200 driver I am using? 

I want to download the appropriate firmware, but can't figure out which to use.

---

### Post by 4ebees on 2007-06-04
> **Rebel Dragon said:**
> IR stoopid and this is a n00b question - 

How do I determine what version of the IPW2200 driver I am using? 

I want to download the appropriate firmware, but can't figure out which to use.

Hi there,

Sorry no-one has answered earlier.

The ipw2200 drivers exist in the kernel (as far as I'm aware). The device should work 'out of the box' - as they say. I have the same device in a HP laptop and it worked immediately.

The best way to set up a wireless connection (if you're having problems) is to allow a connection that has no encryption. See if it connects and if so, then add encryption. 

That way you can more easily check if everything is working before you complicate it with encryption keys etc.

You may also wish to check:

[http://ubuntuforums.org/showthread.php?t=459665](http://ubuntuforums.org/showthread.php?t=459665)

and 

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)


Hope this helps.

---

### Post by miatawnt2b on 2007-06-07
type the following command

modinfo ipw2200

1.2.0 is the latest stable as far as I can tell.
-J

---

### Post by Rebel Dragon on 2007-07-04
Thanks for the replies! This is actually a step toward my bigger goal of getting the wifi light to function correctly. I know it's merely cosmetic, but it bugs the bejebbers out of me that I can't tell if my card is on or off. I've noticed other people have had the same issue and I've found out how to turn it on by issuing this command in a terminal window:

echo "1" | sudo tee /sys/bus/pci/devices/0000\:02\:03.0/led


The only problem is that it's "forgotten" on a reboot and it doesn't really tell you anything because FN-F2 turns the card off, but the light stays on... :confused:

---

