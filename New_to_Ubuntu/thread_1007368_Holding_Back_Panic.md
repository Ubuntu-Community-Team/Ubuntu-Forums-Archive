---
title: "Holding Back Panic"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by BarfBag on 2008-12-10
Note:  I dual boot Windows XP Home Edition and Ubuntu 8.10.  The problems mentioned below occurred in Windows, but this post does have to do with Ubuntu, as I will be using it to attempt to fix the problem.

I am trying my hardest to hold back panic.  My PC has been acting weird for a while, but being intensely occupied with work and school, I never had the time to figure out what was wrong.  Today, it has reached a new level.  (This was in Windows.)  I did a Google search and whenever I clicked on a link, it would open a new tab and take me to an advertisement page.  The same thing happened in Yahoo! and in all web browsers.  Shortly after, my PC randomly restarted.  I can not boot into Windows now without it restarting.  I went into the Ubuntu partition to try and back up my data, but the Windows partition will not mount.  It DID mount before, just yesterday as a matter of fact.  No changes have been made to the Ubuntu system since then.  Could I be experiencing a combination of spyware and hard drive failure?  How can I recover my data?  I have back-ups, but they are not up to date enough.

---

### Post by Titan8990 on 2008-12-10
Sounds like malware all the way. If you hit F5 prior to the Windows splash screen there is an option to disable automatic restart. This will force of BSOD from Windows and give you an error code you can work with. Most likely if it is in fact malware related you will be looking at a reformat after you recover your needed files.

You can't mount the Windows drive because windows did not flag it as not being used before shutting down. You can try mounting using the -force option but it could result in data loss. I personally have force mounted partitions a few times without any issues.

---

### Post by northern lights on 2008-12-10
Given the progression of your Windows failing, I'd say it's most likely related to malware. Virii rather than spyware, though.

What happens if you run ```
sudo mount -a
```from within Ubuntu?

---

### Post by Michael.Godawski on 2008-12-10
> I did a Google search and whenever I clicked on a link, it would open a new tab and take me to an advertisement page. The same thing happened in Yahoo! and in all web browsers. Shortly after, my PC randomly restarted. I can not boot into Windows now without it restarting.

This strange and suspicious behaviour looks like an spy-ware attack. Are you able to run an anti-virus scan in Windows?

> I went into the Ubuntu partition to try and back up my data, but the Windows partition will not mount. It DID mount before, just yesterday as a matter of fact. No changes have been made to the Ubuntu system since then. Could I be experiencing a combination of spyware and hard drive failure? How can I recover my data? I have back-ups, but they are not up to date enough.

So your Ubuntu is working? If yes please post the output of this terminal command to check your hard drive status:
```

sudo fdisk -l
```

If we get your Windows drive visible, you can try to check the drive in Ubuntu with the anti-virus application ClamaAV.

---

### Post by Captain_tux on 2008-12-10
> **BarfBag said:**
> 
I did a Google search and whenever I clicked on a link, it would open a new tab and take me to an advertisement page.  The same thing happened in Yahoo! and in all web browsers.

Definitely sounds like your browser has been hijacked. Run something like **AdAware** to try defeat it.

As to the rest of your post, I would venture a guess and say you've been hit with a virus and possibly more.

---

