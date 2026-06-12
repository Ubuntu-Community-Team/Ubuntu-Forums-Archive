---
title: "Couple of questions"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by Dynamus on 2010-01-04
What's the best way to run windows games on Ubuntu, having a partition for windows or an emulator? I don't currently have windows on partition. What should I use to update my flash...driver/player?

---

### Post by lotharmat on 2010-01-04
You have a couple of options re: windows games.

wine

This is a way of installing and running windows games.

sun virtualbox

version 3 supports openGL

---

### Post by the8thstar on 2010-01-04
IMO, a native windows partition is the best choice.
The second best is a virtual machine with windows on it, although directX will not work well
The third option is running games through Wine (in the repos), but then again, it's not 100% fullproof.

---

### Post by Methuselah on 2010-01-04
If you love to play games that are meant for windows your best bet is to keep windows around in another partition and dual boot.

Wine will run windows programs but it might not run everything perfectly.
I run Simcity 4000 in Wine almost flawlessly but there are still some game demos I cannot install or have to tweak a lot to get running.

A emulator like Virtual Box is a program you run right within Ubuntu that starts up windows.
The advantage is that you do not have to reboot your computer in order to run the other operating system.
The disadvantage is that you don't always get 3D acceleration which is very important for games.

So the best bet, if you're an avid PC gamer is to keep windows around and dual boot.
Hope that helps!

---

### Post by MelDJ on 2010-01-04
> **the8thstar said:**
> IMO, a native windows partition is the best choice.
The second best is a virtual machine with windows on it, although directX will not work well
The third option is running games through Wine (in the repos), but then again, it's not 100% fullproof.

+1
the real deal is always the best.

---

### Post by JimInLakeland on 2010-01-04
> **methuselah said:**
> if you love to play games that are meant for windows your best bet is to keep windows around in another partition and dual boot.

Wine will run windows programs but it might not run everything perfectly.
I run simcity 4000 in wine almost flawlessly but there are still some game demos i cannot install or have to tweak a lot to get running.

A emulator like virtual box is a program you run right within ubuntu that starts up windows.
The advantage is that you do not have to reboot your computer in order to run the other operating system.
The disadvantage is that you don't always get 3d acceleration which is very important for games.

So the best bet, if you're an avid pc gamer is to keep windows around and dual boot.
Hope that helps!

+1

---

### Post by snowpine on 2010-01-04
To answer the second part of your question:

```
sudo apt-get install ubuntu-restricted-extras
```

will give you Flash, mp3 support, and lots of other yummy codecs. :)

---

### Post by Stormspace on 2010-01-04
> **Dynamus said:**
> What's the best way to run windows games on Ubuntu, having a partition for windows or an emulator? I don't currently have windows on partition. What should I use to update my flash...driver/player?

Using Wine works for many games, however as others said it's not perfect. I run Guild Wars via Wine and get about half the frame rate I would get running GW natively, but it's still playable. There are also some artifacts at times where a wild pixel will render funky and stretch across the screen. Other times distant objects will render as black until you get close to them. Panning around the screen fixes it. Also have some issues with Wine if the game requires a CD change while in play. (older games) 

Virtualbox may run games that don't require 3D acceleration OK, but again issues with games that require a CD change.

---

### Post by lavinog on 2010-01-04
I used to use linux for playing the games I play.  I wound up installing windows after a regression in the ati driver broke 3d support.  The next version of the driver fixed the issue, but the rapid changes in video support made linux gaming more frustrating.

---

### Post by gabo.cr on 2010-01-04
If you want to play games in 3D with high quality resolutions, I would use a dual boot.
It is funny how Win end up being used mostly just for the games.

---

