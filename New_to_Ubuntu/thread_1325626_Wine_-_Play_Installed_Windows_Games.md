---
title: "Wine - Play Installed Windows Games?"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by UnknownFear on 2009-11-13
I have access to my Program Files from my Windows computer. Now, I was curious. Is it possible to install wine and play the already installed games on my Windows partition on Linux without installing them on Ubuntu? For instance, I go to host/Users/<name> and there are my Program Files, Music, etc. Could I not open up a game directory, ex: Counter-Strike and just run the .exe file and play it?

---

### Post by stderr on 2009-11-13
By default, no. Wine has its own separate registry for one thing; I'm sure there are many other issues. 

It's an interesting idea though. Have you tried using a virtual machine instead (e.g. VirtualBox)?

---

### Post by UnknownFear on 2009-11-13
> **stderr said:**
> By default, no. Wine has its own separate registry for one thing; I'm sure there are many other issues. 

It's an interesting idea though. Have you tried using a virtual machine instead (e.g. VirtualBox)?

No. Is it possible to even install VirtualBox and run Windows as is, meaning not having to re-install Windows? And that would let me run games via VirtualBox?

---

### Post by bacardiandwatermelon on 2009-11-13
Normally I would say no, but I think if you install steam in wine, then copy your whole steam directory to the wine steam directory, it may just save you reinstalling the whole thing. Mind you I have only tried this from windows to windows machines. You may get lucky :-)

---

### Post by NickJones on 2009-11-13
CounterStrike 1.6 works (with a CD key) just by clicking on the executable.

---

### Post by UnknownFear on 2009-11-13
I installed Counter-Strike 1.6 without a CD key. Can I still play it on Linux using wine by running it from Windows/Program Files?

---

### Post by durand on 2009-11-13
Easiest way to get an answer is to try it :)

---

### Post by stderr on 2009-11-13
Let us know how it goes.

> **UnknownFear said:**
> No. Is it possible to even install VirtualBox and run Windows as is, meaning not having to re-install Windows? And that would let me run games via VirtualBox?
Yes, you install VirtualBox, then you install Windows "on" VirtualBox, install your software and go. However, even with the new 3D acceleration capabilities of VirtualBox 3.0, it's much like Wine: some games work, some partially work, and some don't.

---

### Post by UnknownFear on 2009-11-14
> **stderr said:**
> Let us know how it goes.

Doesn't work lol

> 
Yes, you install VirtualBox, then you install Windows "on" VirtualBox, install your software and go. However, even with the new 3D acceleration capabilities of VirtualBox 3.0, it's much like Wine: some games work, some partially work, and some don't.

Ah, I'll just go on Vista if I want to play my PC games. Or I'll look around for some Linux FPS games.

---

