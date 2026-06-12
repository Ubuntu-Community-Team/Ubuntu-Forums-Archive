---
title: "Generic display size doesn't work anymore after XP update"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by kramer65 on 2010-03-16
Hello,


Yesterday my virtual XP installation in Virtualbox implemented an update when shutting down windows. When I started windows today (I really really need it for word and endnote) the screen didn't adjust anymore when I switched to fullscreen mode.

I tried uninstalling and reinstalling the guest additions, but that didn't work. I now have no clue what else I could try and I really need it..

Can anybody help me?!?

---

### Post by NickJones on 2010-03-16
Word and most of the Office suite is emulatable via Wine (sudo apt-get install wine) if you tell me what version you want I can tell you if it will work or not, and there is also OpenOffice already installed, and it works just as well as Microshaft Office in my opinion, you can even save into MS Office's *.doc format. 

As for EndNote, if you are running version 9, it works 100% in wine, and if you are using a version before that then you may have trouble getting some Add-ons to work.

Wine is a Windows Emulator and is a hell of a lot less resource hungry than running XP in a VirtualBox and saves heaps of HDD space.

---

### Post by kramer65 on 2010-03-16
Hi Nick, Thanks for the tips. I know that it should be possible, but I tried it many times and it simply doesn't work for me. Since I use things like automatic indexing and macros I simply cannot use OOo for my thesis (I use it for everything else though). I simply never got endnote to work in Ubuntu. I just tried again, but it just refuses to work.

So I am simply stuck to windows for the remainder of my thesis (I hope less than a month). I am now however, also stuck with a smaller screen than my actual screen. I hope somebody can help me out here..

---

### Post by kramer65 on 2010-03-17
Today I finally found the solution which I still wanted to share with anyone who might visit this thread afterwards.

The solution is simply Machine > Aut-resize guest display.

Sometimes things get dificult because you make them dificult. The answer is right there but you look over it.. :-)

---

