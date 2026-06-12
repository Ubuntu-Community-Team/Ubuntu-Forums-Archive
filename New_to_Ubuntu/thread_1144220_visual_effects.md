---
title: "visual effects"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by captpicard12 on 2009-04-30
Hi, I've got an ATI RV350 9600 Mobility radeon graphics card, and i can't figure out how to turn on visual effects at all!!!!!!!!!  can anyone help me?  thanks!

---

### Post by gabrielshier on 2009-04-30
Hey captpicard12,
Well, there are a few ways we can solve that one. First, you need to see if your computer even recognized your graphic card. Go to System -> Preferences -> Apprearance . In this window go to the "Visual Effect" tab. There try to enable the full featured graphics ( "Extra- You'll need sungalsses :)" ). 
If that didn't work, give me the output. 
If it did, go to Applications and choose Add/Remove... . There search for compiz . Install it. Than use it's GUI. It's quiet simple. 
Any errors, just quote them to your replay.

---

### Post by Yvan300 on 2009-04-30
First you would want to make sure that you have your propiretry drivers. Those are the ones from ATI itself. If you are running jaunty, then most likely there will not be an available propiretry driver for your card. (the guys over at ati slack off). When they are installed download compiz destop effects through add/remove and after that just click on system, preferences and then compiz to customize all the effects. Cube included :)

---

### Post by Niniel on 2009-04-30
I have that same card in a notebook of mine, and it works very well with the open source drivers included in 9.04. I have selected "Normal" desktop effects and am not experiencing any problems with them, either graphically or performance wise (P4 M 2.4 GHz, 512 MB RAM). 

Do you have a fresh install or did you upgrade from a previous version? 

Oh, and to just turn on the effects, go to System/Appearance and then the last tab on that should be effects.

---

### Post by captpicard12 on 2009-05-01
i just upgraded from hardy heron.    WHen i try to hit normal it says "searching for available drivers", the screen flashes, and then it says "visual effects could not be enabled".  I can't find drivers anywhere for my card...  I searched google and heard something about something called "fgrlx".  What is that, and should i need it?

---

### Post by Niniel on 2009-05-01
That's the old proprietary ATI driver. It won't work anymore in 9.04.
Use the free "ati" driver. Make sure that all traces of old restricted drivers are removed. Then, with some more configuration, you can have desktop effects. [See here]("https://help.ubuntu.com/community/RadeonDriver") for a guide.

On my laptop with mobility 9600 card, desktop effects work without any configuration, in fact, my xorg.conf file is empty.

---

### Post by lavinog on 2009-05-01
> **Niniel said:**
> That's the old proprietary ATI driver. It won't work anymore in 9.04.
Use the free "ati" driver. Make sure that all traces of old restricted drivers are removed. Then, with some more configuration, you can have desktop effects. [See here]("https://help.ubuntu.com/community/RadeonDriver") for a guide.

On my laptop with mobility 9600 card, desktop effects work without any configuration, in fact, my xorg.conf file is empty.

The new proprietary driver discontinued support for older cards.

He may need to just delete the xorg.conf file.
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

---

### Post by captpicard12 on 2009-05-01
My X11 file is completely empty, yeah.  Does that mean i really should try deleting it?  I just wanna be careful before deleting anything important.

---

### Post by lavinog on 2009-05-01
actually the command i posted just renames the file, it doesn't delete it.
this way if things get worse you can just undo it:
```
sudo mv /etc/X11/xorg.conf.old /etc/X11/xorg.conf
```

---

### Post by lavinog on 2009-05-01
Which version of ubuntu are you using?
I think only jaunty has the version of radeon drivers that permit visual effects.

---

### Post by captpicard12 on 2009-05-02
I'm using jaunty

---

