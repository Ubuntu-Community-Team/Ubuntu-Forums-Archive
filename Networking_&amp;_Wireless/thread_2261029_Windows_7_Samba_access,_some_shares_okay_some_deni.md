---
title: "Windows 7 Samba access, some shares okay some denied"
date: 2015-01-15
forum: Networking &amp; Wireless
---

### Post by MotF Bane on 2015-01-15
I'm primarily a Windows user, trying to rebuild my file server onto Ubuntu.  

14.04 with Samba set up, static IP configured, a primary drive and two big data drives.  I've set up a user account for my Windows machine (account = Avahi).  From the Windows machine, I can open the Avahi share folder, and freely edit it.  However, when attempting to open the data drives, I get a Windows cannot access/you do not have permission error.  I've been digging around online, but the fact that I can use one share, but not the separate drive shares, is really throwing the results off and puzzling me.  I'd expect it to be a setting problem in the shares, but everything is checked off.  

Samba server settings: mygroup, Samba Server, auth mode User, No Guest Acct.  Samba user: Avahi, windows name Administrator.

Samba share settings:
Directory: /media/stephen/Red1
Share name: Red1
Description: Red1Full
Writable, Visible.  Access only allow to spec, Avahi is checked.
Same share settings apply to the second drive, 3TBRed2.  

I've attached what seems to be the relevant section of the log file.  It's level 3.  I'm hoping the answer is in there, but it's gibberish to me.  I've also attached my smb.conf, just in case there's something useful in that.  

Thanks!

Log file:
[ATTACH]259284[/ATTACH]

Config file:
[ATTACH]259285[/ATTACH]

---

### Post by MotF Bane on 2015-01-17
Issue resolved.

In the interest of anyone who might stumble onto this thread via search:

Install ntfs-config, change the drive mount points from /media/stephen/<drive> to /media/<drive>, and check the box in ntfs-config for write on internal drives.  Adjust the Samba settings for the new mount points (i.e. /media/<drive>).  And now it all works.  God only knows why the default mount is into one's user folder.

---

