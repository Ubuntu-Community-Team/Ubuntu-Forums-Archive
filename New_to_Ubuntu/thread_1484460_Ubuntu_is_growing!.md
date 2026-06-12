---
title: "Ubuntu is growing!"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by Chipshot on 2010-05-15
My Ubuntu partition is up to 50 gigs now. It had to be increased from a smaller size-if memory serves, around 20 gigs. Does 50 gigs seem too large? Several programs have been added.  Maybe that's it. All my data goes to the “home” partition and moving large amounts of data in and out (several gigs) changed it's size but not the Ubuntu partition. There is a Windows partition that is not used very often. The system is running very well. If this is the wrong area for such a question can you redirect me. Thanks, John

---

### Post by trentscott on 2010-05-15
50GB is sufficient for average use, I wouldn't worry about it. It all depends on what you can spare given your resources and/or other needs (e.g. Windows).

---

### Post by -humanaut- on 2010-05-15
My partitions are 21 GB for / 5 GB Swap and 181 GB /home but I don't have windows or any other O.S.'s. I do have a 5 GB Fat32 Partition that I use to backup important files. That stays unmounted and removed from fstab unless I have to use it.

---

### Post by Chipshot on 2010-05-15
Thanks for your input folks.  It looks like it ain't broke so it probably should not  be fixed.

---

### Post by ezsit on 2010-05-15
> My Ubuntu partition is up to 50 gigs now. It had to be increased from a smaller size-if memory serves, around 20 gigs. Does 50 gigs seem too large? Several programs have been added.

Do you mean to say that your USED space grew from 20GiB to 50 GiB? I have a hard time believing 20 GiB wasn't enough for your / partition. I install several programs, sometimes KDE and Gnome and loads of stuff and I've never had a / partition require more than 15 GiB.

---

### Post by jerome1232 on 2010-05-15
> **ezsit said:**
> Do you mean to say that your USED space grew from 20GiB to 50 GiB? I have a hard time believing 20 GiB wasn't enough for your / partition. I install several programs, sometimes KDE and Gnome and loads of stuff and I've never had a / partition require more than 15 GiB.

+1, My desktop uses 4.8GB of space on it's root partition, my headless server a mere 1.8GB's, but I guess that one doesn't count.

The desktop is a fairly new install but I pretty much have every program I'll use plus a few games installed already.

I'd use du to investigate a little bit, have you put some stuff in your root users trash? your logs huge?

```
sudo du -hx --max-depth=1 /
```

---

### Post by adam22 on 2010-05-15
I have 13.6 GB free of my 18 GB root partition, and 168 GB free of my 184 GB /home partition...I also have a 2 GB SWAP partition and one Windows partition.

---

### Post by BoneKracker on 2010-05-15
> **-humanaut- said:**
> My partitions are 21 GB for / 5 GB Swap and 181 GB /home but I don't have windows or any other O.S.'s. I do have a 5 GB Fat32 Partition that I use to backup important files. That stays unmounted and removed from fstab unless I have to use it.

Sounds reasonable.  5 GiB for swap is probably more than twice what you need in reality, but it's not worth messing with unless you're really pinched for disk space.

The following command will show how utilized your filesystems are:
```
df -hT
```
What does it say?

I like to set up my partitions so that they're about 40% full when I've got everything on them I expect to have there.  Plenty of wiggle room.  I think minor filesystem performance degradation begins (on average) around 80% - 85% or so, so I'll make changes if it reaches that point.  (I'm no expert, though.)

---

### Post by Chipshot on 2010-05-15
When messages about not having enough space started popping up I found the partition full and used Gparted to increase it.

---

### Post by -humanaut- on 2010-05-15
I just use 5 GB swap partition just in case. I have plenty of space on my HDD plus 2GB of RAM. I ran out of Swap once a couple years ago man thats fun...

---

### Post by Chipshot on 2010-05-15
> **BoneKracker said:**
> Sounds reasonable.  5 GiB for swap is probably more than twice what you need in reality, but it's not worth messing with unless you're really pinched for disk space.

The following command will show how utilized your filesystems are:
```
df -hT
```What does it say?

I like to set up my partitions so that they're about 40% full when I've got everything on them I expect to have there.  Plenty of wiggle room.  I think minor filesystem performance degradation begins (on average) around 80% - 85% or so, so I'll make changes if it reaches that point.  (I'm no expert, though.)

It says:  

john@Ubuntu:~$ df -hT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sdb6     ext3     88G   49G   35G  59% /
tmpfs        tmpfs    754M     0  754M   0% /lib/init/rw
varrun       tmpfs    754M  100K  754M   1% /var/run
varlock      tmpfs    754M     0  754M   0% /var/lock
udev         tmpfs    754M  152K  754M   1% /dev
tmpfs        tmpfs    754M  144K  754M   1% /dev/shm
lrm          tmpfs    754M  2.2M  752M   1% /lib/modules/2.6.28-18-generic/volatile
/dev/sdb7     ext3    103G  9.4G   89G  10% /home
john@Ubuntu:~$ 

How's it look to you?

---

### Post by Chipshot on 2010-05-15
> **jerome1232 said:**
> +1, My desktop uses 4.8GB of space on it's root partition, my headless server a mere 1.8GB's, but I guess that one doesn't count.

The desktop is a fairly new install but I pretty much have every program I'll use plus a few games installed already.

I'd use du to investigate a little bit, have you put some stuff in your root users trash? your logs huge?

```
sudo du -hx --max-depth=1 /
```

Where can I find the root user trash and these logs? Is this something I can run down with Nautilus?

---

### Post by BoneKracker on 2010-05-15
> **Chipshot said:**
> It says:  

john@Ubuntu:~$ df -hT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sdb6     ext3     88G   49G   35G  59% /
tmpfs        tmpfs    754M     0  754M   0% /lib/init/rw
varrun       tmpfs    754M  100K  754M   1% /var/run
varlock      tmpfs    754M     0  754M   0% /var/lock
udev         tmpfs    754M  152K  754M   1% /dev
tmpfs        tmpfs    754M  144K  754M   1% /dev/shm
lrm          tmpfs    754M  2.2M  752M   1% /lib/modules/2.6.28-18-generic/volatile
/dev/sdb7     ext3    103G  9.4G   89G  10% /home
john@Ubuntu:~$ 

How's it look to you?

That looks fine, other than your root filesystem seems awfully large for a binary distribution.  Break it down using du as was suggested.

---

### Post by Chipshot on 2010-05-15
> **BoneKracker said:**
> That looks fine, other than your root filesystem seems awfully large for a binary distribution.  Break it down using du as was suggested.

Do you mean to run:

sudo du -hx --max-depth=1 /

If so, what will that do?

I may have to leave for  awhile but I'll be back. Thanks for your input.

---

### Post by BoneKracker on 2010-05-15
It's like df, but it checks directories instead of entire filesystems.

With those options he gave, it will tell you how much space is being used by each thing sitting at the top level of your root directory.

You'll want to look at it and judge whether any of those look out of line (abnormally large).  You may not be able to judge that, but if you post it here, peopel will help.

Then you can use the same command to drill down into any area that looks too big (for example, by changing "/" to "/var" or to "/var/log").  If you want to include 2 levels of subdirectories, change that from 1 to 2.

You can probably use Nautilus to look at these file and directory sizes, but I personally would expect it to be slow and not necessarily honest.

One of the nice things about using the command line is you can have this run as a script every so often so you can monitor how it's changing over time.

---

### Post by Chipshot on 2010-05-15
> **BoneKracker said:**
> It's like df, but it checks directories instead of entire filesystems.

With those options he gave, it will tell you how much space is being used by each thing sitting at the top level of your root directory.

You'll want to look at it and judge whether any of those look out of line (abnormally large).  You may not be able to judge that, but if you post it here, peopel will help.

Then you can use the same command to drill down into any area that looks too big (for example, by changing "/" to "/var" or to "/var/log").  If you want to include 2 levels of subdirectories, change that from 1 to 2.

You can probably use Nautilus to look at these file and directory sizes, but I personally would expect it to be slow and not necessarily honest.

One of the nice things about using the command line is you can have this run as a script every so often so you can monitor how it's changing over time.

Thank you. I'll give it a go tomorrow. I was surprised to discover that I'm not unlike Nautilus!

---

### Post by Chipshot on 2010-05-16
> **BoneKracker said:**
> It's like df, but it checks directories instead of entire filesystems.

With those options he gave, it will tell you how much space is being used by each thing sitting at the top level of your root directory.

You'll want to look at it and judge whether any of those look out of line (abnormally large).  You may not be able to judge that, but if you post it here, peopel will help.

Then you can use the same command to drill down into any area that looks too big (for example, by changing "/" to "/var" or to "/var/log").  If you want to include 2 levels of subdirectories, change that from 1 to 2.

You can probably use Nautilus to look at these file and directory sizes, but I personally would expect it to be slow and not necessarily honest.

One of the nice things about using the command line is you can have this run as a script every so often so you can monitor how it's changing over time.
Here's what was found:
john@Ubuntu:~$ sudo du -hx --max-depth=1 /
[sudo] password for john: 
2.1G    /usr
589M    /var
0    /sys
14M    /etc
26M    /boot
0    /dev
4.0K    /mnt
8.4M    /sbin
30G    /root
76K    /tmp
0    /proc
16K    /lost+found
4.0K    /selinux
220M    /lib
17G    /media
6.1M    /bin
4.0K    /home
4.0K    /srv
4.0K    /opt
49G    /
john@Ubuntu:~$ sudo du -hx --max-depth=2 /root
30G    /root/.local/share
30G    /root/.local
4.0K    /root/.gnome2_private
4.0K    /root/.nautilus/metafiles
8.0K    /root/.nautilus
8.0K    /root/.config/gtk-2.0
12K    /root/.config
8.0K    /root/.cache/gedit
12K    /root/.cache
4.0K    /root/Desktop
8.0K    /root/.dbus/session-bus
12K    /root/.dbus
64K    /root/.gconf/apps
68K    /root/.gconf
4.0K    /root/.gconfd
8.0K    /root/.gnome2/gedit
28K    /root/.gnome2/accels
4.0K    /root/.gnome2/nautilus-scripts
44K    /root/.gnome2
12K    /root/.thumbnails/fail
16K    /root/.thumbnails
4.0K    /root/.pulse
4.0K    /root/.wapi
76K    /root/.synaptic/log
88K    /root/.synaptic
30G    /root
john@Ubuntu:~$ sudo du -hx --max-depth=2/
8.0K    ./.hplip
4.0K    ./.icons
20K    ./.gnupg
4.0K    ./Photos
4.0K    ./.themes
4.0K    ./.checkbox
4.2M    ./.openoffice.org/3
4.2M    ./.openoffice.org
624K    ./tmp4OZ8Lh/base-installer
20K    ./tmp4OZ8Lh/imported
20K    ./tmp4OZ8Lh/NvidiaDetector
64K    ./tmp4OZ8Lh/computerjanitor
3.9M    ./tmp4OZ8Lh/mo
16K    ./tmp4OZ8Lh/patches
32K    ./tmp4OZ8Lh/plugins
96K    ./tmp4OZ8Lh/modaliases
6.5M    ./tmp4OZ8Lh
88K    ./.fontconfig
12K    ./.update-manager-core
40K    ./.sane/xsane
44K    ./.sane
4.0K    ./.gimp-2.6/gfig
4.0K    ./.gimp-2.6/gradients
4.0K    ./.gimp-2.6/tool-options
4.0K    ./.gimp-2.6/themes
4.0K    ./.gimp-2.6/templates
4.0K    ./.gimp-2.6/scripts
4.0K    ./.gimp-2.6/levels
4.0K    ./.gimp-2.6/patterns
4.0K    ./.gimp-2.6/environ
4.0K    ./.gimp-2.6/interpreters
4.0K    ./.gimp-2.6/tmp
4.0K    ./.gimp-2.6/brushes
4.0K    ./.gimp-2.6/curves
4.0K    ./.gimp-2.6/modules
4.0K    ./.gimp-2.6/plug-ins
4.0K    ./.gimp-2.6/gimpressionist
4.0K    ./.gimp-2.6/palettes
4.0K    ./.gimp-2.6/fractalexplorer
4.0K    ./.gimp-2.6/fonts
4.0K    ./.gimp-2.6/gflare
468K    ./.gimp-2.6
244K    ./.gstreamer-0.10
36K    ./.gnome2/panel2.d
48K    ./.gnome2/evince
4.0K    ./.gnome2/eog
8.0K    ./.gnome2/keyrings
148K    ./.gnome2/f-spot
16K    ./.gnome2/gedit
4.0K    ./.gnome2/nautilus-scripts
72K    ./.gnome2/accels
4.0K    ./.gnome2/file-roller
356K    ./.gnome2
9.3M    ./.local/share
9.3M    ./.local
8.0K    ./.aqbanking/shared
16K    ./.aqbanking
8.0K    ./.screenlets
8.0K    ./.gegl-0.0/plug-ins
4.0K    ./.gegl-0.0/swap
16K    ./.gegl-0.0
1.2M    ./.compiz/session
1.2M    ./.compiz
4.0K    ./.wapi
172K    ./.kde/share
176K    ./.kde
20K    ./.config/Screenlets
1.8M    ./.config/transmission
24K    ./.config/autostart
8.0K    ./.config/totem
12K    ./.config/compiz
8.0K    ./.config/enchant
8.0K    ./.config/brasero
8.0K    ./.config/gnome-session
8.0K    ./.config/gtk-2.0
1.9M    ./.config
748K    ./.thumbnails/fail
196K    ./.thumbnails/large
152M    ./.thumbnails/normal
153M    ./.thumbnails
66M    ./Documents/Downloads
250M    ./Documents/Outlook Data
6.5M    ./Documents/MouseDriver
3.6M    ./Documents/CreatingWebSites
814M    ./Documents/DL_Programs
1.6M    ./Documents/Nokia2285Lonna
3.3M    ./Documents/Eds File
24K    ./Documents/PC_World
288K    ./Documents/KMoneyData
34M    ./Documents/Arcata
1.3G    ./Documents/Rotary
4.0K    ./Documents/1A_Upstairs
173M    ./Documents/Backup
288K    ./Documents/OLDKMoneyData
2.2G    ./Documents/WCC_BU_03_12
208K    ./Documents/MapFiles
4.0K    ./Documents/My eBooks
236K    ./Documents/Savings
17M    ./Documents/Signiture
44K    ./Documents/Comcast
2.4G    ./Documents/My Pictures
669M    ./Documents/AccessPrograms
8.5M    ./Documents/My Videos
18M    ./Documents/Pictures
420M    ./Documents/PG
696K    ./Documents/YE5130
784K    ./Documents/My Albums
151M    ./Documents/1QB_Outlook_Backup
12K    ./Documents/LifeCam Files
100K    ./Documents/PHP
216M    ./Documents/ToUnbuntu
6.2M    ./Documents/John's Work
8.5M    ./Documents/Camera Manual
4.0K    ./Documents/ScannedItems
17M    ./Documents/DataBase
31M    ./Documents/QData
18M    ./Documents/BackgroundImages
124K    ./Documents/Bernie
77M    ./Documents/Checking
1.8M    ./Documents/Chase_MC
35M    ./Documents/Desktop
224K    ./Documents/PhotoshopNotes
8.0K    ./Documents/Cannon
8.0K    ./Documents/Recipes
2.7M    ./Documents/SoftwareTips
2.5M    ./Documents/ATT
20K    ./Documents/HTML_Tips
7.3M    ./Documents/Ubuntu_How_To
8.8G    ./Documents
96K    ./.pulse
4.0K    ./Pictures/ToWeb
8.0K    ./Pictures
du: cannot access `./.gvfs': Permission denied
688K    ./.evolution/addressbook
40K    ./.evolution/tasks
40K    ./.evolution/memos
8.0K    ./.evolution/signatures
91M    ./.evolution/mail
184K    ./.evolution/cache
72K    ./.evolution/calendar
92M    ./.evolution
36K    ./.tomboy/Backup
8.0K    ./.tomboy/addins
100K    ./.tomboy/addin-db-001
168K    ./.tomboy
4.0K    ./Templates
45M    ./.mozilla/firefox
12M    ./.mozilla/firefox-3.5
8.0K    ./.mozilla/extensions
57M    ./.mozilla
4.0K    ./Videos
4.0K    ./Public
20K    ./.bogofilter
4.0K    ./.phatch/watermarks
4.0K    ./.phatch/actionlists
4.0K    ./.phatch/actions
4.0K    ./.phatch/masks
24K    ./.phatch
204K    ./.gconfd
4.0K    ./.ssh
12K    ./.cache/rhythmbox
12K    ./.cache/totem
12K    ./.cache/gedit
316K    ./.cache/compizconfig
392K    ./.cache
1.1M    ./.macromedia/Flash_Player
1.1M    ./.macromedia
4.0K    ./Desktop/delthnaksjpg
56K    ./Desktop
4.0K    ./.update-notifier
624K    ./tmpmuITk9/base-installer
20K    ./tmpmuITk9/imported
20K    ./tmpmuITk9/NvidiaDetector
64K    ./tmpmuITk9/computerjanitor
3.9M    ./tmpmuITk9/mo
16K    ./tmpmuITk9/patches
32K    ./tmpmuITk9/plugins
96K    ./tmpmuITk9/modaliases
6.5M    ./tmpmuITk9
8.0K    ./.qt
4.0K    ./Music/My Playlists
8.0K    ./Music
40K    ./.filezilla
20K    ./.gconf/system
124K    ./.gconf/desktop
1.2M    ./.gconf/apps
1.4M    ./.gconf
4.0K    ./.gnome2_private
16K    ./.dbus/session-bus
20K    ./.dbus
1004K    ./.adobe/Flash_Player
1008K    ./.adobe
248K    ./.nautilus/metafiles
252K    ./.nautilus
9.2G    .
john@Ubuntu:~$ 
Notice that the john@Ubuntu:~$ sudo du -hx --max-depth=2/ is showing:
30G    /root/.local/share
30G    /root/.local
Is this a duplication?
Also, the line "66M    ./Documents/Downloads" looks like the beginning of the Windows partition, no?

---

### Post by jerome1232 on 2010-05-16
30 GB's in /root which means your root trash is FULLLLLL, this happens when you use gksu nautilus (runing nautilus as root) to delete files.


The easiest way would be to either gksu nautilus, and HOLD SHIFT while deleting those files at /root/.local/share/Trash/ (this bypasses trash) or use the command line.

```
sudo rm -rf /root/.local/share/Trash/*
```


The -x option for du keeps it from totaling files on other file systems, so it should not be looking at anyfiles not on your root partition. In other words everything du is coming up with is on the root partition only.

---

### Post by Chipshot on 2010-05-16
> **jerome1232 said:**
> 30 GB's in /root which means your root trash is FULLLLLL, this happens when you use gksu nautilus (runing nautilus as root) to delete files.


The easiest way would be to either gksu nautilus, and HOLD SHIFT while deleting those files at /root/.local/share/Trash/ (this bypasses trash) or use the command line.

```
sudo rm -rf /root/.local/share/Trash/*
```
The -x option for du keeps it from totaling files on other file systems, so it should not be looking at anyfiles not on your root partition. In other words everything du is coming up with is on the root partition only.

Thank you. There was a 30gig Full Sbackup folder in the trash. This looks a  lot better to me. How does this look? And OK, back to the command line.

john@Ubuntu:~$ sudo du -hx --max-depth=2 /root
24K    /root/.local/share
28K    /root/.local
4.0K    /root/.gnome2_private
4.0K    /root/.nautilus/metafiles
8.0K    /root/.nautilus
8.0K    /root/.config/gtk-2.0
12K    /root/.config
8.0K    /root/.cache/gedit
12K    /root/.cache
4.0K    /root/Desktop
8.0K    /root/.dbus/session-bus
12K    /root/.dbus
64K    /root/.gconf/apps
68K    /root/.gconf
4.0K    /root/.gconfd
8.0K    /root/.gnome2/gedit
28K    /root/.gnome2/accels
4.0K    /root/.gnome2/nautilus-scripts
44K    /root/.gnome2
12K    /root/.thumbnails/fail
16K    /root/.thumbnails
4.0K    /root/.pulse
4.0K    /root/.wapi
76K    /root/.synaptic/log
88K    /root/.synaptic
328K    /root

---

### Post by jerome1232 on 2010-05-16
That looks better, you should have like 19 GB's used in your / partition now.

You can check that with the df command posted earlier in this thread.

You should be good to shrink it back down to a smaller size from a live cd now. If you wanted to that is.

---

### Post by cuberts on 2010-05-16
> **Chipshot said:**
> My Ubuntu partition is up to 50 gigs now. It had to be increased from a smaller size-if memory serves, around 20 gigs. Does 50 gigs seem too large? Several programs have been added.  Maybe that's it. All my data goes to the “home” partition and moving large amounts of data in and out (several gigs) changed it's size but not the Ubuntu partition. There is a Windows partition that is not used very often. The system is running very well. If this is the wrong area for such a question can you redirect me. Thanks, John
it is not too big.
Really dont worry about it.

---

### Post by Chipshot on 2010-05-16
> **jerome1232 said:**
> That looks better, you should have like 19 GB's used in your / partition now.

You can check that with the df command posted earlier in this thread.

You should be good to shrink it back down to a smaller size from a live cd now. If you wanted to that is.
You are exactly right. Gparted resized things for me and I'm jazzed because any day is a good day to learn something new.
One last question, please.  How do I mark this thread "done" or "solved" or whatever?

Thank you Jerome!

---

### Post by jerome1232 on 2010-05-16
Thread tools, kind of in the upper rightish area.

---

