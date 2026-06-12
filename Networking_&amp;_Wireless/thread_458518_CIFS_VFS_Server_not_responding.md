---
title: "CIFS VFS: Server not responding"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by changlinn on 2007-05-29
CIFS VFS: Server not responding
I get this error at shutdown, and it repeats several times, usually for the amount cifs shares I have mounted, which can be a few if I am at work. It usually takes 10-15 seconds per error for it to move on, meaning this part of shutdown can take a minute or two.
Is there anyway to fix this, short of umounting the shares prior to shutdown?
I don't get the error when for example I am on the bus as no shares have mounted, but I am seeing this error on all the Ubuntu PC's in the house, all 4. All are pretty Much stock Ubuntu. I did search the forums and found a post on NAS' where someone got the same error. But all hints were in vain, I do have VMware on here and two of the 4 Ubuntu PC's. I run gnome, and on the other two Ubuntu PC's only stuff from the standard repos are installed.

---

### Post by changlinn on 2007-06-05
bump...
seriously no-one else has seen this, and i am getting it on 4+ machines in two separate networks?

---

### Post by krouskop on 2007-06-06
Same thing just happened when I rebooted (found your post google-ing the error message)... No idea how how exactly to remedy it, but it is happening to other people.

---

### Post by t0maz on 2007-06-08
Same here. :-( No solution for it?

---

### Post by HiDefDog on 2007-06-09
Check out this thread;
[http://ubuntuforums.org/showthread.php?t=293513](http://ubuntuforums.org/showthread.php?t=293513)

Worked for me :)

---

### Post by dmizer on 2007-06-10
thanks for the tip HiDefDog ... i've been hunting for a fix for that for a couple weeks now.

---

### Post by vmax4ever on 2007-06-15
This link: just great - all works properly. Thanks a lot

---

### Post by LarryJ2 on 2008-02-08
I have been using the utility  smb4k available in the repositories.   In there you have the option Settings -> Configure smb4k-> shares,   then check option "Unmount all shares of user ... on exit".

I would occasionally get the CIFS VFS: giant pause upon restart but this smb4k configuration change seemed to fix it.

FYI, smb4k mounts your shares on your home directory so, for example,  you might have access  to your "share" folder at /home/user/smb4k/share.   Very useful and convenient.

More info on  smb4k  ( An Advanced Network Neighborhood Browser for KDE)  here:

[http://smb4k.berlios.de/](http://smb4k.berlios.de/)

Thank you  Alexander, Massimo and Franck, the developers at berliOS.

---

### Post by andb on 2008-02-08
Have you tried adding the share to /etc/fstab? this should properly mount / unmount for you, without any hassles. The more the software, the more the nightmare :) and I wouldn't add a program to do something as managing network share mounts. Even if it the machine does lag if you forget to unmount, I walk away from the computer after turning it off anyway :D

---

### Post by LarryJ2 on 2008-02-09
> Have you tried adding the share to /etc/fstab?
Speaking for myself,  I've manually added the shares on my local network (using sudo mount ...) ,  put them in /etc/fstab and lately used  smb4k. Since   I have six or so shares (directories on a raid local server)  I really don't need access to any of them constantly.   When I do need them, I ask smb4k to mount them individually which it usually does  without a problem  to /home/user/smb4k. I use kwallet to save the passwords for the mounted shares so one click and the share is available for rw access in konqueror.  By the way, the mounting point or directory is arbitrary, smb4k is just the default.  So for me,  having smb4k mount my shares upon demand is easiest.

---

### Post by Deb.Early on 2008-03-27
I was tearing my hair out over this too until I discovered this simple bugfix in Peter van der Does' blog: [http://blog.avirtualhome.com/2008/03/10/ubuntu-shutdown-problem-cifs-related/](http://blog.avirtualhome.com/2008/03/10/ubuntu-shutdown-problem-cifs-related/) . Worked like an absolute charm for me. Thanks, Peter! :)

I didn't have the problem until I switched from SMBFS to CIFS network mounts in /etc/fstab, apparently CIFS is much less forgiving than SMBFS when you pop its network connection.

I'm a relative newbie so what do I know -- but what Peter described sure looks like a bug to me. If it is a bug, I couldn't find anything in launchpad about it. Shouldn't someone enter it? I'd think it would be an easy fix for the rc6/rc0 scripts maintainer.

---

