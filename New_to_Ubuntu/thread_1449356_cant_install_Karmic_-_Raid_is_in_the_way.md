---
title: "cant install Karmic - Raid is in the way"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by stevek123 on 2010-04-07
I have been absolutely frustrated trying to install Karmic. Sys is new 'hand-me-down' 3.8G dual core 2MD ram with 160GB HD. It used to be on a raid system running ubuntu (Jaunty I think...). 
Yesterday I couldnt get past 'prepare partitions' during install. Today I removed all existing partitions using gparted off the cd. Still nothing. Then I went into bios to change boot options to cd & HD, but there was not option for HD. 
I rebooted and hit F10 to configure Raid. While there I hit the delete button - which sent me to a page to configure it. I just left the raid HD column blank and went on into install. I got it to install (over & over & over... using multiple configs of partitions including the automatic). 

Now when I boot it does not see the HD and immed asks for bootable media.
When I re-install it tells me that 9.10 is already installed... so its there. During boot it tells me that raid is detected and gives option to F10 for configure. I skip cuz it wont give option to disable or delete and I dont want it. I think Raid is blocking my bootinstaller.

 I've looked in the bios - I dont see any way to disable there - there is no 'integrated periphs' category. The only hardware I saw was an unused SCSI pci card that I've removed. How do I get this off??? I've got 6 hours into it so far and FFFfffffail.....

---

### Post by HDave on 2010-04-07
Does your computer have an Intel motherboard with a "Fake-RAID" type raid controller?  If so, you have a real problem.

Otherwise I would do my best to disable the RAID controller from BIOS by setting it to JBOD (just bunch of disk) if it has that setting.  And then try again from scratch using the automated partitioning from the installer.

---

### Post by stevek123 on 2010-04-07
Not an Intel - an ASUS I think. I just hunted down a MB manual from asus and it looks similar. Google searches said there can be physical jumpers or Bios settings. I looked for jumpers but didnt see any (and most stuff was well labeled)... so I suspect a bios setting. Its just that I searched all thru it and didnt find any. FFFfffail. I was hoping some others here had played with Raid settings and would direct me. Thanks.

---

### Post by Slim Odds on 2010-04-07
The fake-RAID crap is not worth your time. And the suggestion about JBOD is also bad. Just turn all that crap off and use mdadm (software RAID). It works fine and it's a lot more obvious.

I use RAID-0 that way and it's very fast.

---

### Post by stevek123 on 2010-04-07
Slim - I dont want Raid - I'm trying to disable it. Just dont know how cuz I didnt install it - comp came with it installed.

---

### Post by sandyd on 2010-04-08
> **stevek123 said:**
> Slim - I dont want Raid - I'm trying to disable it. Just dont know how cuz I didnt install it - comp came with it installed.

ok. just do this. boot up using the desktop livecd. use mdadm to recreate the raid setup since youve screwed it up already. and install. thats it. what do you have against RAID anyways...

---

### Post by -humanaut- on 2010-04-08
You can try booting with the option dmraid i think its called. hit F6 its in there

---

### Post by Steven_S on 2010-04-08
Logically, if the system used to hold disks in a RAID array and was set up structurally to work like that, and now only holds one disk, it stands to reason that it is looking for the other (now missing) disks and has a problem. 

Was the disk that is in there now the disk where the OS was on in the original system? I'm asking because you don't seem to get the option to boo from HD - which could point to hardware setup problems.

If you have re-formatted your HD, that would logically mean that the RAID setup is either in hardware (which you tried), or in the BIOS. So, I would try checking your BIOS first and start clean after that. If that works, swell. If it doesn't, you will have to check the insides of your system again for connections and jumper settings.

And since someone asked what (anyone) has against RAID: I'm not an expert, but I can't see any reason to pick a RAID option if you have only one internal disk. And even with more than one disk (I have 4 in my machine), I personally stay away from RAID, after reading hundreds of opinions, comparisons and how-to's. My main reason for not using RAID is that, when your system fails, you can't just take out the disks and pop them into another machine to retrieve your data. Also, going by the horror stories available, re-building a RAID setup when one of the disks fails seems to be a lot more issue-laden in reality than it is in theory. 

My internal disks just mirror on a schedule (the back-up disks are not mounted when not used - at least, if I get all the ntfs mounting and permission stuff cleared out :-)), and the most important stuff goes off-site. I don't think I need the benefits of RAID so much that I would also need the issues with it.

---

### Post by NickFletcherCC on 2010-04-08
> **stevek123 said:**
> Not an Intel - an ASUS I think.

I use an Asus, in order to get the RAID array to work you need to put the SATA leads into a special pair of headers, coloured red instead of the usual black I think.  What you may need to do is to remove the SATA leads and put them into the standard black headers on the motherboard and then redetect them and restart the installation.

Best of luck

---

### Post by Slim Odds on 2010-04-08
> **stevek123 said:**
> Slim - I dont want Raid - I'm trying to disable it. Just dont know how cuz I didnt install it - comp came with it installed.

Then disable it in the BIOS. That's the place where you have to disable it.

---

### Post by glock30 on 2010-04-08
I had once where I was unable to install because the drives that I was using used to be part of a raid.  I installed the drives on to a computer with no raid enabled, but for some reason, the raid would always show up during install... I ended up doing a crap ton of searching and found [http://www.dban.org/.]("http://www.dban.org/")  This pretty much nukes EVERYTHING on the drive.. takes forever, but it did the trick.  Just be careful, because it will do all the drives on the computer if you command it to.[URL="http://www.dban.org/"]
[/URL]

---

### Post by Slim Odds on 2010-04-08
> **glock30 said:**
> I had once where I was unable to install because the drives that I was using used to be part of a raid.  I installed the drives on to a computer with no raid enabled, but for some reason, the raid would always show up during install... I ended up doing a crap ton of searching and found [http://www.dban.org/.]("http://www.dban.org/")  This pretty much nukes EVERYTHING on the drive.. takes forever, but it did the trick.  Just be careful, because it will do all the drives on the computer if you command it to.[URL="http://www.dban.org/"]
[/URL]

Glad that worked for yah, but I think that you made it harder than it needed to be.

You should be able to just use gparted to delete the old partitions and create whatever you need.

---

### Post by glock30 on 2010-04-08
I actually tried gparted and created a new partition table... it would say it was successful, but then I would go to install, and the partition manager there (not too sure what it is called) would still read the raid.  I fought with it for a couple of days trying different things I searched for, and this was the only one that worked.  That is why I suggested it.

---

### Post by oldfred on 2010-04-08
Drives seem to save raid info;

Does this show raid info?
ls /dev/disk/* -l


Do not run this on raid drives as it will destroy the raid setup:
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

---

### Post by stevek123 on 2010-04-09
Bah! I finally found the raid enable/disable switch in the bios. 3 menus in under the sata ide. A place I'd never been...Once it was disabled, the thing booted up right away. Now on to other problems....sound issues...

---

### Post by Slim Odds on 2010-04-09
> **stevek123 said:**
> Bah! I finally found the raid enable/disable switch in the bios. 3 menus in under the sata ide. A place I'd never been...Once it was disabled, the thing booted up right away. Now on to other problems....sound issues...

Like I said..... :)

---

