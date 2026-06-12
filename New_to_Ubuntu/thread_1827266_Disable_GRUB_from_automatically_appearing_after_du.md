---
title: "Disable GRUB from automatically appearing after dual-boot install?"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by Brushstroke on 2011-08-17
Hi. I just installed Windows 7 to a small 40GB partition on my hard drive as I'll need it for a couple of my classes this semester. I also restored GRUB and got it to recognize Windows, so all potential emergencies of not being able to boot have been averted. Now I have an annoying problem. 

GRUB now appears every time I turn the computer on to give me a choice of what I want to boot into. I want it to autoboot into Ubuntu without the GRUB menu appearing each time unless I use the Shift key to make it appear. How do I do this?

---

### Post by Brushstroke on 2011-08-17
Solved the problem! 

For all other people on here who are dual-booting Ubuntu with a version of Windows, to have Ubuntu boot without GRUB showing up, edit this file in your favorite text editor: [I]/etc/grub.d/30_os-prober

[/I]Find this line. It should be line 28: 

```
  #if [ "x${found_other_os}" = "x" ] ; then
```Comment this line as I have here.

Next, scroll down to line 62: 

```
  #fi
```Again, comment this small line as shown here.

Close the file, run *sudo update-grub. *Now on a multi-boot system you won't have the GRUB menu coming up every time. It'll only come up if you hold the Shift key as normal. 

Solution thanks to: [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

