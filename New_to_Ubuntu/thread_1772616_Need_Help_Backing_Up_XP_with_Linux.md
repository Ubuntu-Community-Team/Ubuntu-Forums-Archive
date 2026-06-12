---
title: "Need Help Backing Up XP with Linux"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by k33bz on 2011-05-31
Ok, here is the scenerio. I am working on a buddy of mine's XP Box. His system is so corrupted and filled with Viruses. He does not want to lose all his programs he has installed, some of them he borrowed from other people so he can install. As well as the discs he does have he does not want to go through all that again.

Normally I just back up documents and stuff like that. I have never tried to back up system settings, programs, and personal files. Does anyone know how I could do this. 

I will be using my Laptop (running Ubuntu 10.04) to back up his files onto, wipe and reload his computer with a copy of XP and his license key.

Is it as simple as backing up Program Files, or is there more to it?

---

### Post by rbishop on 2011-05-31
Most programs on Windows have not only the data but also Registry keys.  As for digging through the registry that is a tough one, cause typically they have multiple entries and in different areas of the registry.

I have tried a couple of different programs, coping the Program Folder to a new machine and it hasn't worked.

---

### Post by MartyBuntu on 2011-05-31
> **k33bz said:**
> 
Is it as simple as backing up Program Files, or is there more to it?

The machine is infected. You risk possibly carrying over any malware trying to backup registry settings.

He may need a new, clean install. Remind him of the importance of good maintenance and regular drive imaging.

---

### Post by Mark Phelps on 2011-05-31
> **k33bz said:**
> Is it as simple as backing up Program Files, or is there more to it?

There is a LOT more to it.

If you want to try an experiment, LapLink used to make a product that allowed you to "migrate" from one PC to another.  That attempts to find everything associated with an app and save it off.  I think it was called PC Mover, or something like that.

If that's still available, you could try using that -- but be warned that you're likely to migrate the malware as well.

---

### Post by dFlyer on 2011-05-31
Have you cleaned all the virus/malware from the computer before you attempt to back it up. If not you risk transferring it all back.

---

### Post by Chembletek on 2011-05-31
Try cleaning the computer up first. I recommend Malwarebytes. If you have a friend who works at staples you can ask them to log into the norton website and get a cleaning tool from there free. I did that and cleaned up my windows partition like no viruses ever happened.

---

### Post by SeijiSensei on 2011-06-01
Most modern Windows programs cannot simply be copied from one machine to another.  They insert a variety of keys into the Registry during installation that must be present to run.  Unfortunately you *absolutely cannot* copy the Registry from an infected machine as that's where most malware hides out.  Your friend needs to bite the bullet and start with a clean installation, or try Linux instead.  Perhaps when you show him how easy it is to install software from the repositories he might be impressed.

---

### Post by k33bz on 2011-06-01
Sorry to say he is windows all the way. Unlike me, I view Windows as evil, lol. IDK that is just me. But he loves windows, so he would be staying with it.

I will be talking to him tomorrow and letting him know I wont be able to save his programs, that those will have to be re-installed. But first I need to make sure the RAM is not the culprit as well for his BSOD.

---

