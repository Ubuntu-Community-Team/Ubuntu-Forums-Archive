---
title: "Is there a way of telling if others have accessed my machine?"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by Mick8882003 on 2008-12-22
Yea, just curious if anyone else has accessed my machine from its logs, should be pretty easy as I am the only one using the machine...

Cheers Mick

---

### Post by SlidingHorn on 2008-12-22
View your user login & auth. logs:  /var/log/auth.log

---

### Post by Mick8882003 on 2008-12-22
Dec 22 13:29:01 mick-desktop gnome-keyring-daemon[5717]: Couldn't unlock login keyring with provided password
Dec 22 13:29:01 mick-desktop gnome-keyring-daemon[5717]: Failed to unlock login on startup
Dec 22 13:50:17 mick-desktop seahorse-daemon[6817]: init gpgme version 1.1.6
Dec 22 14:17:01 mick-desktop CRON[7705]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec 22 14:17:01 mick-desktop CRON[7705]: pam_unix(cron:session): session closed for user root
Dec 22 14:38:04 mick-desktop gnome-keyring-ask: could not grab keyboard: 3
Dec 22 15:17:01 mick-desktop CRON[8852]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec 22 15:17:01 mick-desktop CRON[8852]: pam_unix(cron:session): session closed for user root
Dec 22 16:17:01 mick-desktop CRON[9921]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec 22 16:17:01 mick-desktop CRON[9921]: pam_unix(cron:session): session closed for user root
Dec 22 16:43:39 mick-desktop sudo: pam_unix(sudo:auth): authentication failure; logname=mick uid=0 euid=0 tty=/dev/pts/0 ruser= rhost=  user=mick
Dec 22 16:43:59 mick-desktop sudo:     mick : 3 incorrect password attempts ; TTY=pts/0 ; PWD=/home/mick ; USER=root ; COMMAND=/usr/sbin/smartctl -a /dev/sda
Dec 22 16:44:11 mick-desktop sudo:     mick : TTY=pts/0 ; PWD=/home/mick ; USER=root ; COMMAND=/usr/sbin/smartctl -a /dev/sda
Dec 22 17:17:01 mick-desktop CRON[11215]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec 22 17:17:02 mick-desktop CRON[11215]: pam_unix(cron:session): session closed for user root
Dec 22 17:50:30 mick-desktop polkit-grant-helper[11913]: granted authorization for org.freedesktop.systemtoolsbackends.set to pid 11888 [uid=1000] [auth=mick]
Dec 22 17:51:00 mick-desktop polkit-grant-helper-pam[11933]: pam_unix(polkit:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=mick rhost=  user=mick
Dec 22 17:51:09 mick-desktop polkit-grant-helper[11937]: granted authorization for org.freedesktop.systemtoolsbackends.set to pid 11925 [uid=1000] [auth=mick]

Should I be worried about these?

---

### Post by StOoZ on 2008-12-22
unless its you , there were 3 attempts (at Dec 22 16:43:59) to log with the user mick into your system , none succeeded.

---

### Post by hyper_ch on 2008-12-22
are you afraig against physical or remote login?

---

### Post by Mick8882003 on 2008-12-22
Those attempts where me stuffing up my password :lolflag:

---

### Post by Sprut1 on 2008-12-22
For users logged on atm:

```
who
```

For list of last logged in users:

```
last
```

---

### Post by mkvnmtr on 2008-12-22
There is quite a bit of intrusion alert software in the repositories. Search in the package manager. I have never had the need to use any but I believe system administrators use it a lot. When you get an idea of what is available I am sure some people on the forums will be familiar with it.

---

### Post by baruch60610 on 2008-12-22
I just wanted to say that, unless you're running a server exposed to the Internet, intrusion detection software is a bit of overkill.  Much of it requires you to know a good bit about how it works.  Some may require you to set up a MySQL or other database to keep track of the information they gather.  If you're just worried about someone trying to get into your machine locally (someone in the same home/office/dorm, etc.), then I don't recommend intrusion detection software.

I *do* recommend that you use a good, strong password.  If you have a cat named Fluffy, then 'fluffy' would be a terrible password.  Someone who knows you could guess that and get in.

You might consider using a locking screen saver (I don't recall how to set that up, but it's in some of the system settings).  After a certain amount of time, the screen saver comes on, the computer is locked, and you need to enter a password to use it again (or to even see behind the screen saver).  This can help if you step away from your computer, and there are people who might want to take a peek while you're away - or do damage, or whatever.

Of course, if someone already has your password, then you won't be able to find much in the logs.  It will all be in your name.

---

