---
title: "Question about moving from XP"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by Aglarelen on 2010-04-23
I did a search, but I couldn't find what I was looking for. Maybe that's because I phrased it wrong or something. Anyway, I'm having issues with XP and I'd like to try moving to Ubuntu. What I want to know is I have a few programs that run in XP, but I don't have the installation files anymore because they are old. Is there anyway for me to use them in Ubuntu from the XP installation of the programs? 

Thank you for your help.

---

### Post by mmalone21 on 2010-04-23
That would be a difficult task. Provide more details and I will see if I can help.

---

### Post by xumuk37 on 2010-04-23
I would try it in wine copying all XP regestry entries that indicate on this programs to wine regestry... it works same way regedit > export||import

---

### Post by oldsoundguy on 2010-04-23
Linux is not Windows .. you can't run Windows programs in Linux right out of the box .. you need to run them in Wine (an installable program available in the repositories) for instance (and lots do NOT run in Wine.)

---

### Post by wilee-nilee on 2010-04-23
> **Aglarelen said:**
> I did a search, but I couldn't find what I was looking for. Maybe that's because I phrased it wrong or something. Anyway, I'm having issues with XP and I'd like to try moving to Ubuntu. What I want to know is I have a few programs that run in XP, but I don't have the installation files anymore because they are old. Is there anyway for me to use them in Ubuntu from the XP installation of the programs? 

Thank you for your help.

If you need a copy of XP home and you have a ms key I have a legit download site I can post, if you look through my last couple of days of posts it is already available on the forum.

So if this can fix the XP problems then you might consider dual booting or running XP inside a virtual on Ubuntu.

---

### Post by 2hot6ft2 on 2010-04-23
Welcome to the forum.

Have you considered looking for linux alternatives to those apps.?
Linux alternatives to windows apps
[http://www.osalt.com/](http://www.osalt.com/)
[http://www.linux.org/apps/](http://www.linux.org/apps/)
[http://www.linuxappfinder.com/](http://www.linuxappfinder.com/)

Or search for the type of application in Synaptic
System > Administration > Synaptic Package Manager

Or tell us what they are and we can offer suggestions as to replacements.

---

### Post by Mark Phelps on 2010-04-25
> **Aglarelen said:**
> ... but I don't have the installation files anymore because they are old. Is there anyway for me to use them in Ubuntu from the XP installation of the programs? 
Basically -- NO.  Wine allows you to INSTALL MS Windows programs.  It is not a virtualization setup that will let you point to MS Windows programs installed in an MS Windows OS partition.

Also, the idea of copying registry entries is ludicrous.  There can be hundreds of registry entries associated with s single program -- entries spread across all four main parts of the collective registry (which is a bunch of files, not one file as it appears).

And finally, Wine does not run all Windows programs, only some.  If you go to the WineHQ site and look at their application compatibility database, you can see the ratings for the programs you want to run.  Anything rated silver or below is pretty much a waste of time.

---

### Post by TMKCodes on 2010-04-25
If the applications are windows only. Then look at wineHQ how well they work over wine, but try also looking for alternative programs.

---

### Post by Zintha on 2010-04-25
> **Mark Phelps said:**
> Basically -- NO.  Wine allows you to INSTALL MS Windows programs.  It is not a virtualization setup that will let you point to MS Windows programs installed in an MS Windows OS partition.

I run wow from my Windows Partition through Wine with less problems than most other people. No tweaking.

Steam too, and HL, and MW2 to a certain degree.
(along with a selection of older games)
Plus some other stuff thats passed my mind for now.

Seems to work fine unless i'm misunderstanding what you're saying.

edit: I reread it and i'm standing by my post. Its exactly what I do. Got 100gb XP OS (which I used to use) that I haven't got rid of and probably won't because it holds and runs (through wine) 90% of stuff I used before. I've installed only a couple of things using Wine, everything else is what was installed through XP and just accessed with Wine.

---

