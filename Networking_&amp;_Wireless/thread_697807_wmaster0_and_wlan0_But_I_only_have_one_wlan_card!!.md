---
title: "wmaster0 and wlan0? But I only have one wlan card!!!"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by Anaphylaxis on 2008-02-15
Hi!

iwconfig lists both a wmaster0 and wlan0 output. I only have one wireless card. What part of ubuntu is responsible for assigning names to wireless interfaces? Where can I find some more information on this?

I think my card should be using the rt61 ralink driver. Does that explain anything? 

I saw that a similar question has been asked before, but not answered. [http://ubuntuforums.org/showthread.php?t=488057](http://ubuntuforums.org/showthread.php?t=488057)

---

### Post by rustybronco on 2008-02-15
Don't know if I can help.
[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)
> Lets clarify device names first. Regularly you should only see two new device names: 

wmaster0 
wlan0 
The wmaster0 device is what we call the master device. The master device is an internal master device used only by mac80211. It should be ignored by users. If possible we will try to hide it from users later. 

On distribution releases with old udev rules you may end up with strange network device names, for example, wlan0_rename. You may also end up with master device names such as eth3, when this was actually intended to be named wmaster0. This happens because master interface has the same MAC address as the real interface, and it is created first. The old udev rule, which keys on the MAC addres, may rename it to device names like eth3, for example. Then the real interface is created, udev sees that it has already renamed an interface with that MAC and gives it the wlan0_rename name.

---

### Post by Anaphylaxis on 2008-02-15
Thanks! Now I have some clues that can help me learn more. I also wasn't aware of the wireless page you linked to.

---

### Post by kevdog on 2008-02-15
rustybronco

Where the heck have you been??

---

### Post by rustybronco on 2008-02-15
Hey kevdog, Here every day doing my job :)
By the way congrats on getting your post stickied it's a fine jewel of a post!!!!
(Don't worry i'll put the turkey back up soon so you can find me.)

---

### Post by kevdog on 2008-02-15
Off topic of course

But now that the topic has been stickied -- I'm actually getting less questions about the method than before -- Weird.  Just be careful what you wish for -- a stickied thread isn't always a good thing.  

By the way, you should write a how to for the hardy upgrade along with use of the rt2x000 driver for ra based chipsets.  Not a thread likely to get stickied, however I would consult this how-to often.  I know you have done it with this method, so it would be a great addition to other ra chipset / Gutsy users.

---

