---
title: "BIG display problems"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by Kenny_C on 2009-03-31
Hi,
I'm relatively new to Linux, and I tried installing Ubuntu to my machine. It goes through the boot process fine, the loading screen works, but when the graphical login loads, all I get is a garbled screen, and I cannot make anything out, other than the fact that the colours change when I move the mouse. Does anyone have a clue what I can do to get it to work?

---

### Post by PacSci on 2009-03-31
You could try using Xfix. When GRUB appears at boot-up, select the option that says "recovery mode" for the latest kernel. When the recovery mode start up, select the "xfix" option. There are no guarantees, but it has fixed random X problems for me in the past.

---

### Post by aeiah on 2009-03-31
what graphics card do you have? is there anything unusual about your monitor?

---

### Post by Kenny_C on 2009-03-31
My PC uses onboard graphics, and that is an Intel 82865G graphics controller with 32-96MB shared RAM. The monitor is a Phillips CRT. I just tried Xubuntu, and it seems to work, its just Ubuntu.

---

### Post by dmillerw on 2009-03-31
Are you using Ubuntu 8.10?

Because I have the same integrated graphics as you, and Ubuntu 8.10, (specifically the included Compiz package) has problems with that type of graphics.

Ubuntu 8.04 works well though, and is the LTS version. (Long Term Support)

---

### Post by Street_Physicist on 2009-03-31
You could try setting the display details manually, the resolution and refresh rate for instance.
You will need to boot into a terminal so you can at least see what you are doing.
I'm not sure what is the easiest way to do this.  Try pressing ctrl+alt+F1 once you get to your garbled screen.  If that doesn't work I'll tell you how to get a root shell, but be careful with it.

I started writing a little description of how to do it, but I then I found this thead:
[http://ubuntuforums.org/showthread.php?t=83973]("http://ubuntuforums.org/showthread.php?t=83973")

you can probably skip the (sudo /etc/init.d/gdm stop) step, as you wont have it running.  But it won't hurt you to do it anyway.

so there are two methods in there, the first one will give you a sort of "graphical" step-by-step configuration, and the other method they have just involves you opening the configuration file and doing it manually.
I think your best bet will be to do it manually, but you can try both if you want.

---

### Post by Kenny_C on 2009-04-01
YES!! Problem solved. I don't know what exactly caused it, but it seemed to be because I installed it with WUBI. Thanks for your help.:D

---

