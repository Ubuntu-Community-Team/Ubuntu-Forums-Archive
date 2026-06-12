---
title: "Doesn't seem to want to save settings between sessions."
date: 2010-07-23
forum: New to Ubuntu
---

### Post by Vilicus on 2010-07-23
I'm not sure if this is program specific or if its Ubuntu itself, but I'm getting a little annoyed with certain settings not being saved between settings.

I'm using Ubuntu Netbook 10.04 on an HP 110-3015DX, dual boot with Windows 7 Starter.  The two instances I've noticed so far take place within Empathy and XChat.

In the case of Empathy, anytime I logout and log back in, restart or whatever it does not remember I've ignored people.  It continues to ask me if I want to add so-and-so to my contact list every time and every time I say no.  It doesn't seem to remember that I've said no previously.  Everything else I've done in the program seems to work fine, it remembers my accounts, it remembers my contact list.  I'm worried someones going to ask for an invite and I'll say yes and it wont remember that either.

In the case of XChat, every time I logout and log back in, or restart it doesn't remember that I've checked the skip the server list box.  I shouldn't see that list every time i open up XChat but it pops up and its unchecked again.  It also doesn't remember the Nickname I've put in.  I'll change the nick and sure enough when i reopen the program it doesn't save.

I've managed to find something in the settings that saves a session but I believe that just opens the programs that were open when you last logged off.  This is fine and all but I'm worried somethings in the program themselves that doesn't want to save the changes.

---

### Post by matrixblue on 2010-07-23
run "ls -al" from the terminal in your home directory and post the output here.

The problem could be with insufficient access rights to the configuration files for those programs.

I'm assumuing that Ubuntu is installed and not running from a Live CD or Live USB

---

### Post by Vilicus on 2010-07-23
Yes this is a brand new install to the hard drive.  I'm the only one using it so I dont know what its smoking about privileges as the admin should have full access you'd think.


jason@Jason-Netbook:~$ ls -al
total 292
drwxr-xr-x 34 jason jason  4096 2010-07-23 11:56 .
drwxr-xr-x  3 root  root   4096 2010-07-24 06:46 ..
drwx------  3 jason jason  4096 2010-07-22 18:19 .adobe
-rw-------  1 jason jason   507 2010-07-22 23:55 .bash_history
-rw-r--r--  1 jason jason   220 2010-07-24 06:46 .bash_logout
-rw-r--r--  1 jason jason  3103 2010-07-24 06:46 .bashrc
drwx------ 12 jason jason  4096 2010-07-23 11:21 .cache
drwxr-xr-x 16 jason jason  4096 2010-07-23 11:42 .config
-rw-r--r--  1 jason jason  1424 2010-07-22 20:28 convertTime.py
drwx------  3 jason jason  4096 2010-07-24 06:58 .dbus
drwxr-xr-x  2 jason jason  4096 2010-07-24 06:58 Desktop
drwxr-xr-x 11 jason jason  4096 2010-07-24 06:51 Documents
drwxr-xr-x  2 jason jason  4096 2010-07-24 06:58 Downloads
-rw-------  1 jason jason    16 2010-07-24 06:58 .esd_auth
drwxr-xr-x  3 jason jason  4096 2010-07-22 14:10 .evolution
-rw-r--r--  1 jason jason   179 2010-07-24 06:46 examples.desktop
-rw-r--r--  1 jason jason   199 2010-07-22 20:19 findRange.py
drwxr-xr-x  2 jason jason  4096 2010-07-22 14:46 .fontconfig
drwxr-xr-x  5 jason jason  4096 2010-07-23 11:20 .gconf
drwx------  2 jason jason  4096 2010-07-23 12:54 .gconfd
-rw-r-----  1 jason jason     0 2010-07-23 12:38 .gksu.lock
drwxr-xr-x  6 jason jason  4096 2010-07-23 11:42 .gnome2
drwx------  2 jason jason  4096 2010-07-24 06:58 .gnome2_private
drwxr-xr-x  2 jason jason  4096 2010-07-22 15:01 .gstreamer-0.10
-rw-r--r--  1 jason jason   137 2010-07-23 11:20 .gtk-bookmarks
dr-x------  2 jason jason     0 2010-07-23 11:20 .gvfs
-rw-------  1 jason jason  2060 2010-07-23 11:20 .ICEauthority
drwxr-xr-x  2 jason jason  4096 2010-07-22 18:40 .idlerc
-rw-r--r--  1 jason jason 27869 2010-07-24 06:46 ihaveyounow_1024-600-512x300.jpg
drwxr-xr-x  3 jason jason  4096 2010-07-22 18:19 .kde
drwx------  3 jason jason  4096 2010-07-24 06:58 .local
drwx------  3 jason jason  4096 2010-07-22 18:19 .macromedia
-rw-r--r--  1 jason jason   117 2010-07-22 19:57 Midterm Review - Introduction to Programming
drwx------  3 jason jason  4096 2010-07-22 14:10 .mission-control
drwxr-xr-x  4 jason jason  4096 2010-07-22 14:05 .mozilla
drwxr-xr-x  6 jason jason  4096 2010-07-24 06:51 Music
drwxr-xr-x  2 jason jason  4096 2010-07-24 06:58 .nautilus
drwxr-xr-x 21 jason jason  8192 2010-07-22 19:42 Pictures
drwx------  3 jason jason  4096 2010-07-22 18:19 .pki
-rw-r--r--  1 jason jason   675 2010-07-24 06:46 .profile
drwxr-xr-x  2 jason jason  4096 2010-07-24 06:58 Public
drwx------  2 jason jason  4096 2010-07-23 11:20 .pulse
-rw-------  1 jason jason   256 2010-07-24 06:58 .pulse-cookie
-rw-------  1 jason jason  5194 2010-07-23 11:56 .recently-used.xbel
-rw-r--r--  1 jason jason     0 2010-07-22 14:00 .sudo_as_admin_successful
drwxr-xr-x  2 jason jason  4096 2010-07-24 06:58 Templates
drwx------  3 jason jason  4096 2010-07-22 19:42 .thumbnails
drwx------  2 jason jason  4096 2010-07-22 14:00 .update-notifier
drwxr-xr-x  3 jason jason  4096 2010-07-22 19:42 Videos
drwx------  4 jason jason  4096 2010-07-22 23:30 .xchat2
-rw-------  1 jason jason 33305 2010-07-23 12:55 .xsession-errors
-rw-------  1 jason jason 32932 2010-07-23 08:03 .xsession-errors.old

---

### Post by matrixblue on 2010-07-23
Try this. In terminal run: sudo apt-get purge empathy then sudo apt-get install empathy and try again

If it works try the same with Xchat

---

### Post by Vilicus on 2010-07-23
That did not solve anything.  I did the purge and the install and rebooted, and got the same result, it forgot all my settings.  Yet again I had to ignore the same set of people.  Its like its remembering some settings and not others because it can remember my accounts and its able to sign right into those.  It just doesn't remember who I've ignored.  Same goes for XChat, it remembers the server and channel i connect to, it remembers my password, but the nick doesn't get remembered.

---

### Post by matrixblue on 2010-07-23
I'm out of ideas maybe someone with more experience those programs would be able to assist better.

I was thinking it was a problem with writing to the config file but that doesn't seem to be the case

---

### Post by Vilicus on 2010-07-23
Yeah its not like its breaking the OS, its just a minor annoyance I can live with for now.  Just takes a minute to re-ignore, and edit the nicks to get it back to the way it was.  Thanks for trying.

---

