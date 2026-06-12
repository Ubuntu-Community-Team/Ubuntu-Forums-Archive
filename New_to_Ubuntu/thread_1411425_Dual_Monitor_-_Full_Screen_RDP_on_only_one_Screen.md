---
title: "Dual Monitor - Full Screen RDP on only one Screen"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by adamkbell on 2010-02-19
I am running Ubuntu 9.10 64 bit with an NVidia 7300 LE Dual Monitor.  I am running twin view 1024x768 (I know it's huge but I like it)

I want to be able to run RDP to a Windows PC at 1024x768 full screen but I only want it full screen on 1 of the monitors.  Right now it spans both monitors in full screen.  If I set the session to 1024x768 I lose part of the start menu in the terminal service session.

I am using Gnome-RDP and Terminal Server Client.  Both give the same result.

Do I have to go to the separate X screen to do what I want?

Thanks,

Adam

---

### Post by HermanAB on 2010-02-19
rdesktop -g 50%

---

### Post by adamkbell on 2010-02-19
Thanks,

That gave me an idea:  1024x700 for my RDP session.  That way I get all of vertical.

Thank you,

Adam

---

### Post by Talar on 2010-05-06
Using "-D" to hide window decorations is also useful if you want to use the full size of a screen.

---

### Post by repairscr on 2012-12-27
rdesktop 192.168.0.4 -0 -D -g 1280x720

Change resolution as needed.

Was searching for how to do this and above didn't work but this did.

---

### Post by lisati on 2012-12-27
A lot can change in two years. It might be better to start a new thread.

---

