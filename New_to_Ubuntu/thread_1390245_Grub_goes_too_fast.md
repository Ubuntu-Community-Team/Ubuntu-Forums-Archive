---
title: "Grub goes too fast"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by Mariane on 2010-01-25
The list of bootup options goes by in a blink and does not give time to select anything but the first option. How can I slow it down please? 

Mariane

---

### Post by J V on 2010-01-25
if you change option it will stop the countdown, tried that yet?

*smug eye-roll*

---

### Post by Sir Jasper on 2010-01-25
Hi,

Installing StartUp-Manager using Synaptic is probably the easiest. Then you have some options including resetting your delay. I find 3 seconds is plenty.

My regards

Hope you had success with your headphone problem.

---

### Post by Pol18 on 2010-01-25
Mariane,

You cant open the grub file configuration like that sudo gedit /boot/grub/menu.lst
And modify the "timeout" line to "timeout 10"  is you wish a display of 10 seconds before kernel booting.

Pol

---

### Post by drs305 on 2010-01-25
I second the suggestion to use StartUp-Manager. It's a GUI tool that does a great job tweaking the Grub menu for Grub legacy installs.

Here is a link on how to install and run this app:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by philinux on 2010-01-25
> **Mariane said:**
> The list of bootup options goes by in a blink and does not give time to select anything but the first option. How can I slow it down please? 

Mariane

Just press the down arrow key and the timeout stops.

---

### Post by Paqman on 2010-01-25
> **Pol18 said:**
> 
You cant open the grub file configuration like that sudo gedit /boot/grub/menu.lst


Couple of points:
[LIST=1]
[*]The file you want to edit is at /etc/default/grub as of Karmic.
[*]For graphical apps like gedit, don't use "sudo". Use "gksu" instead. Sudo is for command line apps only.
[/LIST]

---

