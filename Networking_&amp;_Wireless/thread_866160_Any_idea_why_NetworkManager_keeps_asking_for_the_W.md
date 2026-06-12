---
title: "Any idea why NetworkManager keeps asking for the WEP key?"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by bkline on 2008-07-21
I've got a Broadcom wireless chip in my laptop, using the b43 driver.  I'm experiencing very annoying behavior in Ubuntu, where Network Manager keeps stopping the traffic and asking me for the WEP key.  I give it the key, it works for a while, then it stops again and I have to type it in again.  As you can imagine, this gets old quickly.  The signal's not super strong where the laptop usually sits, but it's generally over 50% strength.  The laptop dual boots, and in Windows I don't experience this problem at all (not that I view Windows as a solution).

Any suggestions?  Any further information I can supply about my configuration that might be useful?

Thanks!

---

### Post by NilsE on 2008-07-21
Is it asking the first time you connect or just after a period of time.
  There is the possibility that it is losing the connection and forcing re-authentication. 

One possible way to fix that is to make sure the keyring is authorizing nm-applet.  Go into Applications > Accessories > Passwords and encryption keys and see if wireless network is under the password tab. Let us know what you find and we can see where to go from there.

---

### Post by bkline on 2008-07-21
> **NilsE said:**
> Is it asking the first time you connect or just after a period of time.

Sometimes it asks when I first boot up the system, and sometimes it doesn't at first, but then asks later on.

> Go into Applications > Accessories > Passwords and encryption keys and see if wireless network is under the password tab. Let us know what you find and we can see where to go from there.

It has the correct hex key for the network I'm connecting to ("Passphrase for wireless network kline"), so I'm puzzled that it still feels the need to keep asking me for the key.

---

### Post by sputnikkk on 2008-07-21
I tried for nearly a week straight with that gui app, and [ for me ] it's borked.  Thats whats wrong with it :)

I could network just fine with it - until I rebooted.  Then, re enter all the settings for WPA2 and passkey.

Just installed Wicd and viola - first reboot the software fires up - hits my wireless LAn and connects 

[http://wicd.net/](http://wicd.net/)

Linksys Router running WPA2 and staic Ip's

Linksys WPMG54 [older] wireless nic 

Works for me.  Freakin pumped right now ... soooo many hrs messing with conf files and command line syntax and reboots and frustrations - SOLVED!

Is Wicd better than sex?  Just maybe ...

---

