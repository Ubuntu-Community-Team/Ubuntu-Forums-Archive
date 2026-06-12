---
title: "Mount network share at boot in Ubuntu 15.04"
date: 2015-12-24
forum: Networking &amp; Wireless
---

### Post by manu081 on 2015-12-24
I just installed Ubuntu 15.04 on my Asus Chromebox to set it up as a HTPC in the living room.

I've got 2 NTFS-formatted external hard drives connected to my WiFi router that I would like to mount at boot.

The network drives are accessed as:
//192.168.0.15/folder1
//192.168.0.15/folder2 etc.

There are 5 folders in total that are split between the 2 drives. I can't compress it all into one folder unfortunately, so there are 5 folders that need to be mounted. Ideally, if these folders can be mounted in /media/ it would make for easy access. I tried the steps from [Ubuntu Handbook]("http://ubuntuhandbook.org/index.php/2014/08/map-network-drive-onto-ubuntu-14-04/") but it did not work.

I consider myself a noob when it comes to Linux, so a little help to get this set up would be greatly appreciated :)

---

### Post by dave205 on 2015-12-24
ok, I'm going off memory but this should work. I wanted bluetooth to be OFF by default and was told to edit the /etc/rc.local file. Apparently the file by itself does nothing but is a place to put runtime changes you want. I would expect this might work the same. 

So.....try placing your mount command inside rc.local and see if that works. Also, iirc, network shares are not mounted in /media but instead are in /run/user/<userid>/gvfs

good luck and please report back if it works so it can help everyone!


edit! - apparently UPSTART is replacing rc.local.  I'm going to try this later and see if it works. I just can't get to it now. 

[http://ubuntuforums.org/showthread.php?t=1786173&p=10957361&viewfull=1#post10957361](http://ubuntuforums.org/showthread.php?t=1786173&p=10957361&viewfull=1#post10957361)

---

### Post by manu081 on 2015-12-25
I got it working by first creating new folders to mount each share to:

> 
sudo mkdir /media/share1
sudo mkdir /media/share2
sudo mkdir /media/share3
sudo mkdir /media/share4


Then I simply adjusted the /etc/fstab file to the following:


> 
//[server-name]/share1 /media/share1 cifs uid=[linuxadminuser],username=[nasadminuser],password=[nasadminpass] 0 0


//[server-name]/share2 /media/share2 cifs uid=[linuxadminuser],username=[nasadminuser],password=[nasadminpass] 0 0


//[server-name]/share3 /media/share1 cifs uid=[linuxadminuser],username=[nasadminuser],password=[nasadminpass] 0 0


//[server-name]/share4 /media/share4 cifs uid=[linuxadminuser],username=[nasadminuser],password=[nasadminpass] 0 0




Everything appears to be working correctly now. I know adding your username/password to the fstab file is not ideal, but I'm going to leave it as-is because I don't really have personal information on the machine or hard drive to worry about.

Thanks for the help!

---

### Post by dave205 on 2016-01-07
so how do you get around the error "mount: only root can mount //servershare/sharename on /media/share1"?

when I boot my computer, I see a new mount in file explorer but when I click on it, I get the above error.

I have tried using the UID of 0 and the UID of 1000. 0 for root, 1000 for the user

---

### Post by dave205 on 2016-01-13
bump?

---

### Post by davehenson on 2016-01-19
Dave205, 
I found that I had to add "users" to the end of the fstab file entry. 

Like this
```
[COLOR=#000000]*//[server-name]/share1 /media/share1 cifs uid=[linuxadminuser],username=[nasadminuser],password=[nasadminpass],users 0 0*[/COLOR]
```

---

