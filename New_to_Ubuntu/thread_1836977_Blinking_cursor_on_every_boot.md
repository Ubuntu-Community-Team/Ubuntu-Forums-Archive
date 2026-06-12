---
title: "Blinking cursor on every boot?"
date: 2011-09-01
forum: New to Ubuntu
---

### Post by Doggerdoo on 2011-09-01
Everytime i boot, there is a blinking cursor. Sometimes i just have to wait for 2 min. and it boots to ubuntu, but other times i get a blank screen...? this is getting pretty annoying. 

Please Help!!

:confused:

---

### Post by papibe on 2011-09-01
[Here]("http://ubuntuforums.org/showthread.php?t=1743535&highlight=black") are various tips.

Regards.

---

### Post by Doggerdoo on 2011-09-01
i reinstalled grub using grub customiser, but when i select ubuntu in grub i still get the same problem!

:mad:

---

### Post by Doggerdoo on 2011-09-01
Please Help!!!

---

### Post by Doggerdoo on 2011-09-01
when it works, it gets stuck at "Checking Disk 1 of 1 (70% Complete)

---

### Post by anewguy on 2011-09-01
If you get to the blinking cursor after selecting ubuntu from the grub menu, try holding down ctr and alt and pressing the F1 key - do you get a log on screen?  Post back from that and maybe we can do more to help.  Also, at the grub menu, you may want to edit the boot line to include nomodeset.  What kind of hardware are you running?

I'm a little worried about your file system check hanging at 70% - could be a hardware error, or if there is some sort of display problem (at this point I think it's still just a terminal, not an xwindow, so I don't think it would be a video driver issue causing this.

Dave ;)

---

### Post by Doggerdoo on 2011-09-01
GRUB doesnt even appear anymore for some reason.....

:confused:

---

### Post by anewguy on 2011-09-02
Sounds like a hardware problem.

Dave ;)

---

### Post by femmerlich on 2011-09-02
I had the same problem once with the PC from my neighbours. I never found out the reason, but after re-installing grub, cleaning the APT cache and installing the latest updates the problem was solved.

Here's what I did:

Access the Ubuntu installation from a LiveCD, chroot into the HDD installation and re-install grub2. You can find a description [here]("https://help.ubuntu.com/community/Grub2#ChRoot").

Before leaving the chroot environment in step 11, clean the cache of DEB packages in /var/cache/apt/archives and remove unnecessary packages by running:

```
sudo apt-get clean
```
```
sudo apt-get autoremove
```

Then, check for updates and install them
```
sudo apt-get update && sudo apt-get upgrade
```

Continue with step 11, leaving the chroot environment, unmount all file systems, reboot.

Btw: in case you have problems with the Internet connection in the chroot environment, copy your resolv.conf:

```
cp -L /etc/resolv.conf /mnt/etc/resolv.conf
```

Good luck!

---

