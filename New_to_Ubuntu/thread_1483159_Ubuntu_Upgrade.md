---
title: "Ubuntu Upgrade?"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by mclizardman24 on 2010-05-14
Hi, everyone. I am running Ubuntu 9.10, and heard that tehre is a new one out. Do I have to request anotehr CD, or will Ubuntu aoutmatically upgrade, or something like that. I am really new to everything Linux and just got the 9.10 version. Thanks.

---

### Post by DougieFresh4U on 2010-05-14
> **mclizardman24 said:**
> Hi, everyone. I am running Ubuntu 9.10, and heard that tehre is a new one out. Do I have to request anotehr CD, or will Ubuntu aoutmatically upgrade, or something like that. I don't know, will it? lol, thank anyway.

You could open 'Update Manager' and see if it is offering upgrade
**System>Administration>Update Manager**

---

### Post by uRock on 2010-05-14
You can upgrade using the update manager by clicking the button highlighted in the screenshot. I would back up important data first.

---

### Post by mclizardman24 on 2010-05-14
> **uRock said:**
> You can upgrade using the update manager by clicking the button highlighted in the screenshot. I would back up important data first.
 Just to make sure, im running a dual boot (not a full partition) with windows 7. That won't affected it, right?

---

### Post by dalee on 2010-05-14
> **mclizardman24 said:**
> Just to make sure, im running a dual boot (not a full partition) with windows 7. That won't affected it, right?

Hi,

No it shouldn't affect your Win7 install.

Good Luck!

---

### Post by dtmbmw325i on 2010-05-14
Make sure you also run any updates sitting in the queue before running a distribution upgrade.  I think people have bad experiences when they don't.  These issues would only be with the linux side but would probably cause the need for a fresh install.

---

### Post by mclizardman24 on 2010-05-14
> **dalee said:**
> Hi,
 
No it shouldn't affect your Win7 install.
 
Good Luck!
 
Does it matter what user i'm in, because the user it gave me when i originally set it up was the same as windows 7, but i also created another, so it dosen't matter? I know I'm being paranoid, its just that i spent 200 dollars on windows, and i do not want it to die, lol.

---

### Post by bcbc on 2010-05-14
The wubi upgrade used to hang on 'Preparing memtest86' - it might still. If it does, click CTRL+C to break the loop... if you reboot you will destroy the ubuntu install.

When grub asks you where to install it, do not install it anywhere (all the check boxes should be blank e.g. sda, sda1 etc). It will give you a warning, but ignore it (if you're using wubi).

Note: there may be a help text suggesting you install grub everywhere if not sure - do not do this or it will break windows.

Edit: here is a link to a post containing a screenshot of the 'loop' I mentioned: [http://ubuntuforums.org/showthread.php?t=1467754](http://ubuntuforums.org/showthread.php?t=1467754)

Edit2: Definitely back up your data. My own experience with a test wubi install survived the initial upgrade but broke later with a kernel update.

---

### Post by mclizardman24 on 2010-05-14
> **bcbc said:**
> The wubi upgrade used to hang on 'Preparing memtest86' - it might still. If it does, click CTRL+C to break the loop... if you reboot you will destroy the ubuntu install.
 
When grub asks you where to install it, do not install it anywhere (all the check boxes should be blank e.g. sda, sda1 etc). It will give you a warning, but ignore it (if you're using wubi).
 
Note: there may be a help text suggesting you install grub everywhere if not sure - do not do this or it will break windows.
 
Edit: here is a link to a post containing a screenshot of the 'loop' I mentioned: [http://ubuntuforums.org/showthread.php?t=1467754](http://ubuntuforums.org/showthread.php?t=1467754)
 
Edit2: Definitely back up your data. My own experience with a test wubi install survived the initial upgrade but broke later with a kernel update.
 
 
Do you mean back up on Windows, and ubuntu, or just ubuntu, because i have NOTHING on my current linux. Also, i dont plan on using the wubi, just the upgrade manger. Also, how can i make sure everything else installs before the upgrade?

---

### Post by flyfishingphil on 2010-05-14
> **mclizardman24 said:**
> Hi, everyone. I am running Ubuntu 9.10, and heard that tehre is a new one out. Do I have to request anotehr CD, or will Ubuntu aoutmatically upgrade, or something like that. I am really new to everything Linux and just got the 9.10 version. Thanks.
FYI I went thru update manager, clicked on the upgrade and let it do it's thing. It took a couple of hours to go thru everything, with a good portion of that being updates and cleanups. It asked permission for a couple of things but that was all.

I have a dual boot with Vista. The only "changes" I noticed was it takes a little longer to get into the Vista side when I go there. It also seemed to take a while longer to get into things on the 'net until I did a little change in the Firefox settings. (Don't remember the steps but will browse thru my history and see if I can find that thread for you.)

---

### Post by bcbc on 2010-05-14
> **mclizardman24 said:**
> Do you mean back up on Windows, and ubuntu, or just ubuntu, because i have NOTHING on my current linux. Also, i dont plan on using the wubi, just the upgrade manger. Also, how can i make sure everything else installs before the upgrade?

You should always backup all your data. But before something like this you'd want to refresh your backups.

By "using wubi", I meant running ubuntu by installing within windows. Which is what you said you had done. I just wanted to make that clear as the advice was specific to a wubi install (sometimes posts are read out of context and I don't want a normal dual boot user not to install grub).

When you run update manager there are separate buttons for 'Upgrade' and 'Install updates'. So it should be clear whether you are updating 9.10 or upgrading.

---

