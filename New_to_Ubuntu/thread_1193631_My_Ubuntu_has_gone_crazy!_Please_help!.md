---
title: "My Ubuntu has gone crazy! Please help!"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by Gp. on 2009-06-21
Okay, I restarted Ubuntu and I got a tone of error messages.
Finally managed to boot, and everything is screwed. My desktop icons have dissapeared, whenever I try to access something it says an application doesn't exist?
But it's just opening a folder for example? Seems like nautilus is screwed or something.
Everything is just messed up like it corrupted the **** out of itself.

And what about all my files! :|

Please help!

---

### Post by s3a on 2009-06-21
Does it boot to a terminal screen at least?

---

### Post by Gp. on 2009-06-21
All those errors just came up and I waited ages, it failed to load just with the Ubuntu logo and the progress bar moving left to right, so I restarted, got a DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER, so I turned off and on again, ubuntu gave fewer errors and after a bit of a wait, finally booted and everything is not working properly.

---

### Post by Gp. on 2009-06-21
***Update***

Okay well for some crazy reason Nautilus was removed!
I just reinstalled it in Synaptic and that problem is gone away.
The errors I posted haven't come back since...

Anyone have a clue what just happened to my system? lol

---

### Post by Sealbhach on 2009-06-21
You must have done a sudden shutdown and broke the Nautilus package. I was going to suggest installing Nautilus. Now we need to see if you boot up OK next time. Maybe boot up in safe mode, or recovery mode or whatever it's called.

.

---

### Post by Gp. on 2009-06-21
Okay I just found something VERY weird.
In my synaptic manager, I looked at history.

Removed the following packages:
amarok
gnome-mplayer
gvfs-backends
kdebase-runtime
kdebase-runtime-bin-kde4
kdemultimedia-kio-plugins
khelpcenter4
kolf
kollision
konquest
libgnomevfs2-extra
libkcddb4
libkdegames5
libqt4-webkit
libsmbclient
libxine1
libxine1-misc-plugins
mozilla-plugin-vlc
mplayer
nautilus
nautilus-share
phonon
phonon-backend-xine
python-samba
python-smbc
system-config-printer-common
system-config-printer-gnome
vlc
vlc-nox
vlc-plugin-esd
xmms2-plugin-all
xmms2-plugin-gvfs
xmms2-plugin-smb


ALL THOSE WERE REMOVED? I didnt do that! :|!
My system had a mind of it's own to just remove all those packages! 
Can anyone explain this!!!

---

### Post by s3a on 2009-06-21
Did you do sudo apt-get autoremove by any chance?

---

### Post by Gp. on 2009-06-21
Nope!
I was installing Samba from Add/Remove...
after that everything went to hell.
Did the add/remove manager conflict with what Synaptic had installed?
Bug?
It's like my system restored it to a point before I installed all of that.
Does ubuntu have an auto restore that kicks in on errors like the ones in the screenshots or something?
I cant figure this out.
I just had to manually reinstall all those packages...

And is there an Ubuntu System Restore (GUI) feature incase this happens again?

---

### Post by s3a on 2009-06-21
There is a terminal way to "restore" your system by installing what was recently removed. I don't recall the command by memory so I'll go find it and post back when I do.

_EDIT:_
First, find out the date of when you uninstalled everything accidentally (probably by doing sudo apt-get autoremove). Here the date assumed was March 27, 2009.

awk ' $3 == "remove" && $1 == **"2009-03-27"** {print $4 }' /var/log/dpkg.log

awk ' $3 == "remove" && $1 == **"2009-03-27"** {print $4 }' /var/log/dpkg.log  | xargs apt-get -f -y install

Change the bold part to the last date you recall things working properly. This works in Debian so it should work in Ubuntu.

---

### Post by Sealbhach on 2009-06-21
I think Aptitude will sometimes remove packages that conflict with the new packages you are installing, but it will always tell you beforehand and ask if you wish to proceed.

For example, if I were to install wicd, it would remove network manager:

```
user@sonyvaio:~$ sudo apt-get -s install wicd
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  network-manager network-manager-gnome
The following NEW packages will be installed:
  wicd
0 upgraded, 1 newly installed, 2 to remove and 5 not upgraded.
Remv network-manager-gnome [0.7.1~rc4.1-0ubuntu2]
Remv network-manager [0.7.1~rc4.1.cf199a964-0ubuntu2]
Inst wicd (1.5.9-2 Ubuntu:9.04/jaunty)
Conf wicd (1.5.9-2 Ubuntu:9.04/jaunty)

```

Maybe something like this happened?

.

---

### Post by nandemonai on 2009-06-21
I don't like the look of all those ata errors. That would indicate an issue with your hard disk, file system or CDROM or some such.

You may want to run a fsck on it to be sure. To schedule a fsck on next boot:

```
sudo touch /forcefsck
```

Then reboot.

---

### Post by Gp. on 2009-06-22
> **s3a said:**
> There is a terminal way to "restore" your system by installing what was recently removed. I don't recall the command by memory so I'll go find it and post back when I do.

_EDIT:_
First, find out the date of when you uninstalled everything accidentally (probably by doing sudo apt-get autoremove). Here the date assumed was March 27, 2009.

awk ' $3 == "remove" && $1 == **"2009-03-27"** {print $4 }' /var/log/dpkg.log

awk ' $3 == "remove" && $1 == **"2009-03-27"** {print $4 }' /var/log/dpkg.log  | xargs apt-get -f -y install

Change the bold part to the last date you recall things working properly. This works in Debian so it should work in Ubuntu.


Tried, but I got this...

```
~$ awk ' $3 == "remove" && $1 == "2009-06-21" {print $4 }' /var/log/dpkg.log | xargs apt-get -f -y install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

Tried with sudo and gksu too, still the same permission denied?

---

### Post by Gp. on 2009-06-22
> **nandemonai said:**
> I don't like the look of all those ata errors. That would indicate an issue with your hard disk, file system or CDROM or some such.

You may want to run a fsck on it to be sure. To schedule a fsck on next boot:

```
sudo touch /forcefsck
```

Then reboot.

Also, for learning, what does the touch command do or better yet why is it called touch?

---

### Post by ivanvajar on 2009-06-22
This might be HDD issue or something might be wrong with your RAM.

---

### Post by nandemonai on 2009-06-22
> **Gp. said:**
> Also, for learning, what does the touch command do or better yet why is it called touch?

Touch (in this case) creates a blank file. ;)

For a full explantaion of the command:

```
man touch
```

---

