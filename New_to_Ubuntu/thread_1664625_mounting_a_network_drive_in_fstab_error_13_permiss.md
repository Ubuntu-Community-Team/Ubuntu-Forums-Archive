---
title: "mounting a network drive in fstab error 13 permission denied"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by Ddraig on 2011-01-11
Hi I'm a total ubuntu newb running lucid on a dell mini 10.

I have got a readynas nv+ and i want to mount one of the user shares at boot.

I can mount it through nautilus no problems but I can't get it to mount at boot.

The NAS can use both NFS and CIFS, which would be better to use?

With CIFS my fstab is as follows ( I have tried many different variations )

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=d7f23766-0188-455c-8263-db8657c0752a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4790fb72-8792-4b17-b377-7681439592fe none            swap    sw              0       0
#to mount nas
//nas/lily   /mnt/nas       cifs rw,guest,gid=1002  0 0


When I run sudo mount -a I get the following error

> mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)



Help pls

---

### Post by Ddraig on 2011-01-11
bump

sorry but i've spent all day on this and i'm getting very frustrated.

---

### Post by dBuster on 2011-01-11
I just recently setup a new NAS at home.  I followed this guide [MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

The only exception being when it came to the server name I used the ip address of the drive.  No problems what so ever and I have actually created a map to my private part of the drive as well as to the shared part of the drive.

My fstab line looks something like this

```
//ipaddress/sharename /media/nameofmount cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

where the ipaddress is of course the ip of the drive and the  name of mount is the name of the folder I created to be the mount point or name I see in the PLACES menu.

---

### Post by Morbius1 on 2011-01-11
I don't see anything wrong with that line in fstab assuming //nas/lily allows guest access.

Can you get access using the gvfs way. Either:

```
nautilus smb://nas/lily
```OR
```
gvfs-mount smb://nas/lily
```

[COLOR=Blue]EDIT: There is one thing you can try. Add one more option in your fstab line:[/COLOR]
>  //nas/lily   /mnt/nas       cifs rw,guest,[COLOR=Blue]nounix[/COLOR],gid=1002  0 0 			 		

---

### Post by Ddraig on 2011-01-11
Thanks for your help,

> **Morbius1 said:**
> I don't see anything wrong with that line in fstab assuming //nas/lily allows guest access.

Can you get access using the gvfs way. Either:

```
nautilus smb://nas/lily
```OR
```
gvfs-mount smb://nas/lily
```

[COLOR=Blue]EDIT: There is one thing you can try. Add one more option in your fstab line:[/COLOR]



both methods allow me to mount manually,

I've also put the nounix option in fstab, but still keep getting error 13 when running sudo mount =a.  

Any other ideas?

---

### Post by Morbius1 on 2011-01-11
I don't have an answer at the moment but I do have a workaround - not a solution.

You could go to System > Preferences > Startup Applications > Add.
In the "Command" box enter: 
```
 gvfs-mount smb://nas/lily
```After you login it will mount the remote share automatically.

The down side to this is where gvfs-mount mounts the share. It in a hidden directory at:
> /home/user-name/.gvfs/lily at nasIf you can live with it being in a hidden directory then that's fine. If not you can create a symbolic link to a "real directory":
```
ln -s /home/user-name/.gvfs/"lily at nas" /mnt/nas
```You could also use Gigolo to create the automounting but you will still have to create the symlink: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)
There are advantages to using the Gigolo method.

Just so you know I added your line to my own fstab changing the remote location and mount point and it runs fine. It almost sounds like the nas is not accepting guest access.

---

### Post by Ddraig on 2011-01-12
Thanks for your help.  Even though the NAS should have been able to accept guests because it had been accessed previously through a windows machine it nwanted the windows user name and password for some reason.

---

