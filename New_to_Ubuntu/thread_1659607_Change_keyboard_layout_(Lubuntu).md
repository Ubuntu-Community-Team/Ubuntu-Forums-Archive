---
title: "Change keyboard layout (Lubuntu)"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by Paddy Landau on 2011-01-04
The keyboard on my Lubuntu machine broke, so I replaced it with a new keyboard.

However, the old keyboard was UK and the new one US.

How do I change the keyboard layout on Lubuntu?

---

### Post by cavalier911 on 2011-01-04
This is a new gui for setting your keymap/keyboard for i386 only. 
Installed and works on Lubuntu 10.04 LTS
_[https://launchpad.net/~lubuntu-desktop/+archive/ppa/+build/2081504/+files/lxkeymap_0.3%7Eppa3_all.deb](https://launchpad.net/~lubuntu-desktop/+archive/ppa/+build/2081504/+files/lxkeymap_0.3%7Eppa3_all.deb)_

menu/preferences/lxkeymap

Console keymap configuration:
Ctrl+alt F1
```
sudo nano -B /etc/default/console-setup
```Configure XKBMODEL= XKBLAYOUT= and save
```
sudo setupcon
```Login and test your keyboard setup.
To change repeat the above steps in the same order.
To autoconfigure the setting on boot.
```
sudo nano  /etc/rc.local
```Add whats in [B]bold
[/B]
```
    
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
**setupcon**
exit 0
```Ctrl+alt F7 returns you to X

---

### Post by Paddy Landau on 2011-01-04
EDIT: cancel this post

---

### Post by Paddy Landau on 2011-01-04
Thank you for your post.

I already have the PPA listed in my repositories, and I did not find lxkeymap in Synaptic, so that did not work.

I used your terminal method. setupcon complained about the variant, so I commented out the XKBVARIANT line and now it works.

Thank you!

---

