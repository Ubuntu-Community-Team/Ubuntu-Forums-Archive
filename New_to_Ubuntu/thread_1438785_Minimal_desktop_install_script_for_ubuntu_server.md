---
title: "Minimal desktop install script for ubuntu server"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by muteXe on 2010-03-25
Hiya,
I found this script via google, cant remember where from or how old I'm. I just wondered if it would still work on a modern upbuntu server install.

```

#!/bin/bash
ROOT_UID=0
E_NOTROOT=87
if [ "$UID" -ne "$ROOT_UID" ]
then
   echo "Try again... as root."
   exit $E_NOTROOT
fi
p='gnome-core gdm network-manager-gnome fast-user-switch-applet human-theme x11-xserver-utils tangerine-icon-theme gnome-themes-ubuntu ubuntu-artwork jockey-gtk gnome-screensaver gnome-utils gcalctool tsclient'
apt-get update
apt-get install $p -y --force-yes 2>> ~/error.log
exit

```

I can't see anything out of the ordinary, but just wanted to check with people who know more about scripts and servers than I do (which is 99% of the population of the planet).

Cheers,

mute

---

### Post by unmole on 2010-03-25
May I know why you are using a script instead of executing commands directly?

---

### Post by muteXe on 2010-03-25
yeah my friend has just started to hire a linux server. he want a gui frontend tho to do vnc from his home machine.  He's asked me to help set it up. I'm trying to find an easy way to do it. hence the script.

---

### Post by undecim on 2010-03-25
> **unmole said:**
> May I know why you are a script instead of executing commands directly?

+1

This script just boils down to
```
sudo apt-get update
sudo apt-get install gnome-core gdm network-manager-gnome fast-user-switch-applet human-theme x11-xserver-utils tangerine-icon-theme gnome-themes-ubuntu ubuntu-artwork jockey-gtk gnome-screensaver gnome-utils gcalctool tsclient
```

It's actually safer to just run those commands manually, because then you can sort out any missing packages or package conflicts yourself.

EDIT: also, I see several probably unnecessary packages and nothing to do with VNC.

---

### Post by muteXe on 2010-03-25
yep, nothing to do with vnc yet, that'll come after the install. He can do that, i just wanted to start him off on the right track.

Thanks for your help.

edit: i'll just tell him to run those 2 lines manually then.

---

