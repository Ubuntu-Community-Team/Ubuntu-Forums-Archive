---
title: "issues with nm-applet"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by virtualmaster on 2007-06-05
Well, I recently switched over to ubuntu,and got started mostly without issues. I'm fairly proficient with a computer, and so wasn't really expecting them. Theres just this one thing that irks me. When I use nm-applet to sign in to an encrypted network, it assumes that Im using WEP ascii 128 open system. This is an issue when Im using the keyring to sign in, since it doesnt let me change those settings. The router Im connecting to uses WEP 64 bit hex, with a pre-shared key. Please don't tell me to switch over to WPA, Some other devices I have dont support it. The way I've been getting around this so far is to deny it keyring access, but this is an annoying process, as I need to reenter the key. Is there some easier way?

---

### Post by reh4c on 2007-06-10
Greetings.  This procedure worked on my iBook:  [http://ubuntuforums.org/showthread.php?t=463639&highlight=keyring](http://ubuntuforums.org/showthread.php?t=463639&highlight=keyring)
Good luck!

---

### Post by ugm6hr on 2007-06-10
> **virtualmaster said:**
> Well, I recently switched over to ubuntu,and got started mostly without issues. I'm fairly proficient with a computer, and so wasn't really expecting them. Theres just this one thing that irks me. When I use nm-applet to sign in to an encrypted network, it assumes that Im using WEP ascii 128 open system. This is an issue when Im using the keyring to sign in, since it doesnt let me change those settings. The router Im connecting to uses WEP 64 bit hex, with a pre-shared key. Please don't tell me to switch over to WPA, Some other devices I have dont support it. The way I've been getting around this so far is to deny it keyring access, but this is an annoying process, as I need to reenter the key. Is there some easier way?

Couple of ideas (for Feisty) - not sure whether they will work, but.....

The easy route - which should work fine:
Try deleting the GNOME keyring thing (assuming you have a record of any keys stored there):
[http://ubuntuforums.org/showthread.php?t=157808&page=2](http://ubuntuforums.org/showthread.php?t=157808&page=2)
When you **restart**, it should ask for the wireless network password again (after asking for a new keyring password) - and if you enter the WEP key correctly (as 64HEX), it should remember it correctly for future logins.  Certainly, mine works correctly with both 64 and 128 HEX-key WEP networks.

If this doesn't help - you might try using Wicd instead of Network Manager.  It is less flashy (without the live scanning applet), but I found that one laptop will not do WPA with Network Manager, but will with Wicd (but only the 1.2.9 testing release - the "stable" 1.2.7 was totally unstable!).  It does require you to uninstall Network Manager and reboot to give it a try.
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

