---
title: "mouse is not working properly in my friend's notebook (dell xps 1530)"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by fuser312 on 2009-01-19
its first time he has installed any linux (ubuntu 8.10 with every update), but its weired no mouse or touchpad is working properly in it. we reinstalled the system with a different installation cd but the problem still remains.
nothing much on dell page too.

---

### Post by u-foka on 2009-01-19
Hy!

What do you mean that the mouse not working "properly" it works, but slowly, or you can't touble tap to grab objects? or what is the problem really?!

And what dell model you installed it on?

---

### Post by fuser312 on 2009-01-19
its dell xps 1530, as i have told . 
and its like i have no control over mouse, response time is very high, 

and yes i am done with mouse settings with no help.

---

### Post by u-foka on 2009-01-19
I have googled a little and here is a possible solution for you, I have a vostro 1310 and have no problem with the touchpad so I can't test it for you

Here is the original thread:
[http://ubuntuforums.org/showthread.php?t=872153]("http://ubuntuforums.org/showthread.php?t=872153")

You have to edit your /boot/grub/menu.lst file to put "i8042.nomux=1" at the end of the line looks like this: "# defoptions=quiet splash" it's 86th line in mine... and yesss it's a comment and you have to keep it commented out, because this isn't a parameter directliy to grub, instead it tell's update-grub to add this options to all of the kernels you have... so you have to fire sudo update-grub in a terminal after the edit, and reboot

I hope that helps!

---

### Post by fuser312 on 2009-01-19
thanx u-foka, i will give it a try

---

