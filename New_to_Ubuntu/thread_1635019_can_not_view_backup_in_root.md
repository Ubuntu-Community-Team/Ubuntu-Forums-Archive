---
title: "can not view backup in root?"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by gmenfan83 on 2010-12-01
ok so i made a backup of my ubuntu system and the when i try to view my backup to make sure it is in facdt there and backed up properly i go to filesystem then go to my root folder and when i go to get inside the root folder i get a prompt telling me i dont have permissions....so then i open up terminal to grant myself permission with sudo su and even after doing so and granting myself permission i cant view my root folder?

---

### Post by philinux on 2010-12-01
> **gmenfan83 said:**
> ok so i made a backup of my ubuntu system and the when i try to view my backup to make sure it is in facdt there and backed up properly i go to filesystem then go to my root folder and when i go to get inside the root folder i get a prompt telling me i dont have permissions....so then i open up terminal to grant myself permission with sudo su and even after doing so and granting myself permission i cant view my root folder?

Open a terminal and use this. Be careful as always.

```
gksudo nautilus
```

---

### Post by gmenfan83 on 2010-12-01
> **philinux said:**
> Open a terminal and use this. Be careful as always.

```
gksudo nautilus
```
awesome thanks worked like a charm......i have another question and i dont mean to kind of hijack my own thread but is there like a set place where i can get a list of all these commands?like a command dictionary or something?

---

### Post by philinux on 2010-12-01
> **gmenfan83 said:**
> awesome thanks worked like a charm......i have another question and i dont mean to kind of hijack my own thread but is there like a set place where i can get a list of all these commands?like a command dictionary or something?

[http://ubuntuguide.org/wiki/Ubuntu:Maverick](http://ubuntuguide.org/wiki/Ubuntu:Maverick)

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

There is loads of resource material out there...

Try searching for  "ubuntu guide" or "linux tips" etc etc.

---

### Post by QLee on 2010-12-01
And gmenfan83, don't forget to consider that, if the hard drive fails for some reason or your Ubuntu partition gets completely trashed beyond repair, that backup won't be available to you.

---

### Post by gmenfan83 on 2010-12-01
> **QLee said:**
> And gmenfan83, don't forget to consider that, if the hard drive fails for some reason or your Ubuntu partition gets completely trashed beyond repair, that backup won't be available to you.
so in the event that happens i should create what you would call a live disk?..just transfer my backup to a disk or maybe even flash drive that way if my backup does get hosed i can recover and bootup from the disk or flash drive?.....if this is the case can i use any standard blank disk and just make sure it has enough space?

---

### Post by philinux on 2010-12-01
> **gmenfan83 said:**
> so in the event that happens i should create what you would call a live disk?..just transfer my backup to a disk or maybe even flash drive that way if my backup does get hosed i can recover and bootup from the disk or flash drive?.....if this is the case can i use any standard blank disk and just make sure it has enough space?

Yes backup important data to a usb stick/external drive or DVD.

I never backup the system only my data files. Pics vids document music etc.

---

### Post by gmenfan83 on 2010-12-01
> **philinux said:**
> Yes backup important data to a usb stick/external drive or DVD.

I never backup the system only my data files. Pics vids document music etc.
makes sense to only backup data since system download is obtainable for free and data is precious

---

### Post by philinux on 2010-12-01
> **gmenfan83 said:**
> makes sense to only backup data since system download is obtainable for free and data is precious

I also have /home on it's own partition so a reinstall is pretty fast and pain free.

---

### Post by gmenfan83 on 2010-12-01
> **philinux said:**
> I also have /home on it's own partition so a reinstall is pretty fast and pain free.
so then home saves all your system files so you have that partition there and in the event something happens you just boot from that home partition ..am i understanding properly......

---

### Post by QLee on 2010-12-01
[QUOTE=gmenfan83]so in the event that happens i should create what you would call a live disk?..just transfer my backup to a disk or maybe even flash drive that way if my backup does get hosed i can recover and bootup from the disk or flash drive?.....if this is the case can i use any standard blank disk and just make sure it has enough space?[/QUOTE]
Well, answering this question depends on what you mean by the term "backup" and how you originally intended to use that backup you created.

If you just have a copy of the filesystem tree, don't assume you're going to be able to copy it somewhere and have it be bootable. If you did that to a CD it wouldn't fit, and even if it fit, it wouldn't be bootable. Just copying to a flash drive wouldn't be bootable either. In addition, if not using a Linux partition type on your backup medium, permissions would likely give you grief.

I also use a separate /home like philinux, but we are both experienced, power users, able to deal with things on the fly when errors are encountered during a restoration.

There are lots of backup solutions, among them, 

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

Some users like to use, remastersys:
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)
and
[http://psychocats.net/ubuntu/remastersys](http://psychocats.net/ubuntu/remastersys)

...and probably some I haven't mentioned but one of their proponents will probably reply and explain. There are even third-party applications.

Do some careful study and consideration now, before you have a problem.

---

### Post by gmenfan83 on 2010-12-01
thank you both for your help and info it is much appreciated and your patience as i am obviously new to this

---

### Post by philinux on 2010-12-01
> **gmenfan83 said:**
> so then home saves all your system files so you have that partition there and in the event something happens you just boot from that home partition ..am i understanding properly......

No sorry. The home partition only contains program configuration file which are mainly small text files. Except apps like your browser and email config folders.

If you open Places > Home Folder and then press ctrl h you will see all the hidden config folders that are preceded with a "."

The home partition is not bootable.

When you reinstall and say install a program that was previously installed it picks up it's config from /home. Also any desktop customisations you've made like panels and themes will be preserved.

---

### Post by gmenfan83 on 2010-12-01
> **philinux said:**
> No sorry. The home partition only contains program configuration file which are mainly small text files. Except apps like your browser and email config folders.

If you open Places > Home Folder and then press ctrl h you will see all the hidden config folders that are preceded with a "."

The home partition is not bootable.

When you reinstall and say install a program that was previously installed it picks up it's config from /home. Also any desktop customisations you've made like panels and themes will be preserved.

I see so since it saves configuration so if and when you reinstall it will auto configure since it is saved .....I think I am understanding properly .....I have learned so much from one thread :P

---

### Post by QLee on 2010-12-01
[QUOTE=gmenfan83]I see so since it saves configuration so if and when you reinstall it will auto configure since it is saved .....I think I am understanding properly .....I have learned so much from one thread :P[/QUOTE]

Well, to help make your understanding a bit more complete, I hope.

If you managed to have a separate /home partition and managed to get it mounted correctly and not formatted over during the install process (something inexperienced users often have trouble doing), then you could have your personalised user settings for the applications preserved, assuming you'd used the same username for the new install.

Have some more documentation:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
[http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html](http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html)

gmenfan83, you will benefit greatly if you learn to use the search function of the forum, it can save a lot of time waiting for answers as most questions from inexperienced users have been asked and answered many times.

 [Edit] ...and since I'm throwing out links, have a look at the first post in this one, it's a sticky at the top of the forum:
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

