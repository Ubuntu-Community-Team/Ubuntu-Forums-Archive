---
title: "help with mounting drives"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by kiran.tambe08 on 2008-12-15
is there any way by which the drives will be mounted at startup or atleast when a drive is to b mounted the password shouldnt be asked

---

### Post by 2hot6ft2 on 2008-12-15
Applications>System Tools>NTFS-Configuration Tool

If it's not there then install it in System>Administration>Synaptic Package Manager by searching for ntfs-config and install it.

Make sure the drive you want to auto mount is UNMOUNTED then open up the NTFS-Configuration Tool then select the drive you want and click Apply in the next window select enable write support for which ever it is (internal or external) and click OK. All done

Now it will auto mount with read/write support after you reboot.

---

### Post by drs305 on 2008-12-15
You can place an entry in fstab that will automatically mount during the boot process. Exactly what entry you make depends on what type of file system you are trying to mount.

Here is a link to fstab:
[Fstab]("https://help.ubuntu.com/community/Fstab")

If they are ntfs, install "ntfs-config" and run System, Admin, NTFS configuration tool.

If you don't know the file types you can run and look at the 'Type' column:
```

df -Th

```

---

### Post by Titan8990 on 2008-12-15
Yep, just have to drive to the /etc/fstab folder


Use this guide: [http://ubuntuforums.org/showthread.php?t=283131&highlight=fstab](http://ubuntuforums.org/showthread.php?t=283131&highlight=fstab)

If you have trouble understanding anything or run in to issues, feel free to post back here.

---

### Post by Duck2006 on 2008-12-15
To mount windows partitions.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

To mount linux partitions.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by logos34 on 2008-12-15
for ntfs AND ext3:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by Michael.Godawski on 2008-12-15
> is there any way by which the drives will be mounted at startup or atleast when a drive is to b mounted the password shouldnt be asked

If you post the outputs of these commands we can tell you what entry you have to add to the fstab file, so that the drives will be mounted at start up.
```

sudo fdisk -l
```
```
cat /etc/fstab
```

---

### Post by kiran.tambe08 on 2008-12-16
i got ntfs config i did wat u told me to but i cannot click apply until i enter the mount point. wats the mount point

---

### Post by logos34 on 2008-12-16
try something like 

/media/windows1

---

### Post by Michael.Godawski on 2008-12-16
>  		i got ntfs config i did wat u told me to but i cannot click apply until i enter the mount point. wats the mount point

Please post the output from ```
sudo fdisk -l 
```first.
If there isn't any mount point specified, you can create your own: like in your home or media directory;
for instance
```
sudo mkdir /media/data
```
But I am currently not sitting at my Ubuntu machine so be careful with my advices ):P.

---

### Post by kiran.tambe08 on 2008-12-16
problem solved thanx guys, but how do u keep it mounted but not seen on the desktop

---

### Post by Michael.Godawski on 2008-12-16
open up the gconf editor
```
gksudo gconf-editor
```navigate to (from the top of my head something like) app > nautilus > desktop .... might err here
in the options on the right screen you should be able to check and un-check the volumes you want to be displayed on the desktop.

---

### Post by rlunger on 2008-12-16
> **kiran.tambe08 said:**
> i got ntfs config i did wat u told me to but i cannot click apply until i enter the mount point. wats the mount point

The mount point is simply a folder (i.e., /mnt/windows or /media/cdrom) in your local file system at which another file system is connected.  It's kind of like you're grafting a branch onto a tree - the mount point is where you want to put the branch.

---

### Post by drs305 on 2008-12-16
> **kiran.tambe08 said:**
> problem solved thanx guys, but how do u keep it mounted but not seen on the desktop

Run this command to hide *all* mounted volumes. Change it back to 'true' to display them. 
```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'
```


The path MG gave you was correct (good memory, MG). In gconf-editor, navigate to: apps/nautilus/desktop/volumes_visible    
Then tick or untick the setting as you desire.

---

### Post by logos34 on 2008-12-16
> **drs305 said:**
>  
```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'
```

neat command! Sure faster than saying, 'ok, open gconf-editor>apps>nautilus..., then click on, blah blah...'

---

### Post by Duck2006 on 2008-12-16
This does it all for you.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

