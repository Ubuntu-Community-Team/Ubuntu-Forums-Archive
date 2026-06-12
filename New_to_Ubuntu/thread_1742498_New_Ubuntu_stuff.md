---
title: "New Ubuntu stuff"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by domoappo on 2011-04-28
So a new version of Ubuntu has come out, and I have a few quick questions.

What is going to happen to all my files? Will the movies on my desktop still be there after I upgrade?

What is going to happen to all the things I downloaded from the Ubuntu Software Center? Am I going to have to reinstall everything?

I read that the document writer has changed. Will I still be able to access all my documents?

I use rythmbox, and this new version uses something else. What will happen? Will all my music be shifted to the new music player? Will I have to fill in all the music information again?

Are all my current preferences going to be transferred to this new version after I upgrade?

This is the first time I have upgraded since I first got Ubuntu (which has been fantastic!) so forgive me if I sound paranoid hahaha.

---

### Post by kaldor on 2011-04-28
My advice is to NOT upgrade via the updater. I strongly recommend doing a backup and reinstalling Ubuntu fresh and copying your files back over. The upgrading works fine for servers and some desktops, but overall might be a disaster.

Back up all files in your */home/username* directory. Pressing ctrl+H in the Home folder shows all the hidden files, which is where all the configurations are. If you don't want to copy over everything, copy over only the important stuff.

---

### Post by Finalfantasykid on 2011-04-28
From my experiences, upgrades have always gone smoothly, but you can always back up your files somewhere, either an external harddrive, or on another partition.

But to answer your questions:

> What is going to happen to all my files? Will the movies on my desktop still be there after I upgrade?
Those will still be there, same directory, untouched.

> What is going to happen to all the things I downloaded from the Ubuntu  Software Center? Am I going to have to reinstall everything?
All your installed programs should remain, although some will probably updated to their latest version.

> I read that the document writer has changed. Will I still be able to access all my documents?
LibreOffice has replaced OpenOffice.  All your office documents will still remain where they were on the filestystem, and since LibreOffice is a fork of OpenOffice, the file types are compatable.
> 
I use rythmbox, and this new version uses something else. What will  happen? Will all my music be shifted to the new music player? Will I  have to fill in all the music information again?
I'm not sure about this one.  If you don't like the new one though(Banshee), then you can always continue to use rhythmbox.

> Are all my current preferences going to be transferred to this new version after I upgrade?
The majority of preferences should remain the same, however given the nature of this upgrade(the addition of Unity), many of those preferences will not be relevant.  But things like program settings should remain the same.

I Hope that helped a little :)

---

### Post by Paqman on 2011-04-28
> **domoappo said:**
> 
I use rythmbox, and this new version uses something else. What will happen? Will all my music be shifted to the new music player? Will I have to fill in all the music information again?


The new player is Banshee, it will get installed when you upgrade. However, since you have Rhythmbox installed already, you'll also get the new version of Rhythmbox.

I think kaldor is being a little pessimistic. Upgrades used to be flaky, but these days they're pretty bombproof. I haven't had any trouble with one in years. He's right about taking a backup though, that's always a good idea before making any major changes.

---

### Post by garvinrick4 on 2011-04-28
If you have a lot of ppa's comment them out for time being before changing them to natty.
Can change anytime by inserting natty for maverick in /etc/apt/sources.list
Who knows if ppa's have a natty open yet???
[s]```

sudo apt-get update && sudo apt-get upgrade
``````
sudo apt-get install aptitude
``````
sudo sed -i 's/maverick/natty/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade 
```##All your settings and /home will stay the same but ALWAYS back up your personals as stated before.[/s]
###This works, Ubuntu says to use the Update Manager in GUI to dist-upgrade.

---

### Post by Paqman on 2011-04-29
> **garvinrick4 said:**
> If you have a lot of ppa's comment them out for time being before changing them to natty.


The upgrade process will do this automatically.

> **garvinrick4 said:**
> 
###This works, Ubuntu says to use the Update Manager in GUI to dist-upgrade.


With good reason. The correct method is not to change your sources.list, but to follow the instructions here:

[https://help.ubuntu.com/community/NattyUpgrades](https://help.ubuntu.com/community/NattyUpgrades)

Please bear in mind that you're posting the *Absolute Beginners* forum ;)

---

### Post by kaldor on 2011-04-29
> **Paqman said:**
> ...but these days they're pretty bombproof. 

Honestly?

---

### Post by garvinrick4 on 2011-04-29
> Please bear in mind that you're posting the *Absolute Beginners* forum
Point taken Paqman will be lots of new 11.04 users must be as simple and easy as possible.

---

### Post by Baldrick_NZ on 2011-04-29
For me, I have customised Ubuntu to the point where I have so much extra stuff that it would take hours to restore (by re-downloading and installing everything) if an upgrade of some type goes bad.

To this end, I have two partitions on my hard drive. One for the Ubuntu system files, and the other as purely as a home directory. So, in the event something does go wrong, I wouldn't loose any configuration settings when I reinstalled Ubuntu. To take further precaution, I downloaded 'File Backup Manager', which backs up all of my home drive and stores it on an external drive - just incase. Presently, I'm about to backup my usr/share folder, which has many downloaded apps in it as well.

My advise would not be to do an upgrade at this point in time, rather download the 11.04 liveCD, and try it first. If you like it, and your wifi/graphics/sound and anything else seems to work, then perhaps install it on a new partition of your hard drive. This would allow you to choose between versions in the meantime. When you are sure of which version you want, then you could then simply reclaim  hard drive space by removing the unwanted version. I hope this makes sense.

Undoubtedly 11.04 will have some teething bugs to sort out over the next couple of months, so as a newer user, you may wish to stick with a more stable version as your primary choice, and use 11.04 to play with when you wish.

---

### Post by rocka on 2011-04-29
I am having trouble with this upgrade [it seems to have broken my video system = pls see my other thread at [http://ubuntuforums.org/showthread.php?t=1742752](http://ubuntuforums.org/showthread.php?t=1742752) ].

Having said that, the last few upgrades before this one have all gone smoothly!

---

### Post by garvinrick4 on 2011-04-29
> ##All your settings and /home will stay the same but ALWAYS back up your personals as stated before.
What is not supported by Ubuntu Sef? I told user GUI using Update Manager was Ubuntu's recommendation. Always back up your personals is reasonable. Are you talking dist-upgrade by terminal is not recommended? Would really like to know Sef.

---

### Post by Paqman on 2011-04-30
> **kaldor said:**
> Honestly?

Yes, I've personally not had even the slightest glitch updating several machines over the last few versions. It's been rock solid for me for years.

---

### Post by domoappo on 2011-05-03
Zomg! It worked! This is awesome, everything was saved. 11.04 looks pretty cool too.

---

