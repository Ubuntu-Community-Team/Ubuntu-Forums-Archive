---
title: "Can some post the output of these: ls -l /home and ls -la ~. Please!"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by bhadotia on 2009-01-11
The reason is:
I had made a backup of my home folder using a live CD when I was trying to recover my system after the partition table got messed up. But unfortunately, in a hurry, I copied my home folder as root. So that the root became the owner of all my files on the backup. 
But I could not recover the system(only my linux installations were affected and windows was the culprit) and to reinstall ubuntu (and unfortunately wipe openSuse and Arch). Now want to know what are the default permissions set for the home directory and the configuration files (the dot files) in it.

---

### Post by ajcham on 2009-01-11
> **bhadotia said:**
> The reason is:
I had made a backup of my home folder using a live CD when I was trying to recover my system after the partition table got messed up. But unfortunately, in a hurry, I copied my home folder as root. So that the root became the owner of all my files on the backup. 
But I could not recover the system(only my linux installations were affected and windows was the culprit) and to reinstall ubuntu (and unfortunately wipe openSuse and Arch). Now want to know what are the default permissions set for the home directory and the configuration files (the dot files) in it.

[LIST=1]
[*]**/home** should be 755 and owned by root
[*]**~** should be 700, 744 or 755 and owned by you
[*]All files and folders within **~** should be owned by you and have appropriate permissions set: 6 or 7 for the owner and 0, 4 or 5 for group and world.
[*]One exception to number 3: **~/.dmrc** should be 644 and owned by you
[/LIST]

---

### Post by bhadotia on 2009-01-11
Thank you very much. :KS
If there a guide describing these defaults for the system you can point me to, I would appreciate that.

---

### Post by Captain_tux on 2009-01-11
Keep in mind that **any** file that begins with a dot is a hidden file and not necessarily only a config file.

---

### Post by minsf on 2009-01-11
minsf@minsf-laptop:~$ ls -l /home
total 4
drwxr-xr-x 45 minsf minsf 4096 2009-01-11 10:51 minsf

total 308
drwxr-xr-x 45 minsf minsf  4096 2009-01-10 19:43 .
drwxr-xr-x  3 root    root     4096 2008-12-04 21:43 ..
drwx------  3 minsf minsf  4096 2008-12-12 09:45 .adobe
drwx------  2 minsf minsf  4096 2009-01-10 15:07 .aptitude
-rw-------  1 minsf minsf  7079 2009-01-10 19:42 .bash_history
-rw-r--r--  1 minsf minsf   220 2008-12-04 21:43 .bash_logout
-rw-r--r--  1 minsf minsf  3115 2008-12-04 21:43 .bashrc
drwxr-xr-x  5 minsf minsf  4096 2008-12-15 01:34 .cache
drwxr-xr-x  7 minsf minsf  4096 2009-01-10 22:08 .config
drwx------  3 minsf minsf  4096 2008-12-04 21:52 .dbus
drwxr-xr-x  2 minsf minsf  4096 2009-01-10 15:07 .debtags
drwxr-xr-x  4 minsf minsf  4096 2009-01-11 10:36 Desktop
-rw-------  1 minsf minsf    28 2009-01-10 09:47 .dmrc
drwxr-xr-x  4 minsf minsf  4096 2009-01-04 17:56 Documents
-rw-------  1 minsf minsf    16 2008-12-04 21:52 .esd_auth
drwxr-xr-x  7 minsf minsf  4096 2008-12-12 11:20 .evolution
lrwxrwxrwx  1 minsf minsf    26 2008-12-04 21:43 Examples -> /usr/share/example-content
drwxr-xr-x  2 minsf minsf  4096 2009-01-10 12:54 .fontconfig
drwx------  5 minsf minsf  4096 2009-01-11 07:50 .gconf
drwx------  2 minsf minsf  4096 2009-01-11 09:54 .gconfd
drwx------  4 minsf minsf  4096 2009-01-10 12:54 .gegl-0.0
drwxr-xr-x 22 minsf minsf  4096 2009-01-10 12:55 .gimp-2.6
-rw-r-----  1 minsf minsf     0 2009-01-11 09:41 .gksu.lock
drwx------ 16 minsf minsf  4096 2009-01-10 19:43 .gnome2
drwx------  2 minsf minsf  4096 2008-12-04 21:52 .gnome2_private
drwx------  2 minsf minsf  4096 2008-12-04 21:52 .gnupg
drwxr-xr-x  2 minsf minsf  4096 2009-01-01 18:11 .gstreamer-0.10
-rw-r--r--  1 minsf minsf   116 2009-01-10 09:47 .gtk-bookmarks
dr-x------  2 minsf minsf     0 2009-01-10 09:47 .gvfs
-rw-------  1 minsf minsf 10681 2009-01-10 09:47 .ICEauthority
drwxr-xr-x  2 minsf minsf  4096 2008-12-09 00:21 .icons
drwxr-xr-x  3 minsf minsf  4096 2008-12-16 15:41 .java
-rw-------  1 minsf minsf   536 2009-01-10 18:55 .lesshst
drwx------  3 minsf minsf  4096 2008-12-04 21:52 .local
drwx------  3 minsf minsf  4096 2008-12-12 09:45 .macromedia
drwx------  4 minsf minsf  4096 2008-12-05 10:12 .mozilla
drwxr-xr-x  2 minsf minsf  4096 2008-12-04 21:52 Music
drwxr-xr-x  3 minsf minsf  4096 2009-01-10 09:45 .nautilus
-rw-r--r--  1 minsf minsf  1095 2008-12-21 11:04 .nvidia-settings-rc
drwx------  3 minsf minsf  4096 2009-01-08 18:11 .openoffice.org2
drwxr-xr-x  2 minsf minsf  4096 2008-12-04 21:52 Pictures
-rw-r--r--  1 minsf minsf   675 2008-12-04 21:43 .profile
drwxr-xr-x  2 minsf minsf  4096 2008-12-04 21:52 Public
drwxr-xr-x  2 minsf minsf  4096 2008-12-04 21:52 .pulse
-rw-------  1 minsf minsf   256 2008-12-04 21:52 .pulse-cookie
drwx------  4 minsf minsf  4096 2008-12-12 11:13 .purple
-rw-------  1 minsf minsf  2693 2009-01-08 18:11 .recently-used
-rw-------  1 minsf minsf 38311 2009-01-10 19:43 .recently-used.xbel
drwx------  2 minsf minsf  4096 2008-12-09 00:18 .scim
-rw-r--r--  1 minsf minsf     0 2008-12-04 23:02 .sudo_as_admin_successful
drwxr-xr-x  2 minsf minsf  4096 2008-12-04 21:52 Templates
drwxr-xr-x  2 minsf minsf  4096 2008-12-09 00:21 .themes
drwx------  5 minsf minsf  4096 2009-01-01 17:39 .thumbnails
drwx------  2 minsf minsf  4096 2009-01-09 02:15 .tsclient
drwxr-xr-x  2 minsf minsf  4096 2008-12-04 23:21 .update-manager-core
drwx------  2 minsf minsf  4096 2008-12-17 15:55 .update-notifier
drwxr-xr-x  2 minsf minsf  4096 2008-12-04 21:52 Videos
drwxr-xr-x  2 minsf minsf  4096 2008-12-21 10:49 .wapi
-rw-------  1 minsf minsf   125 2009-01-10 09:47 .Xauthority
-rw-r--r--  1 minsf minsf   129 2008-12-21 10:37 .xscreensaver-getimage.cache
-rw-r--r--  1 minsf minsf  8842 2009-01-10 18:07 .xsession-errors

---

### Post by bhadotia on 2009-01-12
> **Captain_tux said:**
> Keep in mind that **any** file that begins with a dot is a hidden file and not necessarily only a config file.

Yes, of-course. For example the directories .cache and .thumbnails are both cache directories. Other hidden files which (in my knowledge) are not configuration files include .esd_auth, .gksu.lock.

And thanks for posting the output minsf, but I already had it all sorted out. :D

But again, if someone can point me to some manual that describes these system settings, I would much appreciate that.

---

### Post by bhadotia on 2009-01-12
Can someone, please, also post the content of ~/.lesshst file. I accidentally deleted this one when messing up all this permission stuff.
I don't know what this file is meant for. But I just want to be on the safe side (after recovering from a major system crash :D).

---

### Post by ajcham on 2009-01-12
> **bhadotia said:**
> Can someone, please, also post the content of ~/.lesshst file. I accidentally deleted this one when messing up all this permission stuff.
I don't know what this file is meant for. But I just want to be on the safe side (after recovering from a major system crash :D).

```
man less
&#8230;snip&#8230;
       LESSHISTFILE
              Name  of  the  history file used to remember search commands and
              shell commands between invocations of less.  If set  to  "-"  or
              "/dev/null",  a  history  file  is  not  used.   The  default is
              "$HOME/.lesshst" on Unix systems, "$HOME/_lesshst"  on  DOS  and
              Windows  systems,  or "$HOME/lesshst.ini" or "$INIT/lesshst.ini"
              on OS/2 systems.
&#8230;snip&#8230;
```
The contents of .lesshst are therefore unique to each user, so it's of no benefit anyone posting there own.  From what I've read it appears to be generated by the C shell - as I use bash, this would explain why I don't have such a file.

I wouldn't worry about it if I were you, from the description above it is highly doubtful you've lost anything of importance.

---

### Post by bhadotia on 2009-01-13
> **ajcham said:**
> ```
man less
…snip…
       LESSHISTFILE
              Name  of  the  history file used to remember search commands and
              shell commands between invocations of less.  If set  to  "-"  or
              "/dev/null",  a  history  file  is  not  used.   The  default is
              "$HOME/.lesshst" on Unix systems, "$HOME/_lesshst"  on  DOS  and
              Windows  systems,  or "$HOME/lesshst.ini" or "$INIT/lesshst.ini"
              on OS/2 systems.
…snip…
```
The contents of .lesshst are therefore unique to each user, so it's of no benefit anyone posting there own.  From what I've read it appears to be generated by the C shell - as I use bash, this would explain why I don't have such a file.

I wouldn't worry about it if I were you, from the description above it is highly doubtful you've lost anything of importance.

Thanks for the reply ajcham.:KS
You are right that this file is unique to every user. But it is not necessarily generated by Csh. I just opened a file with less in bash and searched for a word in it and this file was replaced in my home folder.

---

### Post by ajcham on 2009-01-13
Ah, that explains why I didn't have the file myself - I use **less** fairly often, but hadn't used the search function before.

Can't remember where I picked up the suggestion that it was related to Csh.

---

