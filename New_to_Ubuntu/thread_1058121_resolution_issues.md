---
title: "resolution issues"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by supertappy on 2009-02-02
hi

i have finally managed to get ubuntu 8.10 installed and it is a bit exciting :)

a problem i have is the biggest screen resoulution i can get is limited to

896 by 600

meaning screens that you cant see the buttons on the bottom on screens

is there some way i can tweak the resolution?

jt

---

### Post by overdrank on 2009-02-02
> **supertappy said:**
> hi
i have finally managed to get ubuntu 8.10 installed and it is a bit exciting :)
a problem i have is the biggest screen resoulution i can get is limited to

896 by 600
meaning screens that you cant see the buttons on the bottom on
is there some way i can tweak the resolution?
jt

Hi and welcome, could you tell us some system specs like the graphics card?

You may try and boot into recovery mode, which is usually the second choice from the grub. There you can use the xfix option to hopefully correct the graphics issues. Once the xfix is complete you should be given a option to boot normally.

---

### Post by rggavubt on 2009-02-02
If you have a nVidia card enter nvidia-settings in terminal and set resolution to what you want and then save and it should stick.

---

### Post by RedRat on 2009-02-02
> **rggavubt said:**
> If you have a nVidia card enter nvidia-settings in terminal and set resolution to what you want and then save and it should stick.

you might have to download nvidia-settings, unless things have changed in 8.10 and it is included. In 8.04, I had to use apt-get to download and install it. Try looking at Synaptic Package Manager, it might be there. Good Luck!

Resolution issues are the biggest annoyance in Ubuntu.

---

### Post by supertappy on 2009-02-04
the card is an ati radeon 4850

however i negletced to mention this is all installed in MS virtual pc 7, so presumably the virtual pc can't see the video card...also the sound doesn't work...

I've been looking for the virtual machine additions to install and hopefully help things in the vm but obviously a .msi file means nothing to ubuntu

jt

---

### Post by HavocXphere on 2009-02-04
> **supertappy said:**
> however i negletced to mention this is all installed in MS virtual pc 7t
There is your problem. You'll struggle with gfx issues in that since you can't install ati drivers while emulating. The OS doesn't get direct access to the gfx hardware due to the emulation layer.

---

### Post by RedRat on 2009-02-04
You know, this a good example of people here not providing enough information about their system. Yes, I know this is for newbies, but perhaps the moderators of the forum could put some kind notice that when you come here to ask a question, please identify exactly what is your system. 

I note that here supertappy came and asked about video resolution problems. Well and good, that is what the forum is for. A not insignificant number of helpful people jumped in but supertappy never mentioned ***_what kind of card he had_*** or how he was running Ubuntu (emulation mode). Only a day later do we find out that it is an ATI Radeon and he was in emualtion mode! Please, please, if you want help, give us information so that we don't waste your time or, more importantly, ours!

---

