---
title: "ubunut 10.04 lts / Partitions"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by daveedking on 2010-05-14
Hello **ubuntu** forums and members,
 i created a 8 gig. ntfs partition to install ubuntu 10.04 on.(install was no problem)
im not sure why but my file system reads as only having 4 gig's.... here are the pics..
[IMG]http://i713.photobucket.com/albums/ww140/daveedking/nopartsmall.png[/IMG]
[IMG]http://i713.photobucket.com/albums/ww140/daveedking/disk_utility.png[/IMG]

the second photo using **disk utility** shows the 8 gigs spread out."'is ubuntu hiding 4 gigs for just data"
i hope to be able to free up those 4 gig's since my **disk analyzer** shows the filesytem as only having 4 gigs and im running low. 400. mb. free space... **help with resizing please..**
**thanks a million**...
-daveed-

---

### Post by venicequeen7706 on 2010-05-14
I'm not the most experienced with partitions but I think if you click the mount volume button in your image you would be able to use it. you could probably use the edit partition to make it mount that automatically as part of the home directory

---

### Post by oldfred on 2010-05-14
I do not understand a linux NTFS partition unless it is wubi, but you are showing a tiny 1.7GB ext3 partition and 230MB swap.

Did you allocated an NTFS partition then choose side by side where it shrinks a partition and installs in the remaining space?

If that is the case and you have not done much updates it may be quicker to delete the NTFS, and linux partitions and totally reinstall to the free space - that still is not large. That will delete everything, so if you want to save any data make sure you have good backups.

I typically recommend a 10-20GB partition for / (root) and 2GB for swap as a minimum install. You can get by with about 6-7GB if you have very limited space.

---

### Post by jerome1232 on 2010-05-14
from that you have

/dev/sda1 - 242 GB NTFS
/dev/sda2 - 4.4 GB NTFS
/dev/sda5 - 3.7 GB EXT4
/dev/sda6 - 232 MB Swap


Are you refering to the /dev/sda2 "linux_volume" 4.4 GB partition as the lost space? 

If you intend on using that to expand your system I would recommend formating to ext4 or ext3 (is there any data on it already? Make sure there isn't first) and migrating your home partition over to it 

simply rsync /home to it and edit fstab to mount the new partition as /home next boot. 

If that's what you like to do then we can help you with the hole process as well.

---

### Post by daveedking on 2010-05-14
> **jerome1232 said:**
> from that you have

/dev/sda1 - 242 GB NTFS
/dev/sda2 - 4.4 GB NTFS
/dev/sda5 - 3.7 GB EXT4
/dev/sda6 - 232 MB Swap


Are you refering to the /dev/sda2 "linux_volume" 4.4 GB partition as the lost space? 

If you intend on using that to expand your system I would recommend formating to ext4 or ext3 (is there any data on it already? Make sure there isn't first) and migrating your home partition over to it 

simply rsync /home to it and edit fstab to mount the new partition as /home next boot. 

If that's what you like to do then we can help you with the hole process as well.

**yes** the linux volume is the lost space, i have no data there... 
 ok. if u can help me expand my current file system with the linux volume that would be great... 
**thanks to everyone for the quick reply** :)

---

### Post by jerome1232 on 2010-05-14
Okay the first step would be to use gparted to format it to ext4 or ext3 your choice.

Second we need to copy /home's file over to it, rsync or grsync are the best tools for this.

Lastly we will need to boot into single user mode or use a live cd to delete the original file's in /home, then update fstab to mount your new partition.


So install gparted

```
sudo apt-get install gparted
```

To access it click System - Administration - Gparted
Type in your password
You should be able to right click on /dev/sda2 and select format to -> ext4.

Alright once that finishes we need to mount that partition and copy files over.

```
sudo mkdir /mnt/temp
sudo mount /dev/sda2 /mnt/temp
sudo rsync -av /home/ /mnt/temp/
```

Grab a cup of coffee and let that complete. When it's done we have to do the hard part.

---

### Post by daveedking on 2010-05-14
> **jerome1232 said:**
> Okay the first step would be to use gparted to format it to ext4 or ext3 your choice.

Second we need to copy /home's file over to it, rsync or grsync are the best tools for this.

Lastly we will need to boot into single user mode or use a live cd to delete the original file's in /home, then update fstab to mount your new partition.


So install gparted

```
sudo apt-get install gparted
```To access it click System - Administration - Gparted
Type in your password
You should be able to right click on /dev/sda2 and select format to -> ext4.

Alright once that finishes we need to mount that partition and copy files over.

```
sudo mkdir /mnt/temp
sudo mount /dev/sda2 /mnt/temp
sudo rsync -av /home/ /mnt/temp/
```Grab a cup of coffee and let that complete. When it's done we have to do the hard part.
**-ok hard part done-** next..??
i did get this **error:**
[IMG]http://i713.photobucket.com/albums/ww140/daveedking/terminal_resynce.png[/IMG]

---

### Post by jerome1232 on 2010-05-14
First backup your current fstab
```
sudo cp /etc/fstab /etc/fstab.bck
```

Do you have a live cd around? If not grab one from
[here]("http://www.ubuntu.com/GetUbuntu/download")

Post the results of the following commands. This just shows me your current fstab and the uuid of your new partition.

```
cat /etc/fstab
sudo tune2fs -l /dev/sda2 | grep UUID
```


As far as that error goes can your rerun that rsync command with one change?

```
sudo rsync -av --exclude .gvfs /home/ /mnt/temp
```

If that last rsync command fails with any errors then I need to see the errors. Which folders failed.

If it works with zero errors then you will need to boot into a live cd session to finish the last part. (deleting old /home and editing fstab)

---

### Post by -humanaut- on 2010-05-14
Backing up your files and reinstalling off the LiveCD maybe a lot easier to deal with and with all probability have a higher success rate. Just my two-cents.

---

### Post by daveedking on 2010-05-14
> **jerome1232 said:**
> First backup your current fstab
```
sudo cp /etc/fstab /etc/fstab.bck
```Do you have a live cd around? If not grab one from
[here]("http://www.ubuntu.com/GetUbuntu/download")

Post the results of the following commands. This just shows me your current fstab and the uuid of your new partition.

```
cat /etc/fstab
sudo tune2fs -l /dev/sda2 | grep UUID
```
As far as that error goes can your rerun that rsync command with one change?

```
sudo rsync -av --exclude .gvfs /home/ /mnt/temp
```If that last rsync command fails with any errors then I need to see the errors. Which folders failed.

If it works with zero errors then you will need to boot into a live cd session to finish the last part. (deleting old /home and editing fstab)

the rsync command 
```
sudo rsync -av --exclude .gvfs /home/ /mnt/temp
``` **returned no errors** :)
[B]
jerome[/B] im a little unclear what i need to do with the live CD. do i boot into it and run the ```
cat /etc/fstab
sudo tune2fs -l /dev/sda2 | grep UUID
``` command ??
i have backed up **fstab** no problem... just need help understanding what u want me 2 do when booting the live CD...
 **thanks a million J**
-daveed-

---

### Post by jerome1232 on 2010-05-14
Post the results of those two commands prior to booting the cd. Once I see your fstab I can tell you how to edit it from the live cd.

---

### Post by daveedking on 2010-05-14
**current fstab and the uuid**:
tikki@tikki-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=e6625e1d-33e9-4cb6-bce5-ce72fec44d62 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c2b96273-d830-4e8d-a334-021c2ada0e62 none            swap    sw              0       0
tikki@tikki-laptop:~$ sudo tune2fs -l /dev/sda2 | grep UUID
[sudo] password for tikki: 
Filesystem UUID:          d55da0ff-57ca-4e5d-a23e-96abd9f7043b
tikki@tikki-laptop:~$ 
____________________________________________________________________________

**the rsync command:**
tikki@tikki-laptop:~$ sudo rsync -av --exclude .gvfs /home/ /mnt/temp
sending incremental file list
tikki/.bash_history
tikki/.xsession-errors
tikki/.config/softwarecenter/
tikki/.config/softwarecenter/softwarecenter.cfg
tikki/.gconf/apps/
tikki/.gconf/apps/baobab/ui/
tikki/.gconf/apps/baobab/ui/%gconf.xml
tikki/.gconf/apps/gnome-terminal/profiles/Default/
tikki/.gconf/apps/gnome-terminal/profiles/Default/%gconf.xml
tikki/.gconf/apps/gnome_settings_daemon/
tikki/.gconf/apps/gnome_settings_daemon/%gconf.xml
tikki/.gconf/apps/gnome_settings_daemon/plugins/
tikki/.gconf/apps/gnome_settings_daemon/plugins/%gconf.xml
tikki/.gconf/apps/gnome_settings_daemon/plugins/housekeeping/
tikki/.gconf/apps/gnome_settings_daemon/plugins/housekeeping/%gconf.xml
tikki/.gconf/apps/nautilus/desktop-metadata/242@32@GB@32@Filesystem@46@volume/
tikki/.gconf/apps/nautilus/desktop-metadata/242@32@GB@32@Filesystem@46@volume/%gconf.xml
tikki/.gconf/apps/nm-applet/
tikki/.gconf/system/networking/connections/1/802-11-wireless/
tikki/.gconf/system/networking/connections/1/802-11-wireless/%gconf.xml
tikki/.gconf/system/networking/connections/1/connection/
tikki/.gconf/system/networking/connections/1/connection/%gconf.xml
tikki/.gconf/system/networking/connections/1/ipv4/
tikki/.gconf/system/networking/connections/1/ipv4/%gconf.xml
tikki/.gconf/system/networking/connections/1/ipv6/
tikki/.gconf/system/networking/connections/1/ipv6/%gconf.xml
tikki/.gconfd/
tikki/.gconfd/saved_state
tikki/.gnome2/accels/nautilus
tikki/.local/share/Trash/expunged/
tikki/.local/share/Trash/files/
tikki/.local/share/Trash/files/filezilla.desktop
tikki/.local/share/Trash/info/
tikki/.local/share/Trash/info/filezilla.desktop.trashinfo
tikki/.local/share/gvfs-metadata/
tikki/.local/share/gvfs-metadata/home
tikki/.local/share/gvfs-metadata/home-eaed4077.log
tikki/.local/share/webkit/icondatabase/
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/cnettv.cnet.com/
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/cnettv.cnet.com/OVPMetricsProvider.sol
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/cnettv.cnet.com/com.conviva.livePass.sol
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/cnettv.cnet.com/[[IMPORT]]/vidtech.cbsinteractive.com/player/1_3_2/CBSI_PLAYER.swf/
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/cnettv.cnet.com/[[IMPORT]]/vidtech.cbsinteractive.com/player/2_3_0/CBSI_PLAYER.swf/
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/cnettv.cnet.com/av/video/cnettv/4/20100511/player.swf/
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/cnettv.cnet.com/av/video/gecko/gecko.swf/
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/player.hulu.com/
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/player.hulu.com/BeaconService.sol
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/player.hulu.com/NewSitePlayer.sol
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/player.hulu.com/NewSitePlayer_VOLUME.sol
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/player.hulu.com/OVPMetricsProvider.sol
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/player.hulu.com/_ggCvar.sol
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/player.hulu.com/_ggCvar_temp.sol
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/player.hulu.com/_ggMCvar_1.sol
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/player.hulu.com/com.quantserve.sol
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/www.hulu.com/
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/www.hulu.com/BeaconService.sol
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/www.hulu.com/MastheadSponsor.sol
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/www.hulu.com/loadplayer.swf/
tikki/.macromedia/Flash_Player/#SharedObjects/LK88A92W/www.hulu.com/loadplayer.swf/mkstb.sol
tikki/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/
tikki/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/settings.sol
tikki/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#player.hulu.com/
tikki/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#player.hulu.com/settings.sol
tikki/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.hulu.com/](www.hulu.com/)
tikki/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.hulu.com/settings.sol](www.hulu.com/settings.sol)
tikki/.mozilla/firefox/vkuuxfit.default/
tikki/.mozilla/firefox/vkuuxfit.default/cookies.sqlite
tikki/.mozilla/firefox/vkuuxfit.default/cookies.sqlite-journal
tikki/.mozilla/firefox/vkuuxfit.default/formhistory.sqlite
tikki/.mozilla/firefox/vkuuxfit.default/places.sqlite
tikki/.mozilla/firefox/vkuuxfit.default/places.sqlite-journal
tikki/.mozilla/firefox/vkuuxfit.default/sessionstore.js
tikki/.mozilla/firefox/vkuuxfit.default/urlclassifier3.sqlite
tikki/.mozilla/firefox/vkuuxfit.default/Cache/
tikki/.mozilla/firefox/vkuuxfit.default/Cache/0198931Ed01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/04BD6DA7d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/04FDD29Ed01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/08CBB107d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/0A4182E4d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/100670EDd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/140A2FE4d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/14C68EACd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/2271C75Cd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/25C17BB7d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/2A264713d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/2CA7D757d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/354CCC4Cd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/41099CCDd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/4255B354d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/42BDEDE0d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/4CB307E3d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/4FD43A33d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/5405EAB7d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/6308A140d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/6A5FAA47d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/6B1DE70Dd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/6DA756BFd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/70EEA2CFd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/80C207D1d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/84A37E7Cd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/87A0805Ed01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/916B3273d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/9270CE83d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/929BB877d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/944E78F5d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/9C8C1BAEd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/9FF534ECd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/A21043CDd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/A43DE85Ed01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/A6AF9DCDd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/B501C6EFd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/B6D1C52Bd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/B8C63C03d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/BA377ECBd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/BA82492Fd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/BF14C28Fd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/BFF84ADEd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/C7D042B9d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/CC1E2342d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/CE907B7Ed01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/D1B5F080d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/E2EE8147d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/E45A61CBd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/F352E10Ed01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/F439DBDDd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/F804C026d01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/FC9B4DCFd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/FD19753Bd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/FE481DACd01
tikki/.mozilla/firefox/vkuuxfit.default/Cache/_CACHE_001_
tikki/.mozilla/firefox/vkuuxfit.default/Cache/_CACHE_002_
tikki/.mozilla/firefox/vkuuxfit.default/Cache/_CACHE_003_
tikki/.pulse/cf5f76f29e7dfe0a85a621884bdcc182-device-volumes.tdb
tikki/Desktop/

sent 54740666 bytes  received 2412 bytes  36495385.33 bytes/sec
total size is 240576154  speedup is 4.39
tikki@tikki-laptop:~$

---

### Post by jerome1232 on 2010-05-14
Okay so boot the live cd Pop open a terminal and...

Mount the root partition of your ubuntu installation to /mnt
```
sudo mount /dev/sda5 /mnt
```

Now we are deleting everything inside of it's /home partition (We copied the files to your new partition so it's fine, we can't have files sitting inside of the future mount point)
```
sudo rm -rf /mnt/home/*
```

Now we are going to edit your fstab, add in the part I highlighted in red, if you formated it to ext3, then substitute ext3 for ext4.
```
gksu gedit /mnt/etc/fstab
```

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda5 during installation
UUID=e6625e1d-33e9-4cb6-bce5-ce72fec44d62 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
UUID=c2b96273-d830-4e8d-a334-021c2ada0e62 none swap sw 0 0
[COLOR="Red"]# /home /dev/sda2
UUID=d55da0ff-57ca-4e5d-a23e-96abd9f7043b /home ext4 defaults 0 2[/COLOR]
```

Save that file. Reboot into Ubuntu and cross your fingers.

---

### Post by daveedking on 2010-05-14
> **jerome1232 said:**
> Okay so boot the live cd Pop open a terminal and...

Mount the root partition of your ubuntu installation to /mnt
```
sudo mount /dev/sda5 /mnt
```Now we are deleting everything inside of it's /home partition (We copied the files to your new partition so it's fine, we can't have files sitting inside of the future mount point)
```
sudo rm -rf /mnt/home/*
```Now we are going to edit your fstab, add in the part I highlighted in red, if you formated it to ext3, then substitute ext3 for ext4.
```
gksu gedit /mnt/etc/fstab
``````

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda5 during installation
UUID=e6625e1d-33e9-4cb6-bce5-ce72fec44d62 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
UUID=c2b96273-d830-4e8d-a334-021c2ada0e62 none swap sw 0 0
[COLOR=Red]# /home /dev/sda2
UUID=d55da0ff-57ca-4e5d-a23e-96abd9f7043b /home ext4 defaults 0 2[/COLOR]
```Save that file. Reboot into Ubuntu and cross your fingers.

i booted the live cd ran those commands and booted back... 
 nothing changed>? what happened >?
[IMG]http://i713.photobucket.com/albums/ww140/daveedking/new_part.png[/IMG]
 **New partition scheme...**

---

### Post by jerome1232 on 2010-05-15
Now that 4.4 gb partition is mounted as part of your file system, at /home, where all of your personal files go.

---

### Post by daveedking on 2010-05-15
> **jerome1232 said:**
> Now that 4.4 gb partition is mounted as part of your file system, at /home, where all of your personal files go.

 hey **jerome** **thanks** for the time and help but there is a **problem:**
[IMG]http://i713.photobucket.com/albums/ww140/daveedking/notmem.png[/IMG]
i recieved this error today using update manager...
**file system still not resized**...
*-daveed-*

---

### Post by necromonger on 2010-05-15
here is the way i do it.1 gig swap 15 gig / root rest of drive as home.

---

### Post by jerome1232 on 2010-05-15
So your out of room on your root partition, it is really small. It would be really complicated to fix that without reinstalling.

I would just backup files and reinstall, do manual partitioning, delete all partitions except swap and /dev/sda1, creat a new partition that takes all empty space and use that as your root.

---

### Post by -kg- on 2010-05-15
[LIST]
[/LIST]

Just for information purposes, what I think has happened is this:

Linux (or any Linux distribution that *I've* ever heard of) will not install into a partition that is formatted as ntfs or fat.  It must install into a partition that is formatted in a compatible format, such as its native ext(2,3,4), ReiserFS, or so forth.

So when you created the 8 GB ntfs partition, the installer saw that you had no compatible partition in which to install itself, so it shrank the 8 GB partition, created an Extended partition, and created the partitions necessary for it to install itself (a swap partition is also required).

If this is a new installation (which I'm assuming it is), then it would probably be better to just delete all the partitions except for sda1...your Windows partition...(after saving what little data you need from those partitions, if any) and either recreate the partitions in the correct format, or turn the installer loose on the free space and let *it* create them for you.

If it is at all possible, a little more room than 8 GB would likely make for a better installation, and your experience a little happier.  It would give you a bit more "wiggle room."  Read at the link in my signature block for more information on partitioning operations.

---

### Post by -kg- on 2010-05-15
[LIST]
[/LIST]

As an addendum...something I just thought of:

If you *do* manually create the partitions in which to install Ubuntu (or Linux, in general), you *_must_* use the "Manual Partitioning" selection.  You have to mark the mount point of those partitions as "/" (root), "/home", or whatever in order for the installer to use them.

Otherwise, the installer will ignore them, shrink them, and create its own, the same as happened with your installation.  Had you done this during installation, though, the installer would have told you that you couldn't use the ntfs partition as root.

---

### Post by daveedking on 2010-05-15
well -**KG**- here is what im going to do...
 boot into win 7, **delet**e 8 gig linux partition with EASEUS **partition manager**, reboot fix grub error /**fixboot rec**, boot back into win 7, create 10 gig **etx4**partiton, boot into live cd and install ubuntu 10.04 lts on that 10 gig **etx4** partition....
 any problems here >? will i get the full 10 gigs for my root (file system) >?
**thanks**...
*-daveed-*

---

### Post by jerome1232 on 2010-05-16
That seems overly complicated to me, you could just boot the live cd and use the manual partitioner during installation.

Of course if your more comfortable using the partition manager you are used to by all means you can do it that way. Everything you said sounds fine, although I don't understand why you need to fix grub after deleting the partition, the live cd installer should take care of reinstalling grub for you, and you don't need to have grub functioning at all to boot the live cd.

---

### Post by -kg- on 2010-05-19
[LIST]

[/LIST]Sorry I'm a little late getting back to this, but:

Probably the easiest way to do what you want to do is to boot into Win 7 (though you ***could*** boot to the Live CD and do this with GPartEd), delete the all the Ubuntu partitions you made with Easus, then reboot into the Live CD, install, and, when you get to the Partitioning step, choose "Install in Largest Contiguous Free Space" (or whatever it is now...I've not installed Lucid yet).

That way, the installer will create all the requisite partitions for you automatically without the need to manually create them and mark their mount points (unless you want to create them and mark their mount points for the learning experience).  That would be the easiest way to do it, and it would install right with no "special considerations."

You realize that you'll need to *at least* create a swap partition in addition to your root partition, right?  That will cut into the free space you have for your root.  The conventional recommended amount is 1 1/2 X the amount of RAM installed in your machine.  In my case, since I have 2 GB of RAM, my swap would be 3 GB.  If you leave 10 GB of free space and have the same RAM, you would have 7 GB left for your root partition.

However, a lot of the time you can use less than this, especially if you have a fair amount of RAM and don't use hibernate, where the contents of memory are stored in the swap area, or very memory intensive software, where portions of memory are swapped out.

Sometimes it's a matter of experimenting to see how little you can get away with.  In the couple of years I've been using Ubuntu, I have used the swap partition so little that I almost don't need one; however, I have plenty of hard drive space, so I keep it around.

---

### Post by daveedking on 2010-05-20
**hey ubuntu members thanks for the help...**
 i took 10.04 off my laptop **"runs 2 hot"  **
  On my desktop ubuntu is still the best linux distro.. **"linux for humans"**
i was never able to resize the **partition** even after i changed the **ntf**s to **ex4**...
 thanks a million 2 the ubuntu forums...
 P.S. Ubuntu runs hot on laptops <>~~~ 
*-daveed-*
[B][URL="http://www.google.com.pr/url?sa=t&source=web&ct=res&cd=1&ved=0CBMQFjAA&url=http%3A%2F%2Fforum.mintywhite.com%2Fviewtopic.php%3Ff%3D24%26t%3D2059%26start%3D0%26st%3D0%26sk%3Dt%26sd%3Da&ei=i-b0S5-4KIPtlQer-9D3Cw&usg=AFQjCNEqtfyddXaMfOohie507c62ufDXOg&sig2=6P1O4AyhHHdqoeUCYB8fxA"]
[/URL][/B]

---

### Post by -kg- on 2010-05-20
> **daveedking said:**
> 
i was never able to resize the **partition** even after i changed the **ntf**s to **ex4**...

As I said, you needed to delete *_all_* the partitions, except for the one for Windows, before you started.  You couldn't resize the partition you created because you had no free space to expand it into.

If you look at the image of your partitions that you posted, you will see that, at the end of your drive, you have an extended partition, which contains your sda5 and sda6 as logical partitions.  There is no space into which to expand your sda2 partition, no matter how it's formatted.

You needed to *at least* delete those two partitions *and* the extended partition in order to expand sda2.  The reason you would need to delete the extended partition is that you cannot expand a primary partition into the space contained by an extended partition.  You would either need to create an extended partition, then create the ext4 partition inside it as a logical partition, or create both your root and swap partitions as primary partitions.

That's why I said it would be best to just delete *all* the partitions and let the installer do it.  That, or if you want to learn partitioning operations, to read on the "How To Partition" link in my signature block, which will show you basic partitioning operations and what you can and can't do.


 > **daveedking said:**
> P.S. Ubuntu runs hot on laptops <>~~~ 
*-daveed-*


It doesn't run hot on *my* laptop.  As matter of fact, it runs cooler than Windows ever did.  But there are differences between laptops...perhaps in the "cooling" department, as well.

---

### Post by daveedking on 2010-05-20
> 
**you cannot expand a primary partition into the space contained by an  extended partition.**


 **dont mean 2 keep this going but why>? what cant i expand a primary partition into the space contained by an  extended partition.**

---

### Post by srs5694 on 2010-05-20
> **daveedking said:**
> > **you cannot expand a primary partition into the space contained by an   extended partition.****dont mean 2 keep this going but why>? what cant i expand a primary partition into the space contained by an  extended partition.**

Why are you boldfacing everything? There's no need to; it's just a bit annoying (IMHO, of course).

To answer your question, though, an extended partition is a special type of primary partition, and primary partitions may not overlap with one another. Suppose for the sake of argument that you deliberately misconfigured a partition table so that a primary partition (let's say it's /dev/sda2) extends a few sectors into the following extended partition (/dev/sda3). An extended partition serves as a placeholder for logical partitions, and in fact the first sector of an extended partition is a definition of the first logical partition on the disk (/dev/sda5), as well as a pointer to the sector that defines the next logical partition (/dev/sda6). On this misconfigured disk, though, this first sector belongs to both the /dev/sda2 primary partition and the /dev/sda3 extended partition. This might seem to work for a while, but if /dev/sda2 starts to fill up, chances are that sector would end up being overwritten. It now contains garbage, from an extended partition point of view, meaning that the computer will no longer know where /dev/sda5 is or how large it is. Furthermore, the link to /dev/sda6 will be lost, and with it the links to all subsequent logical partitions. Thus, having a primary partition overlap with the start of an extended partition runs the risk of losing *all* of your logical partitions. Depending on how much they overlap, the /dev/sda2 primary partition might also overlap one or more logical partition(s), too, which will wreak even more havoc.

In practice, this limitation isn't so awful. If you've got a bit of free space outside of the extended partition and a bit of free space inside the extended partition, it's easy enough to resize the extended partition (using GParted or similar tools) so that all of the free space resides either inside or outside the extended partition. You can then create one or more logical or primary partitions, respectively, that fill all of this free space.

---

### Post by jerome1232 on 2010-05-20
Afaik all partition information (the partition table) is stored in the boot sector of the drive, the boot sector is the first 512 bytes of a drive. As you can imagine only a limited amount of information can be stored in 512 bytes, in fact you can only have 4 primary partitions on a disk.

To get around that they come up with extended partitions, which store more information outside of the boot sector. You can only have one extended partition on a drive (the extended partition takes up the room a primary would have in the boot sector, meaning you can have 3 primary partitions and 1 extended partition) but they in turn can store information about multiple logical partitions ( a logical partition is just a partition inside of the extended partition) contained within them.

I hope that adds to the description above a bit.

---

### Post by daveedking on 2010-05-20
thanks for the run down coffee_geeks...
 we can mark this thread **solved**..

P.S. please forgive me boldness..(text)
*-love ubuntu 4 desktops-*

---

