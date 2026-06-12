---
title: "Salvaging a trashed upgrade"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by Linux_Man on 2009-11-01
So last night I started an upgrade of my Ubuntu 9.04 laptop to Ubuntu 9.10 all went well until despite my instructions DO NOT TURN THIS OFF FOR ANY REASON my roomate managed to turn of my computer because it was making "funny noises" -.-; so needless to say my computer won't boot to the desktop and will only boot to the recovery shell. The error it gives me is /temp: waiting for (null)

swap:waiting for UUID=(long hex string I don't think is important, if its needed I can post the entire thing)

Press ESC to enter a recovery shell

In the recovery shell I can access my documents it just won't boot to the desktop. So is there an easy way I can fix this (sadly no I don't have an fstab backup....) or am I just going to have to do a clean install?

---

### Post by kansasnoob on 2009-11-01
Do you have an Ubuntu Live CD? It needn't be Karmic.

If so I'd boot to the Live Desktop (just choose try Ubuntu without changes to disc) and mount and chroot the proper partition:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

**[COLOR="Red"]If you have any doubts about which partition to mount post the output from terminal of:[/COLOR]**

```
sudo fdisk -l
```

**[COLOR="Red"]before proceeding![/COLOR]**

I'd then try to resume the upgrade by running the command:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

If in doubt ask more questions!

---

### Post by LewRockwell on 2009-11-01
time for a NEW roommate

perhaps one that listens and can follow directions

.

---

