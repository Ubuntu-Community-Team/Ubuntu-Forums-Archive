---
title: "ATI Display Driver"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by anotherdummhead on 2011-02-21
:confused: I don't really know what to do with this, i've downloaded display driver from ATI but it has .run extension, and i can't run the instalation, when i double click it or open in it the terminal, it just opens it like a document.

I didn't install any other driver, the system is pretty much relying on  drivers that Update manager downloaded. So how can i install this display driver ?

---

### Post by anotherdummhead on 2011-02-21
Additional : 

It's Radeon X1300, i've got CD that i got with this card, i don't know if i should run the instalation from this disc, 'cause i don't see if Linux is supported system for these drivers.

So...anyone ?

---

### Post by cascade9 on 2011-02-21
Radeon x1300 cards ATI drivers will not work with the current ubuntu releases, you can only use the open soruce driver.

---

### Post by anotherdummhead on 2011-02-21
Erm...any drivers would be good, can you show me how to use that open source driver ?

---

### Post by cascade9 on 2011-02-21
Its already installed. ;)

---

### Post by anotherdummhead on 2011-02-21
Well it looks like it's not, because even Frozen Throne is laggy and impossible to play, like i'm running Pentium 1 instead of Pentium 4 :D

When i'm moving my window, it leaves trails (if you know what i mean) like there's nothing installed.

---

### Post by mastablasta on 2011-02-21
opensource drivers are sort of reverse engineerd they might or might not work.
 
a user reported that for this card to work nicely you need to install 10.04 LTS and then add the bleeding edgers PPA (upgrade to latest version of opensource drivers). Ubuntu 10.10 has an issue with this card for some reason.

---

### Post by anotherdummhead on 2011-02-21
Oh that's nice, so pretty much with Xubuntu 10.10 i can't do anything, right ?

---

### Post by cascade9 on 2011-02-21
Its installed, its just not that fast. 

The newer versions of the open source driver are better. You can try them by doing this- 

Update Manager-> Settings-> Other Software

Add this 

```
ppa:xorg-edgers/ppa
```[FONT=monospace]
[/FONT]Then update.

*edit- A user had problems with that card, xorg-edgers and 10.10? mastablasta might have seen something I havent.....

If you've got a desktop, and have a free PCIe slot you could buy a cheap (supported) card. That would fix the problem. ;)

---

### Post by anotherdummhead on 2011-02-21
Hey all, i have to dissapoint you. 

I tried updateing my drivers, first, as you said, but nothing, it reported like i already have the latest drivers. Then i tried adding edgers as you said, but nothing. This problem is wide spread, i can't even watch a movie without flitching or choppy images, skype kept on crashing like crazy, while everything else seemed to be working fine, these basic things drove me nuts.

So unfortunately i'm back to XP now, but Xubuntu is really great, it's just pity that i have X1300 that is so poorly supported by the ubuntu...

Cheers all

---

### Post by mastablasta on 2011-02-22
any particular reason you chose Xubuntu? i would give a try with a regular ubuntu if you have enough ram (at least 512 MB). also install it side by side with winXP (not in wubi or ismilar because wubi alone can slow things down).
 
I say Ubuntu because i had graphics issues running live xubuntu on an aging notebook. X kept crashing. i decided to go Ubuntu (eventhough i had only 256RAM incl graphics card). it all works very nice now and very stable. also try 10.04. perhaps try it via LiveUSB before installing.

---

