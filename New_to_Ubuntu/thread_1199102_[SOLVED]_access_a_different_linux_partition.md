---
title: "[SOLVED] access a different linux partition"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by wgardne on 2009-06-28
so i've corrupted my video drivers and now everytime i try to boot ubuntu it flashes a few warped images of the desktop, and then locks up on a bunch of random colors. so now i'm kind of stuck outside of ubuntu (my keyboard doesn't work during the OS seletion menu - it's stupid) & i'm typing this from a live session of some Ubuntu DVD. is there any way I can get root access on a different partition from this live session dvd? thanks

---

### Post by starcraft.man on 2009-06-28
Your keyboard doesn't even work from the GRUB prompt? That's irregular, I've rarely ever seen a video error cause that.

Anyway, I think your asking to mount your partitions and get at your data/attempt a fix. The answer is yes, just go Places menu and there should be listed your partitions. If not, there might be something wrong with them. To verify they are still there, use gparted (don't know whether or not installed on your CD, if not it's in the repos and easily installed).

Oh and you can get root access with any program on the live cd, there's no password like your default account. Just use sudo for any terminal commands and if you must launch an graphical app with root power (say nautilus the file browser) then just open the run dialog (alt+F2) and type:

```
gksudo nautilus
```

If you need more help please elaborate, I found your message a bit hard to understand.

---

### Post by wgardne on 2009-06-30
Sorry I was in a rush
 
What I did was install fglrx and all of its related packages, thinking that I was updating the ATI drivers. I was messing around with stuff I probably shouldn't have been.
 
So now my Ubuntu partition doesn't boot propery.. after the Ubuntu loading screen, it simply flashes a corrupted desktop twice, and then locks up on some graphical distortions. Since getting a PS/2 keyboard, I've been able to try every option available in Safe Mode, but still experience the same problem. I'm not sure what I can try now to uninstall the fglrx packages/restore Ubuntu, aside from just reinstalling Ubuntu (which I really don't want to do!)
 
Anything else I can try? Maybe I can uninstall those packages from inside the sudo commands?
 
Thanks

---

### Post by wgardne on 2009-06-30
[http://ubuntuforums.org/showthread.php?t=1056539&highlight=fglrx+problem](http://ubuntuforums.org/showthread.php?t=1056539&highlight=fglrx+problem)

i shoulda searched harder. this answers my question.

sorry for clogging up the forums.

edit:
using the command "sudo apt-get remove --purge fglrx* xserver-xorg-video-ati" is what ultimately did the trick

---

