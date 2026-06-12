---
title: "Updating from 8.04&gt;8.10&gt;9"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by MikesGuitar on 2009-04-23
Hey guys, I have Ubuntu 8.04 running now and am dying to see the latest update. I know I have to update to 8.10 before going to 9. When I typed in 'update-manager -d' in the run program box, it came up the first time, but I had to cancel the update before starting due to lack of battery. Now when I type it in nothing comes up. HELP! Thanks

---

### Post by Temposs on 2009-04-23
That's generally not a good thing, to cancel an upgrade :-P

Try opening /etc/apt/sources.lst and change everything that says "8.10" or "intrepid" to "8.04" or "hardy", respectively. Then save and open the update manager again.

---

### Post by MikesGuitar on 2009-04-23
Got to where you told me to go but not quite sure exactly what I'm doing. Still a novice to Linux

---

### Post by Temposs on 2009-04-23
Can you paste your sources.lst file here?

---

### Post by MikesGuitar on 2009-04-23
No I dont think so, it is just a list with some unchecked boxes, do you think I should recheck them?

---

### Post by Temposs on 2009-04-23
ok, umm, do this:

```
gedit /etc/apt/sources.lst
```

Paste the contents of the file that you see.

---

### Post by MikesGuitar on 2009-04-23
Here is a screen shot of what I got, its an attachment

---

### Post by Temposs on 2009-04-23
Well, you still didn't do what I said, but your screenshot looks like it's already upgraded your repositories. Try opening update manager through System->Administration->Update Manager. If it opens, click Reload. See if a ton of updates appear.

---

### Post by MikesGuitar on 2009-04-23
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main

---

### Post by AXeS on 2009-04-23
> **Temposs said:**
> Well, you still didn't do what I said, but your screenshot looks like it's already upgraded your repositories. Try opening update manager through System->Administration->Update Manager. If it opens, click Reload. See if a ton of updates appear.


what Temposs means is that you should type that 'code' in 'command-line' aka 'terminal' if you using UBUNTU and 'konsole' if you running in KUBUNTU. 

and Temposs you should understand Mikesguitar said he is a novice.

---

### Post by AXeS on 2009-04-23
ok you still have hardy repo's?

---

### Post by MikesGuitar on 2009-04-23
I got to the sources and posted what i have above. It dosent look like there is anything out of the ordinary to me, but i am a novice

---

### Post by AXeS on 2009-04-23
> **MikesGuitar said:**
> I got to the sources and posted what i have above. It dosent look like there is anything out of the ordinary to me, but i am a novice


dont worry,id say rather im still beginner with a bit of know-how.
i dont think any 1 person would know everything especially troubleshooting.

but give it time you'll get answers,kz though im sorted i still didnt get my answers (almost two months),i fiddled re-installed and fiddled till i got it right.dont know how though.

---

### Post by CRIMPS on 2009-04-23
> **Temposs said:**
> Well, you still didn't do what I said, but your screenshot looks like it's already upgraded your repositories. Try opening update manager through System->Administration->Update Manager. If it opens, click Reload. See if a ton of updates appear.

Can you confirm you have opened and reloaded Update Manager?

---

### Post by MikesGuitar on 2009-04-23
Yea a bunch of times, just says my system is up to date

---

