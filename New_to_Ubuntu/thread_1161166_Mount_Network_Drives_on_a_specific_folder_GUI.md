---
title: "Mount Network Drives on a specific folder GUI"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by Kosimo on 2009-05-16
Hello!

I have two questions: 
1) Where are mounted windows shared drives? because I can't see them on /media( 


2) Can I mount a windows network drive wherever I want, with some easy GUI program?


Thanks!

---

### Post by stalker145 on 2009-05-16
> **Kosimo said:**
> Hello!

I have two questions: 
1) Where are mounted windows shared drives? because I can't see them on /media( 


2) Can I mount a windows network drive wherever I want, with some easy GUI program?


Thanks!

Open up nautilus and type ```
smb://xxx.xxx.xxx.xxx
```where the x's are, obviously, your shared address. You'll see a shortcut load up in the top left panel of nautilus (all of this assuming default configuration).

If you want a permanent mount at boot, you can edit it into your fstab file.

---

### Post by Kosimo on 2009-05-16
> **stalker145 said:**
> Open up nautilus and type ```
smb://xxx.xxx.xxx.xxx
```where the x's are, obviously, your shared address. You'll see a shortcut load up in the top left panel of nautilus (all of this assuming default configuration).

If you want a permanent mount at boot, you can edit it into your fstab file.

Thanks for answering!  

But I would like to know if there is any easy way to mount them on my filesystem!

---

### Post by Kosimo on 2009-05-16
bump

---

### Post by stalker145 on 2009-05-17
> **Kosimo said:**
> Thanks for answering!  

But I would like to know if there is any easy way to mount them on my filesystem!

Is [this]("http://www.debianadmin.com/mount-network-file-systems-nfssamba-in-ubuntu.html") more like what you are looking for?

---

### Post by lukenz on 2009-05-17
Hello

The mountmanager package is a gui for altering the fstab file.  I think it has a plugin for adding network drives.

Are you using wireless?  If so, permanent mounts in the fstab file might not be the best option..  Let me know if this is the case and I'll tell you another way.


Luke

---

### Post by lukenz on 2009-05-17
Also you will need to have smbfs or similar installed.

Luke

---

### Post by Kosimo on 2009-05-17
Thank you guys!


I'm using mountmanager but when running it it doesn't do anything. Does it have a GUI?   

This is the output I get: 

```
mountmanager
3 records in /etc/fstab were detected. 
[G] DBus interface was created
[G] All devices were recieved
[I] Storage device was detected: "/dev/sr0" 
[I] Storage device was detected: "/dev/sda4" 
[I] Storage device was detected: "/dev/sda3" 
[I] Storage device was detected: "/dev/sda2" 
[I] Storage device was detected: "/dev/sda1" 
[I] Storage device was detected: "/dev/sda" 
[G] Parsing of  "/usr/share/mountmanager/options/common.xml"  was successful 
[G] Parsing of  "/usr/share/mountmanager/options/ntfs-3g.xml"  was successful 
Segmentation fault

```

---

### Post by lukenz on 2009-05-17
Did you run this from the terminal?  There should be a menu item for it.  If you did from the terminal use sudo first.

Yes, from memory it does have a gui.

Here is another one:

> 
PySDM is a PyGTK Storage Device Manager that allows full customization of hard
disk mountpoints whitout manually access to fstab.
It also allows the creation of udev rules for dynamic configuration of storage
devices

The reason I suggested mount manager is because i think it has a plugin for adding network drives.  Are you using wireless?  There can be an issue when putting network drives in fstab.  If they try to mount before the network is connected they wont until you run sudo mount -a.  If they don't unmount before the network disconnects (at shutdown) there can be errors.

The way i did it was to add the mount commands to a shell script and have it execute only after the network is connected.  I did this using WICD to manage the network as you can get it to run a script when the network connects.  I ran another command so that they unmount prior to the network disconnecting on shutdown.

---

### Post by Lightstar on 2009-05-21
> **Kosimo said:**
> Thank you guys!


I'm using mountmanager but when running it it doesn't do anything. Does it have a GUI?   

This is the output I get: 

```
mountmanager
3 records in /etc/fstab were detected. 
[G] DBus interface was created
[G] All devices were recieved
[I] Storage device was detected: "/dev/sr0" 
[I] Storage device was detected: "/dev/sda4" 
[I] Storage device was detected: "/dev/sda3" 
[I] Storage device was detected: "/dev/sda2" 
[I] Storage device was detected: "/dev/sda1" 
[I] Storage device was detected: "/dev/sda" 
[G] Parsing of  "/usr/share/mountmanager/options/common.xml"  was successful 
[G] Parsing of  "/usr/share/mountmanager/options/ntfs-3g.xml"  was successful 
Segmentation fault

```

I'm also getting segmentation fault.
That's when I'm using the terminal, if I just use the menu item clicky, I get nothing at all, so I guess it's the same error but it's not shown since I'm not in terminal.

It's the same thing wether I use sudo or not.

---

### Post by lukenz on 2009-05-21
Could you please post the contents of your fstab file so I can take a look?  I suspect that there might be an invalid entry in it.

Are you getting errors on startup or shutdown?

---

### Post by pmla on 2009-07-05
also getting segmentation fault in Mount Manager when I run it from terminal.
If I run it from GUI it just deos not start at all.

Here is mt fstab file

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=f049e45d-51a9-44c3-ab3e-45b5205bdc51 /               ext3    relatime,erro$
# swap was on /dev/sda6 during installation
UUID=caf81dd0-14ee-477b-b854-e4cd3e5fffdf none            swap    sw           $
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by lukenz on 2009-07-06
I think the issue is "ext3 relatime,erro$".  I will have a look at how mine is configured when I get home.  
 
Could you please also post the output of: sudo fdisk -l

---

### Post by pmla on 2009-07-07
I actually removed it but if it works I can install it again.

to make my shared network drives to worked I manually edited the /etc/fstab .... now it looks like this:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=f049e45d-51a9-44c3-ab3e-45b5205bdc51 /               ext3    relatime,erro$
# swap was on /dev/sda6 during installation
UUID=caf81dd0-14ee-477b-b854-e4cd3e5fffdf none            swap    sw           $
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# Mount our network drive
//192.168.1.33/D$ /media/Server00-D smbfs guest 0 0
//192.168.1.33/Torrent /media/Server00-Torrent smbfs guest 0 0
//192.168.1.33/Security /media/Server00-Security smbfs guest 0 0
//192.168.1.33/Backup /media/Server00-Backup smbfs guest 0 0
//192.168.1.1/www-temp /media/Cerebrus-www-temp smbfs guest 0 0



fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2b98cf53

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30309   243457011    7  HPFS/NTFS
/dev/sda2           30310       60801   244926990    5  Extended
/dev/sda5           30310       60050   238894551   83  Linux
/dev/sda6           60051       60801     6032376   82  Linux swap / Solaris

---

### Post by lukenz on 2009-07-07
Unless you have already done so, before making any more changes to the fstab file  make a backup so that you can restore it if your computer fails to boot.


I still think the "segmentation fault" problem might be caused by "relatime,erro$".

Mine says: "relatime,errors=remount-ro 0 1"

remount-ro means that it will mount the drive as read only if there are errors during the mounting process.  This prevents any data loss.  Good info about the dump (the 0) and pass (the 1) can be found here: [http://wiki.archlinux.org/index.php/Fstab](http://wiki.archlinux.org/index.php/Fstab)

My advice is to replace "relatime,erro$" with:

```
relatime,errors=remount-ro
```

The dump and pass, you can make a decision based on the above link.

Are any of your other drives listed with fdisk being mounted?  Do you want them to?

Great info on fstab here [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)


Good luck

Luke

---

### Post by Boondoklife on 2009-07-07
> **Kosimo said:**
> Hello!

I have two questions: 
1) Where are mounted windows shared drives? because I can't see them on /media( 


2) Can I mount a windows network drive wherever I want, with some easy GUI program?


Thanks!

I know this is a little late, but they are mounted in the .gvfs folder under your profile. I like to keep hidden files hidden so I just made a sym link to the folder ln -s /home/username/.gvfs /home/username/NetworkShares

This way you can browse to it with any app.

---

### Post by mtz1 on 2009-11-04
BoondokLife,

Thanks.  Works great.

```
ln -s /home/username/.gvfs /home/username/NetworkShares
```

---

### Post by tele_mark on 2009-11-11
Hi

I found this thread in a search last night when I was trying to solve the same problem the OP put fourth. Namely, my DLink DNS-323 NAS drive wasn't showing up as an option for storage under sbackup, amongst other apps. 

The contents of this thread, and ultimately, the reference to the .gvfs directory under \home\user\, solved that problem, and I created the symlink as above.

However, I still can't see the shared files of my XP machine as save options, even though I can browse them from the file manager. I'm assuming these are under another directory than .gvfs? Does anyone know which one it is? 

thanks

---

### Post by Boondoklife on 2009-11-11
As far as I know, all gnome mounting goes under .gvfs, what do you mean you can not see the files? It could be just a permissions issue, or the app may not be able read/use the files you are trying access

---

### Post by tele_mark on 2009-11-11
Well, say I choose FILE>Save Page As under Firefox here -- knowing now about the .gvis file, I can navigate there as a choice for saving. But, when I click it, I only see my Dlink NAS drive there, not my shares on the XP machine, even though I can see the XP shares and navigate to them, and save, delete stuff, etc. in the file manager.

---

