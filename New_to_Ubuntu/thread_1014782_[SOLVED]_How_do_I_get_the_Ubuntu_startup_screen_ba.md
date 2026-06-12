---
title: "[SOLVED] How do I get the Ubuntu startup screen back?"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by bwallum on 2008-12-18
Hi

I have a perfectly ok 32bit Intrepid running but I have lost the Ubuntu start up screen (with the filling progress bar) I prefer it (reassuring) to the current blank screen.

How do I get it back please?

---

### Post by talsemgeest on 2008-12-18
Install startup manager through synaptic.

---

### Post by PocketDog on 2008-12-18
Have you changed or moved your swap partition? [http://ggts.net/2008/05/13/reading-files-needed-to-boot/](http://ggts.net/2008/05/13/reading-files-needed-to-boot/)

---

### Post by Kellemora on 2008-12-18
HI BW

Are you saying you want to see the text of what is loading during boot-up instead of staring at a blank screen?????

I don't recall ever seeing just a bar like in some Doze programs?

But to show text during boot-up:
```
gksu gedit /boot/grub/menu.lst
```
Then remove the words "Quiet" and "Splash" from behind the word "ro" on your boot-up line.

This way you can see where some problems might appear as well.
Such as ATA being [DRDY].  All the lines should show [OK]!

TTUL
Gary

---

### Post by donkyhotay on 2008-12-18
> **Kellemora said:**
> HI BW

Are you saying you want to see the text of what is loading during boot-up instead of staring at a blank screen?????

I don't recall ever seeing just a bar like in some Doze programs?

But to show text during boot-up:
```
gksu gedit /boot/grub/menu.lst
```
Then remove the words "Quiet" and "Splash" from behind the word "ro" on your boot-up line.

This way you can see where some problems might appear as well.
Such as ATA being [DRDY].  All the lines should show [OK]!

TTUL
Gary

That works great if you want to know exactly what your system is doing on bootup (especially if your troubleshooting) but most non-techie linux users I've worked with prefer having a basic loading bar showing progress but not showing the scary-looking (to them) commands.

---

### Post by bwallum on 2008-12-18
Scary indeed, all I wanted was the Ubuntu splash and progress bar...which I now have thanks to talsemgeest and his advice to use startupmanager, just the job for us non-techie linux users. However it is really good to get slowly absorbed into it so thanks also go to Kellemora for the cli approach. It has helped me understand menu.lst lines a little better.

---

### Post by bwallum on 2008-12-18
no

---

### Post by talsemgeest on 2008-12-18
> **bwallum said:**
> Scary indeed, all I wanted was the Ubuntu splash and progress bar...which I now have thanks to talsemgeest and his advice to use startupmanager, just the job for us non-techie linux users. However it is really good to get slowly absorbed into it so thanks also go to Kellemora for the cli approach. It has helped me understand menu.lst lines a little better.
Cool, glad I could help. Also, sorry for such a short post, I was on windows at the time so I couldn't check exactly what you had to do.

But anyway, it is good to hear that you got it working.

---

