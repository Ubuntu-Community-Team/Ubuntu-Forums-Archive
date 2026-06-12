---
title: "A small doubt on upgrading"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Gonz_91 on 2010-04-30
Hi everyone! I just torrented Lucid, and am thinking about doing a fresh install. Yet, and since I couldn't google an answer, I have this doubt: if, during the installation, I select my current /home partition to, well, mount on /home, will the new installation clear my current home?
This came up because I'm a hundred miles away from my external HD, and really wanted to do the upgrade during the weekend...

Thanks a lot in advance!

(Posted using the Lucid liveCD :P)

---

### Post by baligirl on 2010-04-30
Hi Gonz,

Well, as a disclaimer, I would not suggest doing a fresh install without backing up your /home, it would make me very nervous!

Today I did a fresh install of Lucid (after backing up my /home, of course!).  I chose the option to custom-map my partitions, and I got out my list of partitions that I had set up last time.  It listed all the partitions  (/dev/sda1. /dec/sda5. etc), but I had to edit each one manually and say that (for instance), I wanted /dev/sda1 to be  "ext4" and to be "/boot".  So what I am saying is, be sure you know which partition is your /home, so you don't accidentally overwrite it.  You can do this before you get started by going into System->Administration->System Monitor and clicking on the "File Systems" tab.  I would suggest that you write down the devices, their directories, and their type, so that you can make things exactly the same when you do your new install.

So now that you are sure which partition is indeed your /home partition, you can map that to /home during your install.

IMPORTANT!!  For all the other directories, I clicked the "Format Partition" box, so that it would overwrite everything so that all would be fresh and up-to-date.  HOWEVER, DO NOT CLICK THIS for your /home partition!  If you do this, you will blow away all your personal files, as it will reformat your /home partition.

So this is what I did, and after rebooting from my fresh install of Lucid, there was my /home partition, exactly as I had left it.

Best wishes!

Jennie

---

### Post by KinKiac on 2010-04-30
Backing up is always recommended.  Or, you could do what i do and just have 2 separate partitions for Ubuntu.  One for testing and one for your normal use.  Each time a new release comes out I just install to the testing partition.  If i like it i start using that as my primary OS and mount and copy anything i need form my other home directory.  If not i just change the order in the grub menu and use the old one again.  Its also nice to have 2 if one crashes and becomes unbootable(rare but it can happen), i just boot into the other and start poking around in the broken one to try to fix.  I also use totally separate drives and/or partitions for storing media and other documents, that way reformatting and re-installing doesnt affect me much.

---

### Post by Gonz_91 on 2010-04-30
Thanks a lot for your replies, guys!
Well, given the way Jennie emphasized the need for a backup, I'll try to "steal" an external HD from a friend, or a family member to do a backup of my /home before updating :P


Once again, thanks a lot!

---

