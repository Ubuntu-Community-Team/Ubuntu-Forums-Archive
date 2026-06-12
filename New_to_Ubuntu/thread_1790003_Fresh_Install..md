---
title: "Fresh Install."
date: 2011-06-24
forum: New to Ubuntu
---

### Post by Super-Dan on 2011-06-24
I am currently running a two drive set up.

I have a 40gb which is running Ubunutu and a 320gb that is holding my documents and shniz.

Can I copy my settings over when I do the new install?

How do I do this?

---

### Post by nomko on 2011-06-24
Best to do is a fresh install without copying any settings or configuration files. Any settings/config files left could be the cause of some file version conflicts or conflicts in differences of the default settings and your newer created settings. beside that, saving config files or settings files is a waste of time because you don't know if they gonna work again after the new installation. Best is to format the whole drive before install the new, fresh installation. 

Before doing this, be sure you have back-upped all your documents, movies, music, etc. NOT your settings/configuration files.

---

### Post by wolfen69 on 2011-06-24
> **nomko said:**
> 
Before doing this, be sure you have back-upped all your documents, movies, music, etc. **NOT your settings/configuration files.**

Please don't spread misinformation. Config files such as mozilla, opera, vlc, thunderbird work without a problem when transferred over. System settings *may* give some trouble, but application config files are no problem. Besides, even if it were a problem, simply deleting the file solves the problem, and a new one is generated. So it doesn't hurt anything.

---

### Post by nomko on 2011-06-24
> **wolfen69 said:**
> Please don't spread misinformation. Config files such as mozilla, opera, vlc, thunderbird work without a problem when transferred over. System settings *may* give some trouble, but application config files are no problem. Besides, even if it were a problem, simply deleting the file solves the problem, and a new one is generated. So it doesn't hurt anything.

Best is to forget the setting files and config files of the older Ubuntu version. There are always slight differences in 1 or 2 things between old and new program versions. BEst is to do a fresh install without saving the setting/config files of the older Ubuntu version.... No misinformation at all, just a tip.

---

### Post by grahammechanical on 2011-06-24
Is the 320gb drive mounted as /home or something else? If it is /home then a fresh install on / even with a format will not change any settings. But if /home is a folder on the 40gb drive then a fresh install will wipe out the hidden folders that contain application settings and your email and browser book marks and contacts

You can back up and restore Firefox and Evolution settings.

For Firefox go to help>troubleshooting Information and under the heading Application Basics click on the button called Open Containing folder and note the location of the folder on the system. Then make a copy of the folder. After the installation replace the new Firefox default folder with the old one and all your bookmarks and history will be back in place.

With Evolution you go to the file menu and click on backup Evolution Settings. This will create a file called evolution-backup.tar.gz which you can copy and use to restore you Evolution emails and contacts.

That all I can help you with.

Regards.

---

