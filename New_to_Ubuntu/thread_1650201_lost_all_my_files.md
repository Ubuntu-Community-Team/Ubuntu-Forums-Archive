---
title: "lost all my files"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by drymou99 on 2010-12-21
Background,yesterday I lost the bar at the top of the screen (applications places system etc etc ) I then looked to the ubuntu forums for a solution to the problem.
I tried......... gcontfool--recursive-unset/apps/panel pkill gnome-panel
This action brought back the bar but unfortunately it also wiped out all my files, bookmarks passwords etc.
Please can someone advise are these lost forever or is there a way back.

---

### Post by Verbeck on 2010-12-21
you mean there's nothing on the panel?
then right click>add to panel>
clock
indicator applet
indicator applet session
menu bar
notification area

---

### Post by drymou99 on 2010-12-21
The panel is back and working fine.
But I have no files

---

### Post by Verbeck on 2010-12-21
thats strange..
could you post the output of the following from a terminal(applications>accessories>terminal)
```
ls -la ~/
ls -la ~/Desktop
```

---

### Post by drymou99 on 2010-12-22
user@user-desktop:~$ ls -la ~/
total 192
drwxr-xr-x 36 user user 4096 2010-12-22 12:57 .
drwxr-xr-x  3 root root 4096 2010-07-05 22:57 ..
drwx------  3 user user 4096 2010-12-20 18:23 .adobe
-rw-------  1 user user  245 2010-12-22 12:30 .bash_history
drwxr-xr-x  7 user user 4096 2010-12-22 12:57 .cache
drwx------  3 user user 4096 2010-12-20 17:48 .compiz
drwxr-xr-x 12 user user 4096 2010-12-21 14:31 .config
drwx------  3 user user 4096 2010-12-20 18:05 .dbus
drwxr-xr-x  2 user user 4096 2010-12-21 17:11 Desktop
-rw-r--r--  1 user user   27 2010-12-22 12:57 .dmrc
drwxr-xr-x  2 user user 4096 2010-12-20 18:05 Documents
drwxr-xr-x  2 user user 4096 2010-12-20 18:05 Downloads
-rw-------  1 user user   16 2010-12-20 17:45 .esd_auth
drwxr-xr-x  7 user user 4096 2010-12-20 17:46 .evolution
drwx------  5 user user 4096 2010-12-22 12:57 .gconf
drwx------  2 user user 4096 2010-12-22 12:58 .gconfd
-rw-r-----  1 user user    0 2010-12-21 14:59 .gksu.lock
drwx------  9 user user 4096 2010-12-22 12:31 .gnome2
drwx------  2 user user 4096 2010-12-20 17:46 .gnome2_private
drwx------  2 user user 4096 2010-12-21 14:16 .gnupg
drwxr-xr-x  2 user user 4096 2010-12-20 18:58 .gstreamer-0.10
-rw-r--r--  1 user user  132 2010-12-22 12:57 .gtk-bookmarks
dr-x------  2 user user    0 2010-12-22 12:57 .gvfs
-rw-------  1 user user 1710 2010-12-22 12:57 .ICEauthority
drwxr-xr-x  2 user user 4096 2010-12-20 18:45 .icons
drwx------  3 user user 4096 2010-12-21 14:18 .kde
drwx------  3 user user 4096 2010-12-20 18:05 .local
drwx------  3 user user 4096 2010-12-20 18:23 .macromedia
drwx------  4 user user 4096 2010-12-20 18:05 .mozilla
drwxr-xr-x  2 user user 4096 2010-12-21 14:20 Music
drwxr-xr-x  2 user user 4096 2010-12-20 18:05 .nautilus
drwxr-xr-x  3 user user 4096 2010-12-20 19:56 .openoffice.org
drwxr-xr-x  2 user user 4096 2010-12-20 18:05 Pictures
-rw-r--r--  1 user user   37 2010-12-20 18:15 .printer-groups.xml
drwxr-xr-x  2 user user 4096 2010-12-20 18:05 Public
drwx------  2 user user 4096 2010-12-22 12:57 .pulse
-rw-------  1 user user  256 2010-12-20 17:45 .pulse-cookie
-rw-------  1 user user 9160 2010-12-22 12:31 .recently-used.xbel
drwx------  2 user user 4096 2010-12-21 14:16 .ssh
-rw-r--r--  1 user user    0 2010-12-20 18:19 .sudo_as_admin_successful
drwxr-xr-x  2 user user 4096 2010-12-20 18:05 Templates
drwxr-xr-x  2 user user 4096 2010-12-20 18:45 .themes
drwx------  4 user user 4096 2010-12-20 18:45 .thumbnails
drwxrwxr-x  2 user user 4096 2010-12-20 18:16 Ubuntu One
drwx------  2 user user 4096 2010-12-20 18:06 .update-notifier
drwxr-xr-x  2 user user 4096 2010-12-20 18:05 Videos
-rw-------  1 user user 2421 2010-12-22 12:58 .xsession-errors
-rw-------  1 user user 4485 2010-12-22 12:31 .xsession-errors.old
user@user-desktop:~$ ls -la ~/desktop
ls: cannot access /home/user/desktop: No such file or directory
user@user-desktop:~$ 

Your results I do hope these are of use
Thanks

---

### Post by Elfy on 2010-12-22
First - there is no desktop it is Desktop - case matters in Linux

Second - doesn't look like there files missing - however you are going to need to be more specific perhaps.

What files are you talking about?

---

### Post by QLee on 2010-12-22
[QUOTE=drymou99]Background,yesterday I lost the bar at the top of the screen
...
Please can someone advise are these lost forever or is there a way back.[/QUOTE]

As forestpiskie wrote, your home looks pretty normal.

What might help would be if you explained what you did to lose the main panel.

It's very likely that the "way back" is to reverse what you did to lose it.

---

### Post by NightwishFan on 2010-12-22
The gconftool in no way removes such data, and Firefox does not even use gconf, the only way that you got rid of such settings was by running a rm command while in your home folder.

---

### Post by Verbeck on 2010-12-22
as others have already said, the file structure looks normal.
btw, when was the user account created?
also, did you do anything other than what you mentioned in the first post?

---

### Post by Elfy on 2010-12-22
I wonder if the original issue was caused by a full / - could explain some strange issues. 

Does this show it as more or less full - check the Use % column

```
df -h /
```

Edit - anyway I guess we're all chasing moonbeams till the OP comes back :)

---

### Post by drymou99 on 2010-12-22
1 missing files ......all files pics documents ever thing as gone

2 I think I right clicked on USER and removed it.

3  user@user-desktop:~$ df -h /
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             456G  4.9G  428G   2% /
user@user-desktop:~$ 

4 I don't I did anything else

More info I have also lost almost ever thing I had on a second hard drive from an old computer.

---

### Post by Griffiss on 2010-12-22
It might be the case that you haven't lost any files, only that you can't find them. How did you use to find them? Do you know what folder these files were kept in?

---

### Post by NightwishFan on 2010-12-22
> **drymou99 said:**
> 2 I think I right clicked on USER and removed it.

:p

I think this might have been what happened. :/

---

### Post by Verbeck on 2010-12-22
> **NightwishFan said:**
> :p

I think this might have been what happened. :/
but how could he do that from a normal nautilus :confused:
any modifications are greyed out

---

