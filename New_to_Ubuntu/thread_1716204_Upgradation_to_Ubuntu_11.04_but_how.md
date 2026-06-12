---
title: "Upgradation to Ubuntu 11.04 but how ?"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by xptional on 2011-03-28
Hi :),

It will be my first upgradation, so I don't know what steps should be taken ? 
currently I am running Ubuntu 10.10, 

Can it be done only with internet connection?
Should I have to make backup ? but how ? and how to retrieve after installation ?
Should I have to install Ubuntu 11.04 with LiveCD?
or 
what measures should be taken, that will not disturb/erase my data on hard disk and other installed valuable programmes on the system.? 

Thanks in advance !

---

### Post by fabricator4 on 2011-03-28
> **xptional said:**
> Hi :),

It will be my first upgradation, so I don't know what steps should be taken ? 
currently I am running Ubuntu 10.10, 

Can it be done only with internet connection?
Should I have to make backup ? but how ? and how to retrieve after installation ?
Should I have to install Ubuntu 11.04 with LiveCD?
or 
what measures should be taken, that will not disturb/erase my data on hard disk and other installed valuable programmes on the system.? 

Thanks in advance !

Don't do anything yet, 11.04 is still in alpha testing.  It will shortly move to beta status.  Wait another month and it will be released, but I suggest you don't be in too much of a hurry to upgrade - let the dust settle first.  In other words, let them sort out any problems before you jump in.

When you want to upgrade you can do so with update manager.  Just go to software sources and and tell it to notify you of new releases.  You will then be offered the upgrade to 11.04.

I really suggest you back up your data before you do this.  Upgrades are not really guaranteed to work and things can and do go wrong.

Personally, I prefer to download the LiveCD for a new version, and do a fresh install from that.  This way, if anything does go wrong at least I've already got the LiveCD and don't have to download it again to re-install.  True, you then have to reload any software you've added to the system, but I still much prefer to do it this way.

Chris.

---

### Post by xptional on 2011-03-28
Thank you so much for your advices ... 

I should wait because it will be better than messing in problems.

---

### Post by uRock on 2011-03-28
> **fabricator4 said:**
> Don't do anything yet, 11.04 is still in alpha testing.  It will shortly move to beta status.  Wait another month and it will be released,
+1 to this. I also recommend doing a clean install using a LiveCD or USB, because it is much faster and there are some major changes in the GUI that may conflict with your current configurations.

---

### Post by oldfred on 2011-03-28
One more for clean installs, but if you have room on your hard drive add another root partition 10-20GB. Then you can install and test the new version while still keeping the old version. Then you know you have one working and can test at will with the other.

---

### Post by Dutch70 on 2011-03-28
I agree with what everyone else has said. Just want to add that you can also run it through Virtualbox or a usb stick if you want to try it out and help by reporting bugs.

---

### Post by cheetaux on 2011-03-28
Another thing to consider is to have a separate partition for your /home directory.  That way you can always safely do a clean install without worrying about the files in your /home directory.

---

### Post by xptional on 2011-03-29
I thank you all to help me to choose a path how to install and in which way. It will help when I try 11.04 version. Anyhow, I have enough space on my hard disk. 
Thanks again

---

### Post by Ecip on 2011-04-30
> **cheetaux said:**
> Another thing to consider is to have a separate partition for your /home directory.  That way you can always safely do a clean install without worrying about the files in your /home directory.

How the heck do ya do that?

---

### Post by fabricator4 on 2011-04-30
> **Ecip said:**
> How the heck do ya do that?

Well, you can change your current configuration [like this]("http://ubuntuforums.org/showthread.php?p=9141619") or you can set it up that way when you install using the manual partition option.  It pays to do a little reading and understand it before acutally doing a manual install.

Chris

---

