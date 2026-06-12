---
title: "graphic login screen gone/damaged"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by cronos on 2009-11-10
Hi all,

I am running Ubuntu 9.10, and everything was running fine until I tried to boot Ubuntu after a power failure caused my computer to switched off while Ubuntu was running/idling.

So, when I try to boot, the white Ubuntu logo would show up as normal, but then it would display a text login screen. The brown/black screen does not show up at all.

Sometimes the text login screen would flicker while displaying "starting firewall", as if it is in some kind of loop. It is hard to type when this happens.

If I login, I don't know what to do. I tried typing "startx", but it can't find my screen?

Some other stuff that is worth noting before this problem...

I installed firestarter, and I adjusted the settings; I only opened some ports for Amule.

When I installed a program using CLI, I noticed that a Nvidia package was listed as no longer needed. I don't know if the package was automatically removed. But, I know I did not remove it, and would not remove it, because I do not trust removing unneeded packages.

If there is any other information that you require, please let me know.

I hope someone can help me. Thanks.

---

### Post by aPaSv5 on 2009-11-10
Hmmm....

Maybe ```
sudo restart gdm
``` would work? I don't think it would hurt anything, but then again, if ```
startx
``` doesn't work and you think an nVidia package was accidentally un-installed, then maybe you should start by trying to locate that package with ```
sudo aptitude
```. Just type '/' to search (without the quotes!).

---

### Post by cronos on 2009-11-10
Hi aPaSv5, thanks for your suggestions.

First of all, I should point out that the only way I can log in via text prompt, is by selecting 'recovery' from Grub, and then try to resume boot.

If I try to boot without going into recovery, the boot process seems to stop/loop with starting/stopping (cant remember which) firewall.  At this stage, I can type, but slowly and the login times out after entering password.

Anyway, I tried to follow your suggestions without success, but at least we can make progress. :)

sudo restart GDM displays 'Restart: Unknown instance"

As for sudo aptitude... It displays:-
idA Nvidia-190-kernal-source" 33.9mb

The rest of the Nvidia stuff is listed, but I don't think it is installed, and I am not sure if they need to be installed.

If I try startx, it displays:-
Failed to load module Nvidia (module does not exist)
No drivers available

Fatal Server Error: No screen found

Xinit: No such file/directory; no such process


Sorry if this seems messy.  I am only using one dual booting machine. Grrr...

---

### Post by ST3ALTHPSYCH0 on 2009-11-10
Try this at the command prompt
```

sudo apt-get install envyng-qt

```

Then run
```

sudo envyng -t

```

I know how annoying broken x issues can be... good luck

---

### Post by cronos on 2009-11-10
Hi ST3ALTHPSYCH0,

Thanks for your suggestion. :)

I tried to do what you said, but it said that the package cannot be found.

Yeah, I am not the type of person who would format and start over, but at this stage, I am contemplating backing up my home folder and starting fresh.  But, I am still open to suggestions. :)

---

### Post by cronos on 2009-11-10
Woohoo! :)

I tried again using the envyng-qt, and it didn't work.  But, then I noticed it said 'type envyng-agcore to install' (or whatever it was), and it downloaded and took me a nice screen that allowed me to reinstall my Nvidia drivers.  I restarted my computer, and it worked!

It is nice to see my Ubuntu screen again.  Been using Windows throughout most of the day, so it feels good to be back on Ubuntu. 

Thanks ST3ALTHPSYCH0. :)

---

### Post by ST3ALTHPSYCH0 on 2009-11-10
After spending two days breaking and reconfiguring my xserver attempting to get better than 640x480 graphics, it's the least I can do to help!

---

