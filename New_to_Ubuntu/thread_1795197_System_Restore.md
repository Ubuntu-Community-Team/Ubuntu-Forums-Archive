---
title: "System Restore??"
date: 2011-07-02
forum: New to Ubuntu
---

### Post by sijar85 on 2011-07-02
Is there any way to save your current system setup, so if you try some  change you can do a system restore as in windows, or like snapshot in  virtualbox so you can revert to a prior state??  This would be real  helpful because I have reinstalled my system a couple of times due to  mess ups. I am dual booting but have been spending most of my time here  in Linux Land, and my desktop is pretty much set, network is working,  software packages are installed and I would not like to have to redo it  all over again at this point!! Although I learn alot by fixing mistakes  it gets tiresome!. 

Thanks,[http://www.google.com]("http://www.google.com/")

---

### Post by Gryllida on 2011-07-02
There is a number of System backup and restore tools you can install and use: [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by spillage2 on 2011-07-02
Remastersys is what I think you are looking for. 

It will create a bootable cd from you current settings.

Spill.

---

### Post by amjjawad on 2011-07-02
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by s1baker on 2011-07-02
Everybody's situation is different I suppose, but here is what I did for what it's worth, I thought I would throw this in for your info. I use my computer for work and I could not have the system going down or some software that I depend on stop working in the middle of a job because of a software upgrade or system upgrade.
 So what I did was get another HD ( and I would recommend the same size and type of HD as the main one ) and I used clonezilla to make a cloned copy. They are both hooked up to the same ribbon. Periodically after I have made upgrades to my main HD and everything is working ok, I boot up my second ( cloned ) HD and upgrade it to the same state as the main HD, then I boot back into my main HD and continue. I only do this maybe once every week or two, and only after I am assured that the main HD is functioning ok.
 That said, a cloned HD duel booting on the same ribbon as it's "copied from" HD would need to have another UID generated for it and two files edited ( the grub file and the fstab file ) to reflect this new UID. ( I'm pretty much a nooby but the experts on this forum led me through it, and if I can do it anybody can )

---

### Post by stalkingwolf on 2011-07-02
have you tried the recovery mode and fix broken packages?

There is also the fix broken in synaptic.

---

