---
title: "How to delete GRUB?"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by camn on 2010-06-16
I just installed windows XP on an empty partition of my HD then deleted my Ubuntu partition to give windows more memory but GRUB is stil there and won't let me boot windows... I tried Googling something about it but everyone said to use the windows install disk but mine is modified to skip the part that asks if you want to repair (damn torrented OSes)

---

### Post by ks07 on 2010-06-16
[See here.]("http://ubuntuforums.org/showthread.php?t=391387") Search is a wonderful thing :p.

Btw, not sure it's a good idea to be talking about torrented Windows... ;)

---

### Post by John Bean on 2010-06-16
> **ks07 said:**
> []("http://ubuntuforums.org/showthread.php?t=391387")Btw, not sure it's a good idea to be talking about torrented Windows... ;)

I'm not sure it's a good idea to install them either. Who knows what backdoors, keyloggers, rootkits,... are built into it. It's bad enough running a real version without patching it before connecting to the outside world; I hate to think what the hacked versions are like.

---

### Post by camn on 2010-06-16
> **ks07 said:**
> [See here.]("http://ubuntuforums.org/showthread.php?t=391387") Search is a wonderful thing :p.

Btw, not sure it's a good idea to be talking about torrented Windows... ;)

None of those would work... Is there a way to do it from an Ubuntu Live CD?

---

### Post by ks07 on 2010-06-16
> **camn said:**
> None of those would work... Is there a way to do it from an Ubuntu Live CD?
Sorry, wrong link. :p [Try this one instead.]("http://ubuntuforums.org/showthread.php?t=622828")

EDIT: Seems ms-sys is no longer in the repos. There's a thread [here]("http://ubuntuforums.org/showthread.php?t=868342") with different ways of getting it (or doing the same job).

---

### Post by John Bean on 2010-06-16
> **camn said:**
> None of those would work

"Ultimate Boot" works fine. Did you actually read the thread?

---

### Post by camn on 2010-06-16
> **ks07 said:**
> Sorry, wrong link. :p [Try this one instead.]("http://ubuntuforums.org/showthread.php?t=622828")

EDIT: Seems ms-sys is no longer in the repos. There's a thread [here]("http://ubuntuforums.org/showthread.php?t=868342") with different ways of getting it (or doing the same job).

When I tried to do sudo lilo -M /dev/sda mbr it said E: You don't have enough free space in /var/cache/apt/archives/. but in gparted it says there is over 2GB of free space...
EDIT: actually it said that after I did sudo apt-get install lilo

---

### Post by camn on 2010-06-16
> **John Bean said:**
> "Ultimate Boot" works fine. Did you actually read the thread?

I can't get on a computer except for the Ubuntu Live CD, wich (for some reason) doesn't have working internet for me.

---

### Post by ks07 on 2010-06-16
> **camn said:**
> When I tried to do sudo lilo -M /dev/sda mbr it said E: You don't have enough free space in /var/cache/apt/archives/. but in gparted it says there is over 2GB of free space...
Not sure why you're given that error when using lilo - but hey. To clear some space in your apt archives either run ```
sudo apt-get clean
``` or ```
sudo apt-get autoclean
```. Autoclean will only delete uninstalled packages, but this may not clear enough space. Clean will delete all downloaded packages whether they are installed or not (but will not uninstall them, so don't worry).

---

### Post by camn on 2010-06-16
> **ks07 said:**
> Not sure why you're given that error when using lilo - but hey. To clear some space in your apt archives either run ```
sudo apt-get clean
``` or ```
sudo apt-get autoclean
```. Autoclean will only delete uninstalled packages, but this may not clear enough space. Clean will delete all downloaded packages whether they are installed or not (but will not uninstall them, so don't worry).

Nope, still not enough space ._.

---

### Post by John Bean on 2010-06-16
> **camn said:**
> I can't get on a computer except for the Ubuntu Live CD, wich (for some reason) doesn't have working internet for me.

If that's the case then how do you expect "apt-get install lilo" to work?

---

### Post by camn on 2010-06-16
Update:
I got onto my mom's computer and I'm downloading the Ultimate Boot thing to burn it to a disk...

---

### Post by John Bean on 2010-06-16
> **camn said:**
> Update:
I got onto my mom's computer and I'm downloading the Ultimate Boot thing to burn it to a disk...

Progress at last :-)

Let us know how you get on.

---

### Post by camn on 2010-06-16
> **John Bean said:**
> Progress at last :-)

Let us know how you get on.

The UBCD worked, it was a little confusing though, I just clicked the first thing that said "MBR" :/

---

### Post by ks07 on 2010-06-16
> **camn said:**
> The UBCD worked, it was a little confusing though, I just clicked the first thing that said "MBR" :/
Hey, if it worked it doesn't really matter what happened. :lolflag: Glad you fixed it, remember to mark the thread as solved using 'thread tools'.

---

