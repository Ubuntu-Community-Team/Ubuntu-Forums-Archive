---
title: "Trying to share a folder but cant change permissions"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by aprillia99 on 2009-12-25
so installed samba and the smbfs.conf file and when i go to my second hard drive computer>file system>media and try to share it i get this natlius asking to add permissions and i click ok and get this error "ould not change the permissions of folder "HardDrive 1"     when i look at properties of the file it tells me im not the owner and i cant change the permissions

anyone know how i can fix that, plz and thanks in advance

---

### Post by taurus on 2009-12-25
What filesystem is your second harddrive?

---

### Post by aprillia99 on 2009-12-26
Fat32 i belive i reformatted them when i reinstalled ubuntu

file system vfat
file system type msdos

is what i see when i right click and properties it.

---

### Post by jonest1 on 2009-12-26
I'm going to assume you have the second hard drive mounted somewhere in your filesystem.  If you go to that directory in nautilus (file manager) and right-click and go to properties.  You will probably the owner and group in the Permission tab is root and root.  This means that you will not be able to edit the permissions as a regular user account.

There are two methods that I'm aware to edit ownership on root owned directories while not root.

#1:  Run 'gksudo nautilus' to launch the file manager as root.  Go to Accessories -> Terminal and run the command.  Type in the root password when prompted and then perform the requested action.  There may be a menu item for this, but I didn't see one.

#2.  Open a terminal and use the chown command.
     sudo chown -R user:group directory
Where user is the user account to own the directory and group is the group account.  The -R makes the change recursively, so, keep it out if this is not wanted.  See chmod to change the permissions.  

Once the ownership is changed, you should be able to simply launch nautilus as your normal user account to make additional adjustments.

---

### Post by jonest1 on 2009-12-26
Type mount and find the line item for your file system.  I do not believe that a fat file system will work out for you as I do not think it supports the type of file permissions you may require.  You may want to reformat in ext3.

---

### Post by taurus on 2009-12-26
> **jonest1 said:**
> I'm going to assume you have the second hard drive mounted somewhere in your filesystem.  If you go to that directory in nautilus (file manager) and right-click and go to properties.  You will probably the owner and group in the Permission tab is root and root.  This means that you will not be able to edit the permissions as a regular user account.

There are two methods that I'm aware to edit ownership on root owned directories while not root.

#1:  Run 'gksudo nautilus' to launch the file manager as root.  Go to Accessories -> Terminal and run the command.  Type in the root password when prompted and then perform the requested action.  There may be a menu item for this, but I didn't see one.

#2.  Open a terminal and use the chown command.
     sudo chown -R user:group directory
Where user is the user account to own the directory and group is the group account.  The -R makes the change recursively, so, keep it out if this is not wanted.  See chmod to change the permissions.  

Once the ownership is changed, you should be able to simply launch nautilus as your normal user account to make additional adjustments.

Maybe I am out of this loop a little too long but I don't think chown and chmod would work with fat32 filesystem.  You have to do that in /etc/fstab.

---

### Post by aprillia99 on 2009-12-26
basically i have 2 sata drive i would like to turn into a netowrk storage that my window machine and my ps3 and my ubuntu machine can save to and read from for video streaming and such, so will with ex3 can window read and write to a drive formatted with that??  

and what would u suggest to my needs?? exd3,ntfs,fat32?? i can reformat if need thx

---

### Post by bodhi.zazen on 2009-12-26
> **aprillia99 said:**
> basically i have 2 sata drive i would like to turn into a netowrk storage that my window machine and my ps3 and my ubuntu machine can save to and read from for video streaming and such, so will with ex3 can window read and write to a drive formatted with that??  

and what would u suggest to my needs?? exd3,ntfs,fat32?? i can reformat if need thx

Windows can not directly read or write to an ext 2/3/4 files system, it is the samba protocol that allows this, so yes you most certainly have a linux server with ext 2/3/4 and windows can rw to the share so long as samba is properly configured.

If you wish to change permissions of a FAT partition you will need to edit /etc/fstab . There are several graphical tools that will do this for you, ntfs-config, pysadm.

---

### Post by aprillia99 on 2009-12-26
ok and ubuntu can rw on ntfs? is there any downfall using ntfs?

---

### Post by bodhi.zazen on 2009-12-26
Ubuntu can RW ntfs yes. If, however, the ntfs partition has problems, often Ubuntu can not fix it, you would have to boot windows.

If you are running windows you will be fine. If you are not running windows I advise you back up your data, convert the partition to ext3 or 4, and restore your data.

---

