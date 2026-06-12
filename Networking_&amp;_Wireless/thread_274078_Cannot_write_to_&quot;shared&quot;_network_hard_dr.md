---
title: "Cannot write to &quot;shared&quot; network hard drive!"
date: 2006-10-09
forum: Networking &amp; Wireless
---

### Post by linuxnewbie946 on 2006-10-09
I cannot write to my shared network hdd and I don't know why. I've been up all night google-ing it but I can't find it. The name of the hd is hdb1. Here is my /etc/fstab.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /home/D         vfat    user,defaults,utf8,umask=007,gid=46 0       1
/dev/hda6       /media/oldlinux ext3    defaults        0       2
/dev/hda5       /media/programs vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda2       /media/w2k      ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

I have changed the permissions on the folder and everything, even /dev/hdb1.

---

### Post by kidders on 2006-10-09
Hi there,

How are you sharing this filesystem? (NFS/Samba/etc?)

Assuming you are a member of group 46, you should be able to write to this filesystem, unless it is being mounted read-only due to some sort of error. **mount** will tell you if that's the case. Usually, GID 46 is "plugdev" ... what an odd choice!

By the way, can you write as root?

---

### Post by linuxnewbie946 on 2006-10-09
[COLOR="Blue"]Sorry to waste everyone's time, but at least I found the answer.
**GOOGLEING HELPS**
I am going to show you in a step-by-step howto how I got this working, because I saw a lot of similar unanswered posts like this on Google.
This walkthrough also includes some Samba stuff.[/COLOR]

[COLOR="DarkRed"]
The most important part of sharing a hdd is PERMISSIONS.[/COLOR]
Ironically, the site where I found the answers was called [Basic Linux Operations]("http://linux.about.com/od/linux101/l/blnewbie4_2_3.htm").
[COLOR="Green"]*NOTE: THIS TUTORIAL IS FOR SHARING A FAT32 HDB1. REPLACE HDB1 WITH YOUR HDD AND VFAT WITH YOUR TYPE. IF YOU WANT THIS TO BE AN AUTOMATED PROCESS, LOOK AT THE BOTTOM OF THIS POST FOR A SCRIPT TO DO THE FIRST STEP FOR YOU.*[/COLOR]
[LIST]
[*][COLOR="DimGray"]First, do this in a console:[/COLOR]
```
sudo umount /dev/**hdb1**
sudo chmod 777 /dev/**hdb1**
sudo chmod -R 777 /tmp
sudo mkdir /home/D
sudo mount -t **vfat** -o user,rw,exec,umask=000 /dev/**hdb1** /home/D
sudo chmod a=rwx /home/D
```

The last thing I did was visit this site: [http://ubuntuguide.org/wiki/Dapper#Samba_Server]("http://ubuntuguide.org/wiki/Dapper#Samba_Server")
[*][COLOR="#696969"]It told me to enter the following codes into a console:[/COLOR]
```
sudo apt-get install samba smbfs
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
gksudo gedit /etc/samba/smb.conf
```

[*][COLOR="#696969"]In the file, find the follwing line[/COLOR]
```

...blah blah...
...
;  security = user
...
```

[*][COLOR="#696969"]and REPLACE it with this.[/COLOR]
```
  security = share
```

[*][COLOR="#696969"]It then told me to add the following to the end of the file:[/COLOR]
```
[public]
  comment = Public Folder
  path = /home/D
  public = yes
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup
```

[*][COLOR="#696969"]Next, save the edited file, and run these command in the console:[/COLOR]
```
sudo testparm
sudo /etc/init.d/samba restart
```
[/LIST]
You're Done!

NOTA BENE: I HAVE WRITTEN A SIMPLE SCRIPT TO HELP YOU WITH THE FIRST STEP:

Copy and paste this into /usr/bin/stepscript.
```
#!/bin/bash
echo -en "HDD (ex. hda5, hdb1): "
read reply
echo -en "HDD TYPE (ex. ntfs, vfat): "
read type
hd=/dev/$reply
sudo umount $hd
sudo chmod 777 $hd
sudo chmod -R 777 /tmp
sudo mkdir /home/D
sudo mount -t $type -o user,rw,exec,umask=000 $hd /home/D
sudo chmod a=rwx /home/D
```
In a terminal run:
```
sudo chmod +x /usr/bin/stepscript
stepscript
```

---

### Post by linuxnewbie946 on 2006-10-09
> **kidders said:**
> Hi there,

How are you sharing this filesystem? (NFS/Samba/etc?)

Assuming you are a member of group 46, you should be able to write to this filesystem, unless it is being mounted read-only due to some sort of error. **mount** will tell you if that's the case. Usually, GID 46 is "plugdev" ... what an odd choice!

By the way, can you write as root?

Even though I solved it, I will answer your questions.
I am using Samba.
I am not a member of GID 46.
I can write to it as root.

Thank you for your help!

---

### Post by kidders on 2006-10-09
No problem :-)

One thing worth noting though ... the procedure you outline couldn't possibly be any less secure. _There is almost no way you could more comprehensively obliterate Linux's security precautions._ What you describe should work quite well, but should not be attempted on a computer/network that has any more than one user.

---

