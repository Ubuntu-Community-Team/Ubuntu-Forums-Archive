---
title: "Mounting NTFS Partition"
date: 2005-06-08
forum: Networking &amp; Wireless
---

### Post by andrewsawyer on 2005-06-08
Hiya,

I am trying to mount a Win2003 share directory in Hoary, however I'm having problems.

The share set up and viewable in File Browser with a link to it in the tree.  Displaying properties gives:

Type: X-Directory/smb-share
Location: smb://mediacentre

I have set up a dir called mnt/music, however when I type the following I get the error shown:

root@ubuntu:/home/andrew # mount -t cifs -o username="Andy",password="xxxx" //Mediacentre/Music /mnt/music
mount: wrong fs type, bad option, bad superblock on //Mediacentre/Music,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I've changed the password to xxxx - it's not that I forgot to put it in - I'm not that much of a newbie :-)

I can access all the files through File Manager, however I can't get to them through XMMS or Mplayer, as I don't know the location through the location tree (what with it not being mounted at /mnt/music.  Oh, I can access the dir and play music through my girlfriends laptop over Wi-Fi with no probs, but thats running XP-Pro.

Your help would be much appreciated.

---

### Post by andrewsawyer on 2005-06-12
Anyone?

Help would really be appreciated on this.

Cheers,

Andy

---

### Post by bjorn on 2005-06-12
you need to "apt-get install smbfs"

your command line looks good except change cifs to smbfs

check out [http://www.ubuntulinux.org/wiki/SettingUpSamba](http://www.ubuntulinux.org/wiki/SettingUpSamba) for more details

---

### Post by andrewsawyer on 2005-06-13
Thats great thank you.  I'm not at home right now, but I will give it a try as soon as I am back.  Thank you for the help.

---

### Post by Buffalo Soldier on 2005-06-13
You might want to check the [Networking](http://ubuntuguide.org/#networking) section at the [UbuntuGuide.org](http://ubuntuguide.org/).

---

### Post by andrewsawyer on 2005-06-13
Ok, I've got it working, however I'm still using -cifs, as mounting per [http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs) gives the error:

cli_negprot: SMB signing is mandatory and we have disabled it.
10743: protocol negotiation failed
SMB connection failed

So a question.  What are the entries that I should put into fstab to get the partitions to automount at boot?  The mounting string that I am using at the moment is:

sudo mount -t cifs -o username="Andy",password="*******" //10.0.0.3/tvseries /mnt/tvseries

If someone could tell me how to put this into fstab it would be much appreciated.

---

### Post by diebels on 2005-06-13
The fstab file has these fields
```
# <file system> <mount point> <type> <options> <dump> <pass>

```
So you would put in:
```

10.0.0.3/tvseries /mnt/tvseries cifs username="Andy",password="*******" 0 0

```

---

### Post by andrewsawyer on 2005-06-13
Much appreciated.

Thank you

---

