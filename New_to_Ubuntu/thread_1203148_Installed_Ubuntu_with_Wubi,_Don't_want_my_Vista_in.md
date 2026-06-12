---
title: "Installed Ubuntu with Wubi, Don't want my Vista install anymore"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by Fableflame on 2009-07-03
This has been my first experience with a Linux OS and I've liked it so far. However, I installed it with Wubi. At first I only allocated it the space that it needed to be installed. I soon ran out of room, after downloading videos, mp3s and such, so I had a friend walk me through creating a new virtual drive that was bigger. It seems I'm running out of room again. I'd love to get rid of my Vista install altogether so that I'll have plenty of room on Ubuntu. If I uninstall Vista now, since I'm using Ubuntu with Wubi, will that get rid of my Ubuntu install? How can I take off Vista, and allocate all of my partition to Ubuntu?

Thanks in advance.

---

### Post by snakeman21 on 2009-07-03
You've got a few options.  Probably the simplest is to download a live version of gparted.  This is a utility for editing drive partitions.  (gparted stands for Gnome PARTition EDitor)  Anyways, you download the bootable version and burn it to a cd.  You then boot your computer with the cd inserted, and instead of booting from your hard drive, it boots from the CD.  Use the utility to delete your Vista partition, then resize your Ubuntu partition to use the freed space. Click Apply, wait for it to finish, and Voila:  You have only Ubuntu.  Note:  Even though you should be able to do this without losing data, it is ALWAYS a good idea to pack up your data before you mess with the partitions in case something goes wrong.  

To download gparted bootable, follow [THIS LINK]("http://sourceforge.net/projects/gparted/files/").  Download the latest stable release.  It will be in a ZIP file.  Extract it, and burn the iso to a cd.

You can also burn a Live Ubuntu CD and use gparted from there to do it, but this way takes MUCH longer to download.

Good luck, and let us know if you need any more help.

---

### Post by earthpigg on 2009-07-03
i don't think that will work if he installed via _**wubi**_, as i dont believe he has an ubuntu partition.

---

### Post by earthpigg on 2009-07-03
here ya go chief, your answer is in the ubuntu wiki:

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

i've never tried it myself so can't give specific advice, but that should get you started.

---

### Post by snakeman21 on 2009-07-03
> **earthpigg said:**
> i don't think that will work if he installed via _**wubi**_, as i dont believe he has an ubuntu partition.

oh! I apologize.  I never used Wubi, so I don't know much about it.  *goes to look at the details of Wubi*

---

### Post by snakeman21 on 2009-07-03
ah, I see now why that wouldn't work.  Sorry everyone!

---

### Post by zwdev on 2009-07-03
Hi

The best option would be to backup all your precious files to some external media and do a clean Ubuntu installation. This way you will have gotten rid of Vista and you will enjoy better performance too. Have fun.

---

### Post by steveneddy on 2009-07-03
> **zwdev said:**
> Hi

The best option would be to backup all your precious files to some external media and **do a clean Ubuntu installation**. This way you will have gotten rid of Vista and you will enjoy better performance too. Have fun.

+1

agree here.

Backup import data and do a complete clean reinstall for optimum performance and reliability.

---

### Post by snakeman21 on 2009-07-03
+1  

Clean ubuntu installs are incredibly easy.  Everything is graphical, unless you choose to use the alternate installer, and it's so simple my grandma could do it.  Also, when you install from a live CD, you can play games or surf the web.... While Ubuntu is installing to your hard drive!  And people say Ubuntu is an inferior, primitive operating system... then nerve...

Ubuntu will run a lot faster on a clean install, too.  After reading a little about Wubi (interesting idea) I realized that even though you're running ubuntu, Vista is still running in the background.  Vista is NOT what you would call efficient... It needs a gig of RAM *just to run idly.*  When Ubuntu has full reign of your system, you'll enjoy much faster processing.

Good luck and happy Ubuntu-ing :)

---

### Post by Fableflame on 2009-07-03
I followed the link and it talked about resizing partitions. I'm really not that computer savvy, and I don't know much about partitions and swaps and stuff, but I know that the reason I installed Ubuntu via Wubi is because my windows partition wouldn't resize when I tried it the other way, so I had no other choice but to install it 'inside' Windows.
Can I go into the Ubuntu that I already have installed and use Gparted to resize the partition? Or will it refuse to resize like before?

---

### Post by halitech on 2009-07-03
if you are 100% sure you want to get rid of vista completely, just boot the Ubuntu install disk and tell it to use the entire disk to install too. That way you don't need to resize anything at all.

---

### Post by Old_Grey_Wolf on 2009-07-03
> **halitech said:**
> if you are 100% sure you want to get rid of vista completely, just boot the Ubuntu install disk and tell it to use the entire disk to install too. That way you don't need to resize anything at all.

I agree with this advice; however, as stated before by others, back up (copy) your videos, mp3's, and such, that you want to keep to some removable storage device. The "use entire disk" option will wipe out everything on your disk.

---

### Post by Fableflame on 2009-07-03
> **halitech said:**
> if you are 100% sure you want to get rid of vista completely, just boot the Ubuntu install disk and tell it to use the entire disk to install too. That way you don't need to resize anything at all.

> **Old_Gray_Wolf said:**
> I agree with this advice; however, as stated before by others, back up (copy) your videos, mp3's, and such, that you want to keep to some removable storage device. The "use entire disk" option will wipe out everything on your disk.

I think this is what I'll do. My computer isn't suited for Vista, even though that is the OS that came with it, so I don't ever use it because it's slow. I'll try this when I get back to my computer Sunday.

Thanks for all the replies, I'll report back hopefully after Vista is gone :D

---

### Post by philcamlin on 2009-07-03
you cant get rid of vista wwith wubu just clean install and it will be faster too!!

---

### Post by earthpigg on 2009-07-03
one other thing you may want to back up is your /home/(username) folder, _**including the hidden files.**_

these are the settings for individual applications: firefox, pidgin, save-files for games, etc.

after you get ubuntu installed again, selectively copy over the hidden folders for programs you want back the way they where on your old install.

note that pidgin's settings are in .purple and a couple other folders with 'purple' in the name... i think .libpurple is one or something like that.

---

### Post by philcamlin on 2009-07-03
> **earthpigg said:**
> one other thing you may want to back up is your /home/(username) folder, _**including the hidden files.**_

these are the settings for individual applications: firefox, pidgin, save-files for games, etc.

after you get ubuntu installed again, selectively copy over the hidden folders for programs you want back the way they where on your old install.

note that pidgin's settings are in .purple and a couple other folders with 'purple' in the name... i think .libpurple is one or something like that.

i dont think that would work because of permissions 

i tried that once but it didnt work :mad:

maybe you can i just didnt realize it

---

### Post by earthpigg on 2009-07-03
> **philcamlin said:**
> i dont think that would work because of permissions 

i tried that once but it didnt work :mad:

maybe you can i just didnt realize it

ive done it a couple times, but not using wubi.

i do clean installs every 6 months, and selectively restore application settings using that method.

---

### Post by Fableflame on 2009-07-03
So if I boot up the Live CD and just select to use all of the harddrive it should automatically write over my Windows partition, without having to bother with a resize?

---

### Post by snakeman21 on 2009-07-03
> **Fableflame said:**
> So if I boot up the Live CD and just select to use all of the harddrive it should automatically write over my Windows partition, without having to bother with a resize?

Yes.  The default option is to partition, but just check the box labeled "Guided - Used Entire Disk."  Ubuntu will wipe everything on your hard drive and install itself.  Say goodbye to bloated, slow Vista, and say hello to a REAL OS that works!

---

### Post by theozzlives on 2009-07-03
> **snakeman21 said:**
> Yes.  The default option is to partition, but just check the box labeled "Guided - Used Entire Disk."  Ubuntu will wipe everything on your hard drive and install itself.  Say goodbye to bloated, slow Vista, and say hello to a REAL OS that works!

I'm a believer of manual and create a third /home partition.

---

### Post by snakeman21 on 2009-07-03
> **theozzlives said:**
> I'm a believer of manual and create a third /home partition.

So am I, but is sounds like he was having trouble partitioning, so I figured simpler would be better for now

---

### Post by RayArdia on 2009-07-07
> **Fableflame said:**
> I followed the link and it talked about resizing partitions. I'm really not that computer savvy, and I don't know much about partitions and swaps and stuff, but I know that the reason I installed Ubuntu via Wubi is because my windows partition wouldn't resize when I tried it the other way, so I had no other choice but to install it 'inside' Windows.
Can I go into the Ubuntu that I already have installed and use Gparted to resize the partition? Or will it refuse to resize like before?
I've the same problem - ie how to COMPLETELY remove vista. Have downloaded and burned the latest 8.04.2 Hardy (tried Jaunty briefly, but ran into some problems!) so want to use a version I trust on this new Acer5735 laptop. Config is 4GB RAM, 250GB HDD.
If I simply run an install of 8.04.2, will this do the trick, or do I need to follow some "anti-Vista" plot?

---

### Post by earthpigg on 2009-07-07
> **RayArdia said:**
> I've the same problem - ie how to COMPLETELY remove vista. Have downloaded and burned the latest 8.04.2 Hardy (tried Jaunty briefly, but ran into some problems!) so want to use a version I trust on this new Acer5735 laptop. Config is 4GB RAM, 250GB HDD.
If I simply run an install of 8.04.2, will this do the trick, or do I need to follow some "anti-Vista" plot?

put the cd in, _boot_ from the cd (ie: _dont_ put it in when the computer is already turned on), select 'use entire disk' and bam: windows is gone.*





[SIZE="1"]
*removing the 'designed for windows vista' stickers from the outside of your computer is your responsibility :p[/SIZE]

---

### Post by Fableflame on 2009-07-07
Okay. Vista is gone and I'm only running Ubuntu now. 8D
However, I'm having trouble playing flash.
I've tried installing several flash plugins but none of them are enabling me to view flash. Can anyone help me?

---

### Post by earthpigg on 2009-07-07
> **Fableflame said:**
> Okay. Vista is gone and I'm only running Ubuntu now. 8D
However, I'm having trouble playing flash.
I've tried installing several flash plugins but none of them are enabling me to view flash. Can anyone help me?

```
sudo apt-get install ubuntu-restricted-extras
```


in the future, it is best to always go with the software repositories and _*not*_ 'click here to download bla bla bla' on a website.:guitar:

---

### Post by Fableflame on 2009-07-08
OK, everthing is working great.
Thanks :D

---

