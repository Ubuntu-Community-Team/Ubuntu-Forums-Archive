---
title: "Can't play .mp3 from Windows share"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by dcross on 2007-03-04
Hello.  Complete newbie to Linux and Ubuntu.  Been a Windows users for years, still am, but trying Ubuntu now.

I have a problem with playing .mp3s from a Windows 2003 server share.  I can connect to the share, see all the files, even copy the files to my Ubuntu home directory and play the file successfully from there, but if I try to play the file directly from the Windows share I get an error "Could not read from resource".

I get this every time, no matter what player I use.  Remember I can copy the files to the home folder on Ubuntu and play then with no problem at all from there.

Why won't they play from the server over the network?  I need complete instructions with exact commands if I need to do anything.  I have run through the Samba quick guide and that has worked fine, but everything I have read relating to Samba always seems to be a Windows user wanting to access Ubuntu shares - not the other way around.

Thanks in advance.

David.

---

### Post by adachan on 2007-04-03
I have the exact same problem.  Some friends have told me playing mp3 files from a smb share is broken.  Is this true, or is there a way to do this?  Please help us....

---

### Post by Shazaam on 2007-04-03
Ubuntu has no native support for mp3's. You have to get the proper codecs.
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/codecs.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/codecs.html)

---

### Post by haemphyst on 2007-04-03
He already SAID he can play them if copied to the local drive.  This tells me he has the proper codecs installed.  I'll be wanting to do this IDENTICAL thing shortly, so if anybody can help, that'd be greeeaaat.

---

### Post by spd106 on 2007-04-03
Personally I prefer using DAAP, but some people have reported it working with smbfs.

See [http://www.ubuntuforums.org/showthread.php?t=354053](http://www.ubuntuforums.org/showthread.php?t=354053)

---

### Post by DraconPern on 2007-05-06
This is still not fixed in 7.04. Argh... You still have to copy the file locally to play them.  It's very simple in Windows and OS X, why not in Ubuntu?

---

### Post by nathanhill on 2007-08-28
I have also been tremendously frustrated by this problem.  Playing MP3 from unmounted SMB shares works with other distros - but you have to install a xine plugin: XINE-SMB which I've never been able to find in a debian repo.

Check this link for more info:[https://bugs.launchpad.net/ubuntu/+source/xine-lib/+bug/32436/comments/27](https://bugs.launchpad.net/ubuntu/+source/xine-lib/+bug/32436/comments/27)

I would REALLY like to see this get FIXED.

---

### Post by will71110 on 2007-08-28
Check the mp3 files themselves and make sure they have access permissions, not just read/write.  If they dont, you wont beable to play it directly off the drive.

EDIT:  Whoops:  It's Read and Execute in windows.  That might not make a diff though.

Do you have to log in when accessing the hard drive?

---

### Post by Dark Star on 2007-08-28
I guess this is the case with NTFS vol. . dude tell that can you copy files from windows partition.. The same error I receive when I 1'st switched Ubuntu :p

---

### Post by will71110 on 2007-08-28
How are you mapping to the drive?  I use fstab to map my smbfs.  Access to my hard drive is much faster and I havent had any problems.

---

### Post by rallyrulz on 2008-04-30
Hey guys I think I found it, well it worked for me. 

My situation:
 In ubuntu 7.04 I used to be able to play from a windows share
 Upgraded to 7.1 and couldnt, got no codec installed errors or file just did not play

My Fix
 Right click on the file, go to permissions tab and TICK the 'allow executing of file as a program'

Yet another stupid ubuntu issue, surely if they rate ubuntu as a 'commercial desktop' ready for general public use they would sort these things out. I swear im going to switch to OSX !

---

