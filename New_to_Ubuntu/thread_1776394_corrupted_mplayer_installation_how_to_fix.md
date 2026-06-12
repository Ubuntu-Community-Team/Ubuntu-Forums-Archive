---
title: "corrupted mplayer installation how to fix"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by msinfo on 2011-06-06
Hello Reader,
Just migrated to Ubuntu few days ago.
Tried installing mplayer using ...... sudo apt-get install mplayer
Installation was done but I could not see mplayer in application also tried .............. gmlayer command, but of no use.
So for fresh installation I tried Ubuntu software center option, and tried to install mplayer from their but following error comes: 

Package operation failed.
E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package. (due to missing arch): 

Same happening when I am trying to uninstall Wine, palyonlinux, 

Also tried  sudo apt-get clean and its some variation but they all failed.

Waiting for friendly help! :o

---

### Post by andrew.46 on 2011-06-06
> **msinfo said:**
> Tried installing mplayer using ...... sudo apt-get install mplayer
Installation was done but I could not see mplayer in application also tried .............. gmlayer command, but of no use.

MPlayer is actually a commandline application so you will not find it in your menu and GMPlayer is not by default installed with MPlayer. Perhaps install a better gui that is also a frontend for MPlayer:

```
sudo apt-get -y install smplayer smplayer-themes qt4-qtconfig
```

You will find SMPlayer in your menu and it functions as a very nice gui for the commandline player. I am not sure about your package manager error though...

---

### Post by SeijiSensei on 2011-06-06
To get rid of the core fonts problem, install **ubuntu-restricted-extras** (or kubuntu-restricted-extras if you're using Kubuntu).  Those are the Microsoft "core fonts" like Verdana and Tahoma.  You'll see a text screen pop up along the way asking you to agree to the the license.  Use the tab key to highlight the [OK] item, then hit enter to continue.

You'll need the restricted-extras package to watch DVDs, too.  After it completes, run "sudo /usr/share/doc/libdvdread4/install-css.sh" to download and install the required libdvdcss2.

You may find that the version of mplayer that's in the repositories won't play certain H.264-encoded files.  See [this thread]("http://ubuntuforums.org/showthread.php?t=1747753") for details on methods to fix this.

---

### Post by msinfo on 2011-06-06
@Andrew
Thanks for replying so quick.
As you said, executed command. Now I see open terminal with End User Licence Agreement form, but can't move forward over it.
There is OK option, but nothing works over it. Should I close terminal or it would result in corrupt installation again.
And when I finished typing this terminal is bit hanged with overlay images of other application.
Is there any fix for this.

---

### Post by SeijiSensei on 2011-06-06
> **msinfo said:**
> There is OK option, but nothing works over it.

Read my post above.  Use the tab key, hit enter.

---

### Post by msinfo on 2011-06-06
@[SeijiSensei]("http://ubuntuforums.org/member.php?u=698195")
@Andrew
Thank you friends, because of you all, my multimedia problem got solved within half an hour.

Problem:
Mplayer installation.
Not quality performance for audio/video playback by VLC/Totem/etc.
Getting stuck at EULA form

Solution
Installed SMplayer.
Hitting Tab and than Enter for EULA form problem. (I laughed at myself, because even after dual booting with windows7, this small thing escaped from my mind)

Feeling Happy and Relaxed

---

### Post by andrew.46 on 2011-06-06
> **msinfo said:**
> Thank you friends, because of you all, my multimedia problem got solved within half an hour.

Excellent news :).

---

