---
title: "Upgraded to 10.10: fglrx package install error &amp; Black screen at boot"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by mattismyname on 2010-10-10
I upgraded to 10.10 (from 10.04) today and am now getting a black screen at boot.  I try to switch to a virtual console and the video card changes modes, but does not display the VC.

I am able to boot into recovery mode from GRUB (every 10 tries or so).  I try to do a repair on broken packages, but the fglrx package errors out every time it tries to repair it.

So, I'm trying to figure out the answer to a few questions:

1) Why the black screen at startup (and why no VCs)?
2) Why does the GRUB menu only show up 1 out of 10 tries?
3) Why is the fglrx package not installing properly and is it related to the black screen?

I definitely should have tried a live CD before going for the full upgrade!

---

### Post by vlad1975 on 2010-10-10
Looks like you and i are having the same problem only diffrent you ded is a upgrade and i did a fresh install

---

### Post by mattismyname on 2010-10-10
Good to hear I'm not the only one.  If I see more people seeing something similar, I'll submit a bug to launchpad.

---

### Post by DougieFresh4U on 2010-10-10
I wasn't aware that 'fglrx' worked with Maverick:confused:

---

### Post by alphacrucis2 on 2010-10-10
> **DougieFresh4U said:**
> I wasn't aware that 'fglrx' worked with Maverick:confused:

AMD supplied Ubuntu with a pre release of Catalyst 10.10 which should work fine. I suspect that folks doing upgrades should completely remove the old fglrx before commencing the upgrade to Maveric. Then install the new version of fglrx via the Hardware drivers menu after the upgrade to Maverick is complete. The problem seems to be that the new fglrx does not get installed properly by the Ubuntu OS upgrade process. I have seen several reports of people getting errors on the part where it tries to upgrade fglrx.

---

### Post by alphacrucis2 on 2010-10-10
Just put my money where my mouth is.

1. Disable Desktop effects
2. Disable Fglrx via system administration hardware drivers.
3. sudo apt-get --purge remove fglrx
4. sudo do-release-upgrade
5. A couple of hours later it was done, asking me to reboot.
6. Reboot. 
7. Reenabled fglrx via system administration additional drivers (menu name has changed in MM) downloads and installs driver and tells you that you need to reboot. Before rebooting do step 8.
8. sudo aticonfig --initial -f
9. Reboot
10. Enable desktop effects.
11. All good.

Upgraded from 10.4  --- > 10.10

Graphics card is a HD 3400

---

### Post by DougieFresh4U on 2010-10-10
> **alphacrucis2 said:**
> AMD supplied Ubuntu with a pre release of Catalyst 10.10 which should work fine. I suspect that folks doing upgrades should completely remove the old fglrx before commencing the upgrade to Maveric. Then install the new version of fglrx via the Hardware drivers menu after the upgrade to Maverick is complete. The problem seems to be that the new fglrx does not get installed properly by the Ubuntu OS upgrade process. I have seen several reports of people getting errors on the part where it tries to upgrade fglrx.
Thanks.
I installed and rebooted and all was good. I am using the **2.6.36** kernel as well

---

### Post by mattismyname on 2010-10-11
@alphacrucis2:

```
root@host:~# sudo apt-get --purge remove fglrx
...
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing 'diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for unreadahead ...
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1).
```

Any ideas?

---

### Post by mitulv4u on 2010-10-11
I upgraded to 10.10 too with errors on grub and some other stuff. I am a novice.

Only thing i can tell you is I don't get my desktop wallpaper anymore. When I try change a theme or Desktop wallpaper, the file manager keeps on opening with several windows of "Opening File Manager" being opened and keeps on opening till I close the Desktop preferences window.



???? No clue what to do...

---

### Post by castironpants on 2010-10-11
I have tried every driver out there and I still can't enable desktop effects

---

### Post by mattismyname on 2010-10-11
@mitulv4u & @castironpants -- I think your issues are not related to this thread.

---

### Post by mattismyname on 2010-10-11
[deleted]

---

### Post by mattismyname on 2010-10-11
[deleted]

---

### Post by mattismyname on 2010-10-11
I found the solution over here: 

[http://www.linuxquestions.org/questions/linux-general-1/un-removable-package-661472/](http://www.linuxquestions.org/questions/linux-general-1/un-removable-package-661472/)

Use dpkg-divert --remove to remove the diversions it is complaining about.  Then remove the fglrx package.

---

### Post by pricorp on 2010-10-12
I had the same issue.

I found an quick solution to fix it:

- boot in safe mode
- select start in low grafic resolution
- once in gnome: system > administration > additional driver > install the FGLRX driver
- restart

HTH

---

### Post by fgr on 2010-10-13
same issue on Dell Studio 1747

Started once in rescue mode and repaired packages, after that I rebooted and installed once again the fglrx package.

works for me.

but for beginners this problem is not easy to solve. bad upate this time.

---

### Post by ashwinhgtx on 2010-10-13
I have a fresh install of 10.10 on a Dell Studio with Mobility Radeon HD5470. I haven't installed the fglrx package yet because I've been hearing about this blank screen bug. Right now I can't enable Desktop Effects as I haven't installed the driver yet.



 Will this bug affect me? I have some sensitive data on the laptop and I don't have a back up option. So I'd like to know if this would affect a fresh 10.10 install. I'll be installing the proprietary driver via the Additional Drivers utility.

---

### Post by castironpants on 2010-10-13
I acutally have the SAME graphics card and I've been having troubles. I'm back on Lucid right now. Granted, I'm a perfectionist and the fact that there's an updated OS and I'm not using it is getting under my skin so I'm probably going to try again tomorrow night but I can let you know how it works out.

---

