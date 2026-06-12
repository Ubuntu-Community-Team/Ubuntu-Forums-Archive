---
title: "help mouse not working"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by lanceps on 2009-06-24
Hi there i have been using ubuntu 8.10 for a while and the decided to install ubuntu 9.04 :( . sadly for some reason the unbuntu 9.04 has a problem with my mouse..... it moves and sometimes work.... i want to go back to my 8.10 but i dont have ubuntu 8.10 and i got only a kubuntu 8.10 that i downloaded sadly i been used to GNOME that i dont know what to do in KDE...

can anyone help me with the driver or can anyone tell me where i can get ubuntu 8.10

---

### Post by Gaweph on 2009-06-24
Hello,

Have you restarted since? or has it just happened?
SOmetimes stuff can get messed up during a large update e.g. from 8.10 ro 9.04

If you havent restarted then try that

---

### Post by lanceps on 2009-06-24
yup again and again a couple of time :(.... my mouse worked perfectly in 8.10

---

### Post by NightwishFan on 2009-06-24
If you still have 9.04 installed:

1) Make sure the mouse is set to move fast under mouse settings.

2) Shutdown, and remove mouse. If it is USB, then use another port. If it is ps/2 then make sure it is not damaged then reinsert it.

3) Start back up, does it work? If not, make sure your bios (the setup screen right when you hit the power button) has ps/2 enabled. If your mouse works at all then it is.

---

### Post by Gaweph on 2009-06-24
Googling it brings up some relevant information.
Some peopel say that maybe Xorg lost your mouse information.

Try doing:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

Which will backup your old XORG.

Then do:
sudo dpkg-reconfigure -pHigh xserver-xorg

---

### Post by Gaweph on 2009-06-24
Oh yeah, then try restarting X (CTRL + ALT + BACKSPACE i think)

---

### Post by NightwishFan on 2009-06-24
If you do not want to do commands, Ubuntu can fix X in recovery mode, (press esc when prompted before the splash screen loads). That I think will fix it if not anything else.

---

### Post by Gaweph on 2009-06-24
Even better :)

---

