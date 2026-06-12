---
title: "backing up installed programs."
date: 2010-05-03
forum: New to Ubuntu
---

### Post by Kapser on 2010-05-03
I am going to be reinstalling ubuntu on my computer and I have many programs which i'll have to download again, so is there any way to back them up ? I mainly want to back up stuff like xbmc, wine and amarok so i dont have to download it again. 
I'll be backing them up on a pendrive, as my cd writer doesn't work, and i've already copied by *deb files from var/cache/apt/archives to my pendrive so APToncd won't work.

So how do you do it ?

Cheers

---

### Post by mörgæs on 2010-05-03
Are you sure that you want to back up (potentially) obsolete packages rather than downloading packages which are guaranteed to be new?

---

### Post by Kapser on 2010-05-03
Hmm.... Though you do have a point my internet connection i get charged a helluva lot for my downloads, plus can't i upgrade xbmc and wine..... ? (not a rhetorical question, i'm actually asking :confused: ?

---

### Post by mörgæs on 2010-05-03
I am not sure that I understand the question...

For any given package, this being Xbmc, Wine or another: If you have enabled the right repository, then the upgrades will be presented to you automatically.

---

### Post by dalee on 2010-05-03
Hi,

If you are doing a fresh, clean install, the best you can do is create a list with synaptic. System = Administration - Synaptic Package Manager - File - Generate package download script. Your best option might well be to do an upgrade. That way you will get the upgraded packages and the dependences met properly without breakage.

You can find your downloaded packages in /var/apt/cache/archives. But I would highly recommend you don't try and use those Karmic packages in your fresh new Lucid install. There are bound to version differences that will break things.

dalee

---

### Post by Kapser on 2010-05-04
> **dalee said:**
> Hi,

If you are doing a fresh, clean install, the best you can do is create a list with synaptic. System = Administration - Synaptic Package Manager - File - Generate package download script. Your best option might well be to do an upgrade. That way you will get the upgraded packages and the dependences met properly without breakage.

You can find your downloaded packages in /var/apt/cache/archives. But I would highly recommend you don't try and use those Karmic packages in your fresh new Lucid install. There are bound to version differences that will break things.

dalee
Though it is a fresh clean install i'll be using lucid on both (been using the release candidate, switching to the LTS and wiping out mint and xp). So im guessing the there wont be any differences/problems in the pacakges ?

---

