---
title: "Help with a &quot;Home directory /home/username not ours.&quot;"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by Dangger on 2011-03-27
I have already followed all the instructions  [here]("http://ubuntuforums.org/showthread.php?p=6208727") and still every time I reboot it says:

```
username@username-laptop ~ $ alsamixer
username@username-laptop ~ $ sudo alsactl store
[sudo] password for username: 
Home directory /home/username not ours.

```

Thank you guys.

---

### Post by andrewthomas on 2011-03-27
Post the output of
 
```
 
ls -al /home/username

```

---

### Post by Dangger on 2011-03-27
> **andrewthomas said:**
> Post the output of
 
```
 
ls -al /home/username

```

Here it is:

```
total 408
drwxr-xr-x 68 username username  4096 2011-03-27 21:18 .
drwxr-xr-x  3 root    root     4096 2010-05-21 11:51 ..
drwx------  4 username username  4096 2010-06-18 16:54 .adobe
drwx------  2 username username  4096 2010-09-04 15:45 .aptitude
drwxr-xr-x  4 username username  4096 2010-09-22 20:42 .audacity-data
-rw-r--r--  1 username username  1164 2011-03-20 15:57 .banter.log
-rw-------  1 username username  7022 2011-03-27 19:28 .bash_history
-rw-r--r--  1 username username   220 2010-05-21 11:51 .bash_logout
drwx------ 18 username username  4096 2011-03-27 21:18 .cache
drwx------  3 username username  4096 2010-05-21 12:39 .compiz
drwxr-xr-x 28 username username  4096 2010-11-27 02:20 .config
drwx------  3 username username  4096 2010-05-21 12:00 .dbus
drwxr-xr-x  2 username username  4096 2010-09-04 15:45 .debtags
drwxr-xr-x  3 username username  4096 2011-03-20 22:42 Desktop
-rw-r--r--  1 username username    44 2011-03-27 21:18 .dmrc
drwxr-xr-x  5 username username  4096 2010-11-04 12:03 Documents
lrwxrwxrwx  1 username username    26 2011-01-01 15:27 Downloads -> /media/Documents/Downloads
drwxr-xr-x  4 username username  4096 2010-12-18 19:27 .dvdcss
-rw-------  1 username username    16 2010-05-21 12:00 .esd_auth
drwxr-xr-x  3 username username  4096 2010-05-22 08:37 .evolution
-rw-r--r--  1 username username 14124 2010-10-26 18:33 .face
drwxr-xr-x  2 username username  4096 2011-03-19 16:17 .fontconfig
drwxr-xr-x  4 username username  4096 2010-10-14 16:11 .Fontmatrix
drwxr-xr-x  2 username username  4096 2011-01-03 21:46 .fonts
-rw-r--r--  1 username username   141 2010-10-14 16:07 .fonts.conf
drwx------  5 username username  4096 2011-03-27 21:18 .gconf
drwx------  2 username username  4096 2011-03-27 21:19 .gconfd
drwx------  4 username username  4096 2010-05-22 08:13 .gegl-0.0
drwxr-xr-x 22 username username  4096 2011-01-05 15:28 .gimp-2.6
-rw-r-----  1 username username     0 2011-03-27 16:06 .gksu.lock
drwxr-xr-x  5 username username  4096 2010-08-10 10:42 .gnome
drwx------ 12 username username  4096 2010-12-30 11:41 .gnome2
drwx------  2 username username  4096 2010-05-21 12:00 .gnome2_private
drwxr-xr-x  2 username username  4096 2010-12-20 11:31 .gnome-desktop
drwxr-xr-x  2 username username  4096 2010-06-10 09:39 .gnomenu
drwx------  2 username username  4096 2010-12-22 00:41 .gnupg
drwxr-xr-x  2 username username  4096 2011-03-19 17:53 .gstreamer-0.10
-rw-r--r--  1 username username   150 2011-03-27 21:18 .gtk-bookmarks
dr-x------  2 username username     0 2011-03-27 21:18 .gvfs
drwxr--r--  2 username username  4096 2010-05-21 13:08 .hardinfo
drwxr-----  2 username username  4096 2010-05-25 12:12 .hplip
-rw-------  1 username username 46900 2011-03-27 21:18 .ICEauthority
drwxr-xr-x  3 username username  4096 2010-08-11 22:30 .icedteaplugin
drwxr-xr-x  2 username username  4096 2010-06-07 06:27 .icons
drwxr-xr-x  3 username username  4096 2010-09-04 15:55 .java
drwxr-xr-x  3 username username  4096 2010-05-21 13:10 .kde
-rw-------  1 username username    35 2010-10-25 10:50 .lesshst
drwxr-xr-x  7 username username  4096 2010-06-20 04:41 .linuxmint
drwxr-xr-x  3 username username  4096 2010-05-21 11:51 .local
drwx------  3 username username  4096 2010-12-20 13:51 .loki
drwxr-xr-x 13 username username  4096 2010-11-27 02:21 .lyx
drwx------  3 username username  4096 2010-05-21 12:30 .macromedia
drwxr-xr-x  3 username username  4096 2010-09-04 16:01 .minecraft
drwx------  5 username username  4096 2010-05-24 14:29 .mozilla
drwxr-xr-x  2 username username  4096 2011-03-20 16:58 .mplayer
drwxr-xr-x  2 username username  4096 2010-05-21 12:00 Music
drwxr-xr-x  2 username username  4096 2010-05-21 12:00 .nautilus
drwxr-xr-x  3 username username  4096 2010-05-24 14:29 .netscape
drwxr-xr-x  3 username username  4096 2010-06-07 06:21 .netx
-rw-r--r--  1 username username   128 2010-10-25 10:51 new file
drwxr-xr-x  3 username username  4096 2010-05-21 12:33 .openoffice.org
drwxr-xr-x 16 username username  4096 2010-12-30 09:32 .opera
drwxr-xr-x  2 username username  4096 2011-01-03 22:32 .pdfedit
drwxr-xr-x  2 username username  4096 2010-06-14 17:24 Pictures
drwx------  3 username username  4096 2010-05-21 12:29 .pki
-rw-r--r--  1 username username    37 2010-05-25 12:12 .printer-groups.xml
-rw-r--r--  1 username username   700 2010-06-01 18:01 .profile
drwxr-xr-x  2 username username  4096 2010-05-21 12:00 Public
drwx------  2 username username  4096 2011-03-27 21:18 .pulse
-rw-------  1 username username   256 2010-05-21 12:00 .pulse-cookie
drwxr-xr-x  2 username username  4096 2011-01-03 22:30 .qt
drwxr-xr-x  3 username username  4096 2010-05-21 12:58 .quakelive
drw-------  2 username username  4096 2010-05-27 19:56 .recently-used.xbel
drwx------  4 username username  4096 2011-03-20 19:29 .Skype
drwxr-xr-x  5 username username  4096 2010-06-13 15:57 .speech-dispatcher
drwx------  2 username username  4096 2010-12-22 00:41 .ssh
-rw-r--r--  1 username username     0 2010-05-21 12:00 .sudo_as_admin_successful
drwxr-xr-x  2 username username  4096 2010-05-21 12:00 Templates
drwxr-xr-x  3 username username  4096 2010-12-03 23:38 .texmf-var
drwxr-xr-x  3 username username  4096 2010-06-22 15:50 .themes
drwx------  4 username username  4096 2010-05-24 16:58 .thumbnails
-rw-r--r--  1 username username  1300 2010-10-11 21:02 .usbcreator.log
drwxr-xr-x  2 username username  4096 2010-05-21 12:00 Videos
drwxr-xr-x  3 username username  4096 2010-10-22 18:31 .VirtualBox
drwx------  4 username username  4096 2010-10-26 12:09 .xchat2
drwxr-xr-x  2 username username  4096 2010-06-22 11:30 .xine
-rw-r--r--  1 username username   797 2011-03-20 20:00 .xscreensaver-getimage.cache
-rw-------  1 username username  2368 2011-03-27 21:18 .xsession-errors
-rw-------  1 username username  4855 2011-03-27 19:28 .xsession-errors.old

```

---

### Post by andrewthomas on 2011-03-27
Why did you change your username to username?
 
You were supposed to substitute your username for "username"
 
Or did you create the original user when you installed Ubuntu with the username of username?

---

### Post by Dangger on 2011-03-27
> **andrewthomas said:**
> Why did you change your username to username?
 
You were supposed to substitute your username for "username"
 
Or did you create the original user when you installed Ubuntu with the username of username?


My username is not username. My username is something else I manually changed it to appear as username to be more generic.

---

