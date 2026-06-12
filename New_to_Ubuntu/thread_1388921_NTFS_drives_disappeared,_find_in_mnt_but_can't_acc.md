---
title: "NTFS drives disappeared, find in /mnt but can't access"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by TJGeezer on 2010-01-23
Make that NTFS, sorry. "STFS" sounds like troll-speak but I can't edit the subject line I guess..

Here's the problem - I have a logon id for everyday use, a desktop-user without admin privileges. Recently I removed, then reinstalled Orca in an attempt to get its settings to stick. No joy. But more disturbing, after I removed it again, my NTFS partitions (an internal hdd, 2 USB drives, the main Windows partition) all disappeared from my desktop.

I tried a few things to see if I could bring them back - logged on as administrator and used the System user-and-group applet to assign every privilege to the desktop user including administrative, for example.  Made the desktop user a member of the Administrativce group. No joy. 

I found the missing drives listed in /mnt and the missing partitions in /dev but was afraid to do anything more. Double-clicking on a /dev/disk/by-label icon popped up "no application installed for block device files" and double-click on /mnt produced a blank window. Nothing there.

The drives do show up in /media but double-clicking there popped up a notice that I don't have the necessary permissions to view the contents.

I see lots of "failure to mount" references in the forums but is that the problem I'm having? Doesn't seem like it, since my non-admin user is the only one that can't use the drives, but what do I know. 

Disheartening. I was feeling so close to making the switch from MS Viscous. But now I can't get Orca magnifier to work (needed for a low vision problem) and can't access my USB or other NTFS partitions from my on-admin id. Granting full administrator status doesn't help. 

Can you help me get my drives back? Then I'll tackle the Orca problem another day...

Thanks!
:confused:

---

### Post by cariboo on 2010-01-23
To get your ntfs partition to mount correctly again, install ntfsprogs, it is in the repositories. The package contains tools that make it easier to deal with ntfs partitions. As far as the Orca problem goes, I can't help with it, but if you ask a question in [here]("http:///ubuntuforums.org/forumdisplay.php?f=145"), someone should be able to help with your problem.

**Edit** I fixed the title for you.

---

