---
title: "Changed resolution, skewered screen"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by Erik M on 2010-01-11
I really hate being a newbie, hopefully I'll be only that...

Anyhow, I changed screen resolution (from 1280x to 1024x) and got a skewered screen for it. And no visible way back...

Could I get a hand in what to do with it?

---

### Post by JDShu on 2010-01-11
How did you change the screen resolution?

---

### Post by warfacegod on 2010-01-11
When grub loads, try using the header one number lower than the highest or try going into recovery mode for the newest kernel and telling it fix xsomething or other.

---

### Post by lupin492 on 2010-01-12
Once the PC presents you with the logon screen, instead of doing that, pres 'Ctrl+Alt+F1'.  You'll be in a text screen where you have to login.
Once there, type:
$ sudo dpkg-reconfigure xserver-xorg <enter>
(you'll be prompted (again) for your password here)

It should start a program that will enable you to reconfigure the xserver.  When options to change other parameters appear (mouse, keyboard, whatever), let them as they are.

A simpler one is to run (instead of the above command):
sudo dpkg-reconfigure -phigh xserver-xorg <enter>

It will set basic defaults again, and then you should be able to login (GUI) again.

After whichever you did, type 'Ctrl+Alt+F7' to get back to the GUI, for login.
Hope it helps. Regards,

---

### Post by Erik M on 2010-01-15
Many thanks everyone! I'm back up with it.

Now I just need to get my VLC to work properly again. It's very slow. Very.

---

