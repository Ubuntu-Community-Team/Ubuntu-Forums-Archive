---
title: "Set package as manually installed (no autoremoval)"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by Mgamerz on 2010-09-27
I am using libnotify-bin for a plugin I have on thunderbird to push notifications to the desktop instead of the standard thunderbird installation.
I have Ubuntu 10.04 AMD64 on a computer with... a total of 7GB (2 HD's (4GB primary, 3GB (unused?????? wtf? set to automount at /media/3GB) ) and high specs on every other front, and I completely ran out of space trying to remove as much stuff as I could (how did that happen?), and now I cannot boot to a GUI as it runs out of space and refuses to load past something about power options failing. 
So I'm stuck in the good ol' termy. 
Anyone know how to set this so when I run autoremove it won't take it with it? I tried
aptitude unmarkauto, and guess what, the first thing it did was try to remove it (in the same command even <_<)
So...
Anyone able to help?

While I'm on the subject of 'problems I'm having' here is many more... 
I want to remove evolution as well since I only use Thunderbird. I have read around and have learned that ubuntu-desktop is one big metapackage and makes it a pain in the... eh... to remove anything from it which cuts down seriously on the amount of install space I have.
I also have no access to a linux live CD right now. My CD drive is dead and the largest flash drive I have at the moment is 256MB (Had to use mini.iso on a 128MB SD card). GRUB also doesn't work, I have to use supergrub on a floppy to boot, which is starting to fail as well as it kicks me to terminal to begin with. 
I tried update-grub (grub2) and it doesn't fix anything, it still sticks me with a blinking cursor that does nothing.

---

### Post by Chesamo on 2010-09-27
See, you're stuck with a problem that I ended up making an entire new installation script for (see my signature)... however, there is a way we can try to eke out some extra hard drive space without a reinstall.

Try ```
sudo aptitude clean
``` which will clear the cache of downloaded packages (which you don't need anymore). I'm not sure apt-get has a method of marking packages as manual... try ```
man apt-get
```

---

### Post by Mgamerz on 2010-09-27
I looked at man apt-get, but it didn't say anything about how to keep it from marking things as dependencies so that it doesn't autoremove them. I did however notice an incorrect word. It says I think in the part talking about download sources that you will 'properly get the wrong version' when it should say 'probably' (I think.)
I don't know where to submit that for correction however.
Update: Alright, I've managed to remove about 500MB of crap. Which probably will be eaten up if I update anything. I haven't booted to GUI yet since it ran out of space last time either.
I finally fixed my fstab (since I was mounting my second hard drive on / , now on /media/3GB). Is there a way to... eh utilize this more than just files I download?

---

