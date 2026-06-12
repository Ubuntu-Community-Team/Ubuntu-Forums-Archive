---
title: "Wireless and Gnome-Keyring (Fiesty)"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by Ateo on 2007-04-12
Hello all,

This applies only to the Fiesty Fawn release (Ubuntu 7.04_beta).

**Synopsis**

You are sick and tired of having to enter your Gnome Keyring 'key/password' each time your wireless manager applet wanted to establish a wireless connection to an AP. Even on a brand new install of Ubuntu's Feisty Fawn release.

So, here's how to fix this 'feature'...

Install libpam-keyring
```
$ sudo apt-get install libpam-keyring
```

Next, we need to tell GDM use the keyring modules when we log in so add the following code to the end of the file. This basically tells GDM to pass your password on to the keyring to use:
[COLOR="Red"]**/etc/pam.d/gdm**[/COLOR] (sudo gedit /etc/pam.d/gdm):

```
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so
```

Next, delete your keyrings
```
$ rm -fr ~/.gnome/keyrings/
```

Lastly, reboot. I found that simply logging out did not work, for me, but whatever. You'll need your network key for the ESSID to be used. Enter that and you're done. To verify it works, simply reboot one last time.

HTH.

Note: If this is a dupe, sorry but I couldn't find it.

---

