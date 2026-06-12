---
title: "How do I..."
date: 2010-05-24
forum: New to Ubuntu
---

### Post by BrainWart on 2010-05-24
How would I change the grub so my friends can boot onto windows without needing to touch my computer?
I already had it to where I could boot onto Ubuntu and then I would need to use my arrow keys to select windows. Then I only needed to wait to get into windows again. I just upgraded and lost this.... Thanks again for all help!

---

### Post by Blümchen Blau on 2010-05-24
Ubuntu Version?
Grub Version?

---

### Post by birkopf on 2010-05-24
> **BrainWart said:**
> How would I change the grub so my friends can boot onto windows without needing to touch my computer?
I already had it to where I could boot onto Ubuntu and then I would need to use my arrow keys to select windows. Then I only needed to wait to get into windows again. I just upgraded and lost this.... Thanks again for all help!

You can install any boot manager and it should do the trick but GRUB is best. Thing with GRUB is that it likes to be installed at the end which means if you are going to have windows and linux on one drive - install first win than linux. 

If you already have both systms and dont want to start from begining - install again linux on linux (without formating) and GRUB will replace itself. 

Before - check man for options for GRUB. You may have disabled showing boot menu or something...

---

### Post by Zemblan on 2010-05-24
It is easy to alter which of the operating systems listed in grub boots as the default, it's a change of one number in a configuration file. However which configuration file needs editing depends on the version of grub you have. I'm going to assume that you have the most recent Ubuntu and therefore grub2.
If that's true you'll find instructions here: 
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

If you have an older version it will be a different file.

If the menu is hidden and you want it to be visible for a particular boot, then press and hold 'shift' while the boot is starting until the menu appears. To make menu appear every boot see : [http://forums.linuxmint.com/viewtopic.php?f=46&t=48231&p=278067](http://forums.linuxmint.com/viewtopic.php?f=46&t=48231&p=278067)

A overview of grub2's options and functions: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by kansasnoob on 2010-05-24
> **BrainWart said:**
> How would I change the grub so my friends can boot onto windows without needing to touch my computer?
I already had it to where I could boot onto Ubuntu and then I would need to use my arrow keys to select windows. Then I only needed to wait to get into windows again. I just upgraded and lost this.... Thanks again for all help!

Please boot into your Ubuntu and post the output of these commands:

```
lsb_release -a
```

```
grub-install -v && aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
```

Also, when you say, "I just upgraded and lost this", I'm not quite sure what you mean :confused:

You don't even see the boot menu now?

Or Windows is just no longer in the menu?

---

### Post by Chesamo on 2010-05-24
```
sudo update-grub
```
should cause Windows to at least *appear* in the boot list.

---

