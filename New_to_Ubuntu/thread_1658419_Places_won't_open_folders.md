---
title: "Places won't open folders"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by SuperFreak on 2011-01-02
I am not able to open any of the directories under "Places" except Computer and Network. I have no trouble accessing files either through Computer under places or through a number of shortcuts on the desktop (for example Music). I have been running 10.10 for a few months with only a few problems like this cropping up. I have tried changing "open with" to file browser with folders under Computer but it doesn't fix it.

---

### Post by wojox on 2011-01-02
Open your terminal and run and post back:

```
cat .local/share/applications/mimeapps.list
```

---

### Post by HTMLCrazy on 2011-01-02
Try rebooting the computer at least once. If it doesn't work, do it again. If it doesn't work after the second time, try setting the opening program to Archive Manager.

---

### Post by rburkartjo on 2011-01-02
super try this

i know how to fix. i did the samething the other day. this should fix advise if it doesnt. go to places/computer/c lick computer when computer open click system than RIGHT click home
then open with select other application. scroll the list and select file manager and  LEFT double click that should do it. (in order words get to you home folder by accessing it though computer and then do the last line of the fix. yea i had my home folder and all any bookmarks opening in opera.

---

### Post by SuperFreak on 2011-01-02
Here is my terminal output I have already tried the other solutions to no avail (except it was file browser not file manager


[Added Associations]
application/x-shellscript=gedit.desktop;
x-content/blank-cd=brasero.desktop;kde4-k3b.desktop;
x-content/video-dvd=vlc.desktop;
x-content/audio-cdda=rhythmbox.desktop;
x-content/audio-player=rhythmbox.desktop;
application/x-executable=sun-java6-java.desktop;gedit.desktop;
application/x-win-lnk=wine-extension-txt.desktop;
audio/mpeg=nautilus-browser.desktop;
inode/directory=userapp-cover-thumbnailer-0H2SNV.desktop;nautilus-browser.desktop;wine.desktop;
x-content/image-dcf=totem.desktop;
application/x-extension-link=nautilus-browser.desktop;

---

### Post by wojox on 2011-01-02
Edit that file and replace this

```
inode/directory=userapp-cover-thumbnailer-0H2SNV.desktop;nautilus-browser.desktop;wine.desktop;
```


With this

```
inode/directory=nautilus-folder-handler.desktop;
```

You may have to log out and back in.

---

### Post by SuperFreak on 2011-01-02
Thank you very much, it worked. I had earlier been trying to use cover-thumbnailer and I guess that is why the file got messed up

---

### Post by wojox on 2011-01-02
Your welcome.

---

### Post by Psion23 on 2011-01-06
Pardon me, but I have a similar problem. However, while the terminal script given above works fine, I cannot find the file to edit it anywhere. I don't seem to have a folder labeled "local/share" that I can find. Searching for mimeapps returns nothing.:confused:

---

### Post by mattblowers on 2011-02-20
I found this.  It works great:

gedit ~/.local/share/applications/mimeapps.list
Change the line starting:
inode/directory=
to read:
inode/directory=nautilus-folder-handler.desktop;

---

### Post by sabutuga on 2011-02-20
> **wojox said:**
> Edit that file and replace this

```
inode/directory=userapp-cover-thumbnailer-0H2SNV.desktop;nautilus-browser.desktop;wine.desktop;
```
With this

```
inode/directory=nautilus-folder-handler.desktop;
```You may have to log out and back in.

Thank you Wojox, I had the same problem and this work great from

---

### Post by cheapodonuts on 2011-09-19
Oooo! 8 month's since the last post, I hope our good friend wojox is still subbed to this thread.!

 I have the same problem as superfreak. The issue started while I was running 10.04 and, surprisingly it remained after upgrading to 11.04
 It began while I was messing around with Rythmbox.

 So my terminal output is not quite the same:-

cheapo@cheapo-desktop:~$ sudo cat .local/share/applications/mimeapps.list
[sudo] password for cheapo: 

[Added Associations]
inode/directory=nautilus-autorun-software.desktop;nautilus-folder-handler.desktop;eog.desktop;nautilus-browser.desktop;
image/x-olympus-orf=f-spot-view.desktop;gimp.desktop;
application/x-7z-compressed=file-roller.desktop;mount-archive.desktop;
x-content/audio-cdda=rhythmbox.desktop;
x-content/video-dvd=vlc.desktop;
x-content/audio-player=rhythmbox.desktop;
x-content/image-dcf=f-spot-import.desktop;
audio/mpeg=totem.desktop;audacious2-gtkui.desktop;vlc.desktop;soundconverter.desktop;audacity.desktop;rhythmbox.desktop;audacious2.desktop;
application/x-extension-volume=rhythmbox.desktop;
audio/x-wav=totem.desktop;audacious2-gtkui.desktop;vlc.desktop;soundconverter.desktop;audacity.desktop;audacious2.desktop;rhythmbox.desktop;
application/x-trash=gedit.desktop;
video/ogg=totem.desktop;vlc.desktop;gnome-mplayer.desktop;soundconverter.desktop;rhythmbox.desktop;audacious2.desktop;audacity.desktop;Kino.desktop;
text/plain=nautilus-browser.desktop;

[Default Applications]
text/plain=nautilus-browser.desktop
cheapo@cheapo-desktop:~$ 


Thankx in advance, Pete.  ):P

---

### Post by Krytarik on 2011-09-19
> **cheapodonuts said:**
> cheapo@cheapo-desktop:~$ sudo cat .local/share/applications/mimeapps.list
[sudo] password for cheapo: 

[Added Associations]
inode/directory=nautilus-autorun-software.desktop;nautilus-folder-handler.desktop;eog.desktop;nautilus-browser.desktop;
...
Well, besides that you don't need to use 'sudo' here - luckily, the output nevertheless reflects your own profile settings -, you can simply follow the very same advice, as your respective association settings are similarly scrumbled. ;-)

However, I, personally, would just remove the whole file, as there are many faulty associations in it. It would be re-created automatically. And any associations not included in it are defaulting anyway.

Greetings.

---

### Post by cheapodonuts on 2011-09-20
Thanks for your response Krytarik. 
 I had to use sudo as I apparently don't have permission to open the file otherwise. Sorry if it seems a foolish question, but what is the correct way to remove the file? I don't normally mess with that type of thing. I prefer the GUI, so I don't use the terminal often enough to learn anything useful. :D

Pete.

---

### Post by Krytarik on 2011-09-20
> **cheapodonuts said:**
> I had to use sudo as I apparently don't have permission to open the file otherwise.
Really!? If that's the case, it would indicate a pretty serious and weird general issue with your home directory! Please post the output of:
```
ls -al ~/.local/share/applications/mimeapps.list
```And to also get general picture of your home directory:
```
ls -al ~/
```Please use the #-button in the editor to enclose the outputs in code boxes.

> **cheapodonuts said:**
> what is the correct way to remove the file?
Usually, it would be just:
```
rm ~/.local/share/applications/mimeapps.list
```

---

### Post by cheapodonuts on 2011-09-27
Hi Krytarik, thanx again for helping out.

Output 1:
cheapo@cheapo-desktop:~$ ls -al ~/.local/share/applications/mimeapps.list 
-rw-r--r-- 1 cheapo admin 1143 2011-09-24 14:44 /home/cheapo/.local/share/applications/mimeapps.list
cheapo@cheapo-desktop:~$ 

Not sure what you mean about the editor # button

Output 2:

cheapo@cheapo-desktop:~$ ls -al ~/
total 560
drwxr-xr-x 70 cheapo cheapo  4096 2011-09-27 18:48 .
drwxr-xr-x  3 root   root    4096 2011-04-10 15:52 ..
drwx------  3 cheapo cheapo  4096 2011-04-10 16:56 .adobe
drwxr-xr-x  5 cheapo cheapo  4096 2011-09-16 22:18 .audacity-data
-rw-------  1 cheapo cheapo  2231 2011-09-27 19:24 .bash_history
-rw-r--r--  1 cheapo cheapo   220 2011-04-10 15:52 .bash_logout
-rw-r--r--  1 cheapo cheapo  3180 2011-04-10 15:52 .bashrc
drwxr-xr-x  3 cheapo cheapo  4096 2011-05-14 15:45 beast
drwxr-xr-x  2 cheapo cheapo  4096 2011-05-08 18:18 .beast
drwx------  2 cheapo cheapo  4096 2011-04-24 09:10 .bogofilter
-rw-r--r--  1 cheapo cheapo   488 2011-05-08 18:18 .bserc
drwx------ 24 cheapo cheapo  4096 2011-09-27 18:48 .cache
-rw-r--r--  1 cheapo cheapo   239 2011-09-22 17:49 .cairo-clockrc
drwxr-xr-x  3 cheapo admin   4096 2011-09-17 15:36 .cddbslave
drwx------  3 cheapo cheapo  4096 2011-04-10 16:24 .compiz
drwxr-xr-x 37 cheapo cheapo  4096 2011-09-23 15:23 .config
drwx------  3 cheapo cheapo  4096 2011-04-10 15:57 .dbus
drwxr-xr-x 11 cheapo cheapo  4096 2011-09-27 07:03 Desktop
-rw-r--r--  1 cheapo admin     63 2011-09-27 18:48 .dmrc
drwxr-xr-x 24 cheapo cheapo  4096 2011-09-03 21:13 Documents
drwxr-xr-x  2 cheapo cheapo  4096 2011-09-14 18:35 Downloads
drwxr-xr-x  4 cheapo cheapo  4096 2011-06-07 20:09 .dvdcss
drwxr-xr-x  2 cheapo cheapo  4096 2011-04-25 12:59 dwhelper
-rw-------  1 cheapo cheapo    16 2011-04-10 15:57 .esd_auth
-rw-r--r--  1 cheapo cheapo   167 2011-04-10 15:52 examples.desktop
drwxr-xr-x  2 cheapo cheapo 36864 2011-09-24 13:40 .fontconfig
drwx------  3 cheapo cheapo  4096 2011-07-10 13:16 .FontForge
drwx------  5 cheapo cheapo  4096 2011-09-27 18:48 .gconf
drwx------  2 cheapo cheapo  4096 2011-09-27 19:24 .gconfd
drwx------  4 cheapo cheapo  4096 2011-04-10 21:22 .gegl-0.0
drwxr-xr-x 22 cheapo cheapo  4096 2011-09-24 15:09 .gimp-2.6
-rw-r-----  1 cheapo cheapo     0 2011-09-24 17:35 .gksu.lock
drwxr-xr-x  2 cheapo cheapo  4096 2011-05-15 09:01 .gnaural
drwx------ 12 cheapo cheapo  4096 2011-09-25 18:55 .gnome2
drwx------  2 cheapo cheapo  4096 2011-04-10 15:57 .gnome2_private
drwxr-xr-x  6 cheapo cheapo  4096 2011-08-29 10:10 gnome-video-effects
drwx------  2 cheapo cheapo  4096 2011-07-20 18:36 .gnupg
drwx------  4 cheapo cheapo  4096 2011-07-22 19:32 .googleearth
drwxr-xr-x  2 cheapo cheapo  4096 2011-04-16 13:22 .gpilotd
-rw-r--r--  1 cheapo cheapo     4 2011-04-16 13:22 .gpilotd.pid
drwxr-xr-x  2 cheapo cheapo  4096 2011-09-24 17:43 .gstreamer-0.10
-rw-r--r--  1 cheapo admin    206 2011-09-27 18:48 .gtk-bookmarks
-rw-r--r--  1 cheapo cheapo  2079 2011-07-06 07:04 .guvcviewrc
dr-x------  2 cheapo admin      0 2011-09-27 18:48 .gvfs
drwxr-xr-x  3 cheapo cheapo  4096 2011-05-14 15:42 .hydrogen
-rw-------  1 cheapo cheapo 79100 2011-09-27 18:48 .ICEauthority
drwxr-xr-x  4 cheapo admin   4096 2011-09-22 21:44 .icedtea
drwxr-xr-x  3 cheapo cheapo  4096 2011-05-01 22:50 .icedteaplugin
drwxr-xr-x  2 cheapo cheapo  4096 2011-04-10 15:57 .icons
drwxr-xr-x  3 cheapo cheapo  4096 2011-04-23 20:42 .java
drwx------  3 cheapo cheapo  4096 2011-04-28 15:59 .kde
drwx------  2 cheapo cheapo  4096 2011-07-10 13:39 .kino-history
-rw-r--r--  1 cheapo cheapo  2971 2011-07-10 13:39 .kinorc
drwxr-xr-x  3 cheapo admin   4096 2011-09-24 13:40 .libreoffice
drwxr-xr-x  5 cheapo cheapo  4096 2011-04-19 14:50 lmms
-rw-r--r--  1 cheapo cheapo   966 2011-05-14 15:41 .lmmsrc.xml
drwx------  3 cheapo cheapo  4096 2011-04-10 19:45 .local
drwx------  3 cheapo cheapo  4096 2011-04-10 16:56 .macromedia
drwx------  3 cheapo cheapo  4096 2011-04-23 13:43 .mission-control
drwx------  4 cheapo cheapo  4096 2011-04-10 16:25 .mozilla
drwxr-xr-x  2 cheapo cheapo  4096 2011-04-10 16:49 .mplayer
-rw-r--r--  1 cheapo cheapo     6 2011-04-29 18:46 .musePrj
drwxr-xr-x  5 cheapo cheapo  4096 2011-05-13 16:13 Music
drwxr-xr-x  2 cheapo cheapo  4096 2011-04-10 15:57 .nautilus
drwxr-xr-x  3 cheapo cheapo  4096 2011-05-01 16:51 .netx
drwxr-xr-x  3 cheapo cheapo  4096 2011-04-10 19:45 .openoffice.org
drwxr-xr-x  3 cheapo cheapo  4096 2011-05-06 06:55 opt
drwxr-xr-x  3 cheapo cheapo  4096 2011-09-23 21:54 outRec
drwxr-xr-x 36 cheapo cheapo  4096 2011-08-19 18:22 Pictures
drwx------  3 cheapo cheapo  4096 2011-06-02 18:59 .pki
-rw-r--r--  1 cheapo cheapo    37 2011-07-28 22:29 .printer-groups.xml
-rw-r--r--  1 cheapo cheapo   675 2011-04-10 15:52 .profile
drwxr-xr-x  2 cheapo cheapo  4096 2011-04-10 15:57 Public
drwx------  2 cheapo admin   4096 2011-09-27 18:48 .pulse
-rw-------  1 cheapo cheapo   256 2011-04-10 15:57 .pulse-cookie
drwxr-xr-x  2 cheapo cheapo  4096 2011-04-28 21:03 .qt
-rw-------  1 cheapo cheapo  1153 2011-04-30 13:23 .recently-used
drwx------  2 cheapo cheapo  4096 2011-04-10 15:57 .ssh
-rw-r--r--  1 cheapo cheapo     0 2011-04-10 16:03 .sudo_as_admin_successful
drwxr-xr-x  2 cheapo cheapo  4096 2011-04-10 15:57 Templates
drwxr-xr-x  2 cheapo cheapo  4096 2011-05-01 14:10 .themes
drwx------  5 cheapo cheapo  4096 2011-04-15 15:20 .thumbnails
drwxrwxr-x  2 cheapo admin   4096 2011-09-23 15:23 Ubuntu One
-rw-r--r--  1 cheapo cheapo   711 2011-04-30 17:36 .ufrawrc
drwxr-xr-x  2 cheapo cheapo  4096 2011-04-10 15:58 .update-manager-core
drwx------  2 cheapo cheapo  4096 2011-04-10 15:57 .update-notifier
-rw-r--r--  1 cheapo cheapo  2426 2011-06-05 14:00 .usbcreator.log
drwxr-xr-x 10 cheapo cheapo  4096 2011-06-05 14:02 Videos
drwxr-xr-x  2 cheapo cheapo  4096 2011-04-28 20:53 .wapi
-rw-r--r--  1 cheapo cheapo     2 2011-05-01 19:35 .windows-serial
drwxr-xr-x  4 cheapo cheapo  4096 2011-05-07 18:28 .wine
drwxr-xr-x  2 cheapo cheapo  4096 2011-06-05 13:12 .winff
drwxr-xr-x  4 cheapo cheapo  4096 2011-06-11 09:02 wxcam-1.1
drwxr-xr-x  2 cheapo cheapo  4096 2011-07-11 19:01 .xine
-rw-------  1 cheapo admin   8476 2011-09-27 19:22 .xsession-errors
-rw-------  1 cheapo admin  62282 2011-09-27 07:15 .xsession-errors.old
cheapo@cheapo-desktop:~$

I might just order a CD from the Linux Shop and do a fresh install, as the upgrade has obviously saved settings etc which were faulty in the first place..

---

### Post by Krytarik on 2011-09-27
> **cheapodonuts said:**
> I might just order a CD from the Linux Shop and do a fresh install, as the upgrade has obviously saved settings etc which were faulty in the first place..
Nah, just try this for a start:
```
sudo chown cheapo:cheapo -R /home/cheapo
rm /home/cheapo/.local/share/applications/mimeapps.list
```
Apart from "mimeapps.list" being filed under the group "admin", everything else looks fine, at this first glance.

---

### Post by cheapodonuts on 2011-09-29
Thanks Krytarik, that worked. :) :) :) :) :)


Have several donuts on me! 


[IMG]http://i81.photobucket.com/albums/j226/chashugh/Donuts/donutsdetail.jpg[/IMG]



Pete.

---

### Post by Krytarik on 2011-09-29
Hmmm, these are looking tasty, thanks! :D

---

### Post by cheapodonuts on 2011-09-29
You have to go jogging after eating them. ;)

---

