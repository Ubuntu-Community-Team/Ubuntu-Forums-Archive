---
title: "Turn gamepad into  keyboard"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by Yvan300 on 2009-08-10
Ok i want to play urban terror on my gamepad quite badly, but the problem is that urban terror does not support this. So i wanted to know if there is some kind of program that would turn my gamepad into a keyboard. There is xpadder for windows but i don't see anything native for linux, any suggestions?

---

### Post by synapsys on 2009-08-10
Check out **joy2key** in the repositories.

There is also **qjoypad** which is not in the repositories. Sourceforge?

---

### Post by Yvan300 on 2009-08-10
Thanks :D

Hmmm it says that i have no joystick support in the kernel :'(

---

### Post by wyrless2002 on 2009-10-25
I get the same thing.

> joy2key - reads joystick status and dispatches keyboard events
By Peter Amstutz (tetron@interreality.org)
This is free software under the GNU General Public License (GPL v2)
              (see COPYING in the joy2key archive)
You are welcome to use/modify this code, and please e-mail me
if anything cool comes of it!
Version: 1.6.1   Binary built on Oct 30 2007 at 08:10:20

Error opening /dev/js0!
Are you sure you have joystick support in your kernel?

It looks like joy2key is looking in /dev/js0 instead of /dev/input/js0, which is where jscalibrator shows my gamepad mounted.  Am I correct in this observation?  Has Ubuntu changed things up again?

---

### Post by jchammons on 2010-03-23
Check this out: [http://qjoypad.sourceforge.net/](http://qjoypad.sourceforge.net/)

---

