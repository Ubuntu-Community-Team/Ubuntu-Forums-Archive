---
title: "Problems after Heron crash"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by Riffster on 2009-08-11
Hi guys

I'm very new here so appologies if this is in the wrong place. Please move if necessary. 

I'm also a linux Newbie - relatively speaking - despite having used it for more than a year, I'm only just getting to look under the floorboards so to speak. 

I've got 2 main problems at present: I had a good install of 8.04 Heron but somehow on Friday I managed to blow my entire system up. I have managed to reinstall it from fresh but I need to swap my data over. If I copy my home partition that seems to lock up and break the install. I'm ok with just saving specific bits - I would like very much to save my bookmarks and email (Firefox and Evolution respectively) - most of my other data is backed up. (I still have the old data on a separate drive.)

I also have a peculiar sound problem - use Second Life a lot and I cannot play streaming media in world. All other sounds seem to work well but I frequently dj and presenter in world and being unable to hear my own - or other peoples - streams is difficult. I've had some help with configuring the sound but this one aspect is troublesome. 

Any advice on either subject would be gratefully received.

Once I've got those problems sorted I want to put Fedora 11 on a disk and run both OS's side by side - but I'll probably need to play with Grub too then and will need my hand holding then too.

Cheers

---

### Post by ranch hand on 2009-08-11
Your home folder is where all your settings are.  This is probably the source of your crash.  Just transfer the bits you want.

Your bookmarks and so forth are hidden files (start with ".").  You can set nautilus to show them under "view".

---

### Post by mapes12 on 2009-08-11
> If I copy my home partition that seems to lock up and break the install. I'm ok with just saving specific bits - I would like very much to save my bookmarks and email (Firefox and Evolution respectively) - most of my other data is backed up. (I still have the old data on a separate drive.)Yeh. I had the same problem with an 8.04 reinstall. Copying /home onto the new installation didn't work for me either. The best option is install a new /home using the installer wherever you want it on you system then copy across /home/username from your backup set. That should also restore your username bookmarks and email contacts specific to your username account.

To save yourself grief with bookmarks checkout the Firefox Addon "Xmarks" everything is backed up on the Xmarks server for you.

For the sound problem I would suggest posting a seperate thread.

Mark

---

### Post by Riffster on 2009-08-11
> **mapes12 said:**
> Yeh. I had the same problem with an 8.04 reinstall. Copying /home onto the new installation didn't work for me either. The best option is install a new /home using the installer wherever you want it on you system then copy across /home/username from your backup set. That should also restore your username bookmarks and email contacts specific to your username account.

To save yourself grief with bookmarks checkout the Firefox Addon "Xmarks" everything is backed up on the Xmarks server for you.

For the sound problem I would suggest posting a seperate thread.

Mark


Thanks. I gave in and installed Jaunty from a magaizine disk and my sound issues are solved. I'm using this as an opportunity to clear out bookmarks by starting afresh.

I need to keep mails tho, where's the data stored in the partition to just swap that over?

Thanks for the advice so far guys

---

### Post by ranch hand on 2009-08-11
> **Riffster said:**
> Thanks. I gave in and installed Jaunty from a magaizine disk and my sound issues are solved. I'm using this as an opportunity to clear out bookmarks by starting afresh.

I need to keep mails tho, where's the data stored in the partition to just swap that over?

Thanks for the advice so far guys
/home/(your username)/.mozilla-thunderbird/(someweirdname).default/Mail

Just open your Places->Home Folder and click "show hidden files" under "view" and scroll down.

---

### Post by Riffster on 2009-08-12
> **ranch hand said:**
> /home/(your username)/.mozilla-thunderbird/(someweirdname).default/Mail

Just open your Places->Home Folder and click "show hidden files" under "view" and scroll down.


Thanks again. I notice you've pointed me at the Mozilla folder. Is that the same place for Evolution?

---

### Post by ranch hand on 2009-08-12
Ah, assumtions are a mistake.  No there is an evolution folder.

I gave up on evolution as an email server early on.  Lost mail somehow.

The mozilla folder is for FF and the mozilla=thunderbird for Thunderbird.  You will not have the second one if you have not installed Thunderbird.

---

### Post by Riffster on 2009-08-12
> **ranch hand said:**
> Ah, assumtions are a mistake.  No there is an evolution folder.

I gave up on evolution as an email server early on.  Lost mail somehow.

The mozilla folder is for FF and the mozilla=thunderbird for Thunderbird.  You will not have the second one if you have not installed Thunderbird.

ok thanks again.

I have used Evolution successfully so I don't really want to move to an alternative. I'm happy with it and the last thing I need is something else to learn. Where will I find the Evo folder?

---

### Post by ranch hand on 2009-08-12
The /home folder just like all the other hidden files that hold data for apps.

In mine it is between the .ecryptfs and .fontconfig.  It is all alphabetical.

Just be sure you click on the "show hidden files" under "view".  They are all after the files you are used to seeing (Documents, Pictures, Music).

---

### Post by Riffster on 2009-08-13
> **ranch hand said:**
> The /home folder just like all the other hidden files that hold data for apps.

In mine it is between the .ecryptfs and .fontconfig.  It is all alphabetical.

Just be sure you click on the "show hidden files" under "view".  They are all after the files you are used to seeing (Documents, Pictures, Music).


Thanks. This is all sorted now - thanks for everyone's help! Colour me a happy bunny :D

---

