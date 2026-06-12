---
title: "Your /home/.dmrc file is being ignored"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-06-17
Hi all,

I seem to be having a strange problem that resurfaces every time I restart my computer.

When I first turn the machine on, I get /home/.dmrc file is being ignored.,,,blah blah something about 644 permissions. 

So I enter this into shell, because X refuses to boot without this:
```
chmod 644 /home/girdy/.dmrc
```

I get past that error, and then I get something about the ICEauthority file. I give it the same permissions:
```
chown 644 /home/girdy/.ICEauthority
```

All is well, until I restart my computer. Then it repeats itself all over again! ](*,)

*I should note that I just recently installed TimeVault on my computer.*

Is there some reason why these file permissions are erased every time i restart? 

thanks for any help :D

---

### Post by asuastrophysics on 2009-06-17
nobody has any ideas?

---

### Post by freebeer on 2009-06-17
I haven't run into the ICEauthority one, but I did run into the .dmrc one.

I did the chmod 644 on .dmrc (although it was already set that way) and also made sure that my home directory was chmod'ed to 700 (which it wasn't).  That's supposed to clear up the issue.  I haven't tried rebooting yet, so I can't verify until I do.

---

### Post by asuastrophysics on 2009-06-18
alright i just did that i'm going to restart here in a sec and i'll let you know if it worked.

---

### Post by asuastrophysics on 2009-06-18
same thing!

somehow the permissions are changed every time i restart.

i don't even know how/why this started happening.

is it possible that some program on shutdown is chmodding my home folder?

if so why?

---

### Post by philinux on 2009-06-18
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by asuastrophysics on 2009-06-18
these are my current /home/USER permissions,
after running chmod 700 /home/girdy:

```
girdy@girdy-laptop:~$ ls -al /home/girdy
total 12804
drwxr-xr-x 58 girdy girdy    4096 2009-06-18 18:36 .
drwxr-xr-x  3 root  root     4096 2009-06-09 01:17 ..
drwx------  3 girdy girdy    4096 2009-06-09 16:57 .adobe
drwx------  2 girdy girdy    4096 2009-06-17 20:56 .aptitude
-rw-------  1 girdy girdy   11130 2009-06-18 18:35 .bash_history
-rw-r--r--  1 girdy girdy     220 2009-06-09 01:17 .bash_logout
-rw-r--r--  1 girdy girdy    3115 2009-06-09 01:17 .bashrc
drwxr-xr-x  6 girdy girdy    4096 2009-06-16 15:45 .cache
drwxr-xr-x  2 girdy girdy    4096 2009-06-18 18:43 catalog
drwxrwxrwx  3 girdy girdy    4096 2009-06-10 14:11 .compiz
drwxrwxrwx 11 girdy girdy    4096 2009-06-15 16:16 .config
drwx------  2 girdy girdy    4096 2009-06-13 14:43 .covers
drwxrwxrwx  3 girdy girdy    4096 2009-06-09 08:18 .dbus
drwxr-xr-x  2 girdy girdy    4096 2009-06-10 18:22 .debtags
drwxrwxrwx  2 girdy girdy    4096 2009-06-18 18:37 Desktop
-rw-r--r--  1 girdy girdy      28 2009-06-17 18:29 .dmrc
drwxrwxrwx  5 girdy girdy    4096 2009-06-16 16:09 Documents
-rw-rw----  1 girdy girdy      16 2009-06-09 08:18 .esd_auth
drwxr-xr-x  7 girdy girdy    4096 2009-06-10 00:32 .evolution
-rw-r--r--  1 girdy girdy     357 2009-06-09 01:17 examples.desktop
-rw-rw-r--  1 girdy girdy 2614230 2009-06-11 04:58 Firefox_wallpaper.png
drwxr-xr-x  2 girdy girdy    4096 2009-06-12 13:46 .fontconfig
drwxrwxrwx  5 girdy girdy    4096 2009-06-18 18:28 .gconf
drwxrwxrwx  2 girdy girdy    4096 2009-06-18 18:42 .gconfd
-rw-r-----  1 girdy girdy       0 2009-06-18 18:37 .gksu.lock
drwx------  2 girdy girdy    4096 2009-06-13 14:45 .gmpc
drwxr-xr-x  3 girdy girdy    4096 2009-06-10 13:50 .gnome
drwxrwxrwx 11 girdy girdy    4096 2009-06-17 19:51 .gnome2
drwx------  2 girdy girdy    4096 2009-06-09 08:18 .gnome2_private
drwxrwxrwx  2 girdy girdy    4096 2009-06-12 13:23 .gnupg
drwxr-xr-x  2 girdy girdy    4096 2009-06-16 18:04 .gstreamer-0.10
-rw-r--r--  1 girdy girdy     152 2009-06-18 18:34 .gtk-bookmarks
dr-x------  2 girdy girdy       0 2009-06-18 18:27 .gvfs
-rw-r--r--  1 girdy girdy    3267 2009-06-17 18:29 .ICEauthority
drwx------  3 girdy girdy    4096 2009-06-10 20:12 .icedteaplugin
drwxr-xr-x  5 girdy girdy    4096 2009-06-10 14:41 .icons
drwxr-xr-x  4 girdy girdy    4096 2009-06-16 16:23 internal
drwxr-xr-x  3 girdy girdy    4096 2009-06-16 15:38 .java
drwx------  9 girdy girdy    4096 2009-06-16 15:31 .kazehakase
drwx------  3 girdy girdy    4096 2009-06-12 13:46 .kde
drwx------  2 girdy girdy    4096 2009-06-09 17:38 .kino-history
-rw-r--r--  1 girdy girdy    2969 2009-06-16 15:58 .kinorc
drwx------  3 girdy girdy    4096 2009-06-09 16:56 .local
-rw-r--r--  1 girdy girdy 1294760 2009-06-10 15:03 macfonts.tar.gz
drwx------  3 girdy girdy    4096 2009-06-09 16:57 .macromedia
drwx------  6 girdy girdy    4096 2009-06-11 02:39 .mozilla
drwxrwxrwx  8 girdy girdy    4096 2009-06-11 11:49 Music
drwxr-xr-x  3 girdy girdy    4096 2009-06-09 08:18 .nautilus
-rw-r--r--  1 girdy girdy   33777 2009-04-23 08:06 nautilus_2.26.2-0ubuntu2.diff.gz
-rw-r--r--  1 girdy girdy    2025 2009-04-23 08:06 nautilus_2.26.2-0ubuntu2.dsc
-rw-r--r--  1 girdy girdy 8697871 2009-04-13 22:05 nautilus_2.26.2.orig.tar.gz
drwxr-xr-x  3 girdy girdy    4096 2009-06-10 20:12 .netx
drwxr-xr-x  3 girdy girdy    4096 2009-06-10 14:47 .openoffice.org
drwx------  9 girdy girdy    4096 2009-06-16 15:45 .opera
drwxr-xr-x  2 girdy girdy    4096 2009-06-16 15:51 pending
drwxrwxrwx  4 girdy girdy    4096 2009-06-16 16:11 Pictures
drwxrwxrwx 10 girdy girdy    4096 2009-06-16 15:45 .PlayOnLinux
-rw-rw-r--  1 girdy girdy     675 2009-06-09 01:17 .profile
drwxrwxrwx  2 girdy girdy    4096 2009-06-09 08:18 Public
drwx------  2 girdy girdy    4096 2009-06-18 18:34 .pulse
-rw-rw----  1 girdy girdy     256 2009-06-09 08:18 .pulse-cookie
drwx------  4 girdy girdy    4096 2009-06-15 19:05 .purple
drwxr-xr-x  2 girdy girdy    4096 2009-06-12 13:46 .qt
-rw-------  1 girdy girdy   61235 2009-06-18 18:36 .recently-used.xbel
drwxr-xr-x  2 girdy girdy    4096 2009-06-10 16:47 .screenlets
drwx------  2 girdy girdy    4096 2009-06-09 12:29 .ssh
-rw-r--r--  1 girdy girdy       0 2009-06-09 12:29 .sudo_as_admin_successful
drwxrwxrwx  2 girdy girdy    4096 2009-06-09 08:18 Templates
drwxr-xr-x  6 girdy girdy    4096 2009-06-11 02:10 .themes
drwxr-xr-x  8 girdy girdy    4096 2009-06-10 14:41 .themes.old.link
drwx------  4 girdy girdy    4096 2009-06-10 18:27 .thumbnails
drwxr-xr-x  2 girdy girdy    4096 2009-06-17 20:59 .update-manager-core
drwx------  2 girdy girdy    4096 2009-06-09 17:15 .update-notifier
drwxrwxrwx  2 girdy girdy    4096 2009-06-17 18:17 Videos
-rw-r--r--  1 girdy girdy     296 2009-06-10 18:08 wget-log
drwxr-xr-x  3 girdy girdy    4096 2009-06-13 12:02 .wifi cracker
-rwxr-xr-x  1 girdy girdy     196 2009-06-11 22:04 Wifi Hard Restart
drwxr-xr-x  4 girdy girdy    4096 2009-06-16 15:42 .wine
-rw-r--r--  1 girdy girdy   82262 2009-06-07 20:38 winetricks
drwxr-xr-x  2 girdy girdy    4096 2009-06-11 11:58 .winetrickscache
-rw-------  1 girdy girdy       0 2009-06-17 20:27 .Xauthority
-rw-rw-r--  1 girdy girdy   11435 2009-06-17 19:11 .xsession-errors

```

---

### Post by asuastrophysics on 2009-06-18
i seemed to have fixed my home problem, but i'm not even sure why/how.

i just deleted some junk folders out of the /home directory. 

fixed the problem

---

### Post by Possum Films on 2009-06-20
> **philinux said:**
> [https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
Thanks for that link. I encountered the same problem (although I could still start X). Those instructions worked perfectly.

---

### Post by asuastrophysics on 2009-06-22
nope, actually i was wrong. that didn't fix the problem.

turns out my hard drive was failing. every restart i did would corrupt data. the .dmrc file permisions were on a bad sector. 

sucks, because this laptop is 6 months old. :confused:

---

