---
title: "Problem after upgrade to 9.10"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by Tykeboy on 2010-01-08
Hi, before the weekend I had 9.04 running on my PC alongside Windows XP. The machine has 3 hard drives, XP being on C: (40 Gig disk) and Ubuntu in a 10 Gig partition on D: (80 Gig disk). This had been running fine for a few months. I decided to upgrade to 9.10 which appeared to be successful except it wouldn't let me log in (including the root account for which I had previously set a password). I then wiped the D drive and reinstalled from a 9.10 disk and it installed again on the D drive in a 40 Gig partition. At first this worked fine, however, since monday I can't login to my account. I did get in as root - but only the first time. After I logged out and tried again as me or as root I could no longer get in. 

I can get in using recovery mode.

Anyone else had a similar problem or can suggest how to fix it?

---

### Post by ajgreeny on 2010-01-08
Is this a wubi install or a completely normal partitioned install.  I ask because you talk about installing into the D disk, and this is not the way that linux or ubuntu names disks.

The first thing to do is start up in recovery mode and see if you can reset your password(s).  Root password is not usually used in ubuntu, so I have no idea about how to deal with that, but for your user you can reset the user password from recovery with the commands shown in [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Why do you want to use a root account with password; is it because you are used to doing so in other distros?  I have been using ubuntu since the second version, 5.04, I think, and have never felt the need to have a separate root account.  have a good read of [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) to understand more, if you do not already know about it.

---

### Post by Tykeboy on 2010-01-09
Hi, thanks for your reply. It was a clean install from a 9.10 CD (downloaded and burnt by myself). The disk it installed on is an 80Gig disk (D drive under XP), I chose to split the drive into 2 40Gig partitions, and install 9.10 onto one of them.

It is not a password problem, because if I enter an incorrect password, it comes back immediately and says that the password is wrong. When I enter the correct password, it seems to be trying to start the graphical interface, but fails and comes back to the login page.

I set the root password because I use Linux (Debian I think) occasionally at work and thought it might be useful.

---

### Post by charlier653 on 2010-01-09
Side note on use of root.....

The only way I have ever been able to change X configuration is from the root account. I am sure there are other apps that gksu will not work on as well.

Using root for anything else *is* bad practice, however, when gksu will give the same or better results.

---

### Post by ajgreeny on 2010-01-09
> **charlier653 said:**
> Side note on use of root.....

The only way I have ever been able to change X configuration is from the root account. I am sure there are other apps that gksu will not work on as well.

Using root for anything else *is* bad practice, however, when gksu will give the same or better results.
I agree totally with your last comment, but I think you are incorrect about configuring X needing a root account.  You can certainly do all that using sudo, (or gksudo for gui applications) so I don't know whay you feel you need a root account.  In 5 years of ubuntu, as I said, I have never needed a root account, nor have I ever enabled one, and I have made a lot of different  configuration changes in those years when things have not worked as they should with my graphics card.

---

### Post by Trebaruna on 2010-01-09
I might have experienced the same problem. I think X simply restarts at some point during the login. Unfortunately, I do not recall exactly when/what it was. 
Perhaps there's an update somewhere that fixes the problem? Try logging in on a virtual terminal (CTRL+ALT+F1) and get the updates that way.
If this is new to you:
"sudo aptitude update" will get the latest package information, and "sudo aptitude full-upgrade" will, surprise surprise, install the latest packages.

---

### Post by Tykeboy on 2010-01-11
Thanks for that, I'll have a go tonight.

---

