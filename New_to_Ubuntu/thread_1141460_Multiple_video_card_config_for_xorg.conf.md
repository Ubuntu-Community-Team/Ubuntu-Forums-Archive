---
title: "Multiple video card config for xorg.conf"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by alison.santiago on 2009-04-28
To clarify:

I have installed ubuntu to a portable 2.5" 7200 rpm drive. The install is used at home with a pc that can't have Linux installed (not my pc) and also at the computer labs at the university.

Both pc have different hardware configuration (home pc has Nvidia video card, university has an intel video card). The install has the Nvidia proprietary drivers installed (1.80).

Is there a way to configure it so that if I connect to the drive at home or the university, it can load the correct drivers automatically?  I am tired of having to edit the xorg.conf file all the time to get it working on the machine. There has to be an easier way than this.
:confused:

---

### Post by Elfy on 2009-04-28
You could use seperate xorg.conf's and change them in recovery mode from the prompt, would stop the need to edit each time.

This thread though does appear to deal with a similar issue

[Solution to: How to have multiple different Xorg.conf's]("http://ubuntuforums.org/showthread.php?t=669165")

---

