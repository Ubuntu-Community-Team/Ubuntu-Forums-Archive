---
title: "Green Lines After Boot"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by Raynman37 on 2010-01-15
Hey everyone, I just upgraded (yes, not fresh install which may be a step in the near future) to 9.10 and after I boot up every time I have green lines that look like the ubuntu boot splash screen loading bar.  I attached a screenshot so you can see what it looks like.  Has anyone seen this and/or know how to fix it?  Any help would be greatly appreciated.  Thanks!

---

### Post by KeLa on 2010-01-15
I had same kind of lines (only blue) on my screen after changing to new monitor.
But it was not only ubuntu problem it was same in windows box and that's because
i used belkin dvi kvm switch with those two computers.
When i connected both directly to new monitor (ubuntu with DVI and windows with vga connector) all those lines vanished and now everything is ok in my system.

This problem can also come with broken display cable.

---

### Post by kansasnoob on 2010-01-15
Welcome to bullet proof X.

[https://wiki.ubuntu.com/BulletProofX](https://wiki.ubuntu.com/BulletProofX)

More like bullet in the head to me!

---

### Post by Raynman37 on 2010-01-15
@Kela

I check on the windows side and there were no problems.  And I don't sound like I have the same setup you do so I'm not sure that's the problem.

@Kansasnoob:

Hey do I follow the directions in the implementation section?

---

### Post by Raynman37 on 2010-01-18
I tried following the directions in the implementation section, but there is no change.  Just a little more info, it seems to start when the loading splash screen is shown while booting up.  It also looks like it's got pieces of both the old splash and the new splash in it.  Anyone have problems with the boot loading screens or does anyone know if I can just reinstall that part or get rid of it?

---

### Post by presence1960 on 2010-01-19
> **Raynman37 said:**
> I tried following the directions in the implementation section, but there is no change.  Just a little more info, it seems to start when the loading splash screen is shown while booting up.  It also looks like it's got pieces of both the old splash and the new splash in it.  Anyone have problems with the boot loading screens or does anyone know if I can just reinstall that part or get rid of it?

welcome to the world of dist-upgrades. A clean install is the best way to go when changing to a new version. It may seem as if you are avoiding work by doing the dist-upgrade but as witnessed by the many threads in here about dist-upgrades the time spent fixing problems caused by the dist-upgrades is not worth the trouble.

You can make a file of your installed packages and then use that file to reinstall those packages on the clean install. The only packages not reinstalled are third party software not in repositories or packages you compiled from source. here is the link for that how-to: [http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

Also back up your home directory and restore that after the install as most of the packages' settings are stored there. If you have a separate /home partition I still would back that up just in case. When installing set that /home partition up by highlighting it and choosing Change. Then select filesystem in "use as", _**don't tick the format box**_ or you will be using that backup you made & select from the mount point drop down box "/home"

In the time you all that your dist-upgrade probably wouldn't have completed anyway.

---

### Post by Raynman37 on 2010-01-22
Solved with a fresh install...

---

