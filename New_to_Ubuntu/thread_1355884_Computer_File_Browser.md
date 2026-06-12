---
title: "Computer File Browser"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by kakashi_12 on 2009-12-15
Can I safely rename (filesystem) when going to properties of that drive, without messing up the system? Can I do the same for my Windows drive safely without affecting Windows? When I change the name of it, will it change the name in it in the other user accounts? If I do allow a normal user to access my Windows drive, can I stop them in Linux (settings Linux permissions) to a particular folder (since Linux overrides the NTFS permissions)? Thanks.

---

### Post by presence1960 on 2009-12-15
> **kakashi_12 said:**
> Can I safely rename (filesystem) when going to properties of that drive, without messing up the system? Can I do the same for my Windows drive safely without affecting Windows? When I change the name of it, will it change the name in it in the other user accounts? If I do allow a normal user to access my Windows drive, can I stop them in Linux (settings Linux permissions) to a particular folder (since Linux overrides the NTFS permissions)? Thanks.

To rename a device you need to change the label from gparted on Live CD. You can access gparted through terminal ```
gksu gparted
```
OR System > Administration > Gparted

Right click on the device you want to rename in gparted(see pic1). Choose Label.

Now change Label (see pic2). Click OK. Click Apply (green check mark) on toolbar. Close gparted when changes are completed. next time you open a file browser that device will show as what you put in Label in gparted.

Third pic is a file browser showing devices with my labels.

Everything in Filesystem device you want to leave alone as that is your Ubuntu root partition. You should not change anything in there as you may render your Ubuntu broken.

---

### Post by ajgreeny on 2009-12-15
I'm not quite sure what you are wanting to do, but I think the easiest way to do the first part of what you want is to use the live CD and start gparted.  Using this you can label each partition/filesystem to your chosen label.  The partitions will now all appear as their labels in the Places list in nautilus, and the icons on the desktop of mounted partitions.  These labels will also be used in all ubuntu users accounts, as they are not just set by your user, but by root, gparted being used as root.

With regard to your second question about windows, again I am not sure what you want, but if other users are not given admin privileges, I don't think they will be able to write to the ntfs partition, but I admit I am not totally sure about that.  Even though I have a Windows XP partition, I read from it but never write to it. You will need to await a further answer to that.

---

### Post by philinux on 2009-12-15
If he's running karmic no need for live cd can be done easily with System>Admin>Disk Utility.

Although I've changed the partition name to root it still shows as Filesystem. Maybe it hard coded.

---

### Post by kakashi_12 on 2009-12-15
what's karmic? a distro?

What I want is...
to be able to allow users to access the XP NTFS drive, but not have permissions to MY folder(s). I think what I'll try if I can do, is maybe mount the drive, then right click the folder i want, go to permissions, and add linux permissions on that folder just for my username and deny the other user access. Hopefully that won't affect it in Win though. What do you guys think?

Check that... I just tried opening properties on the ntfs, and it was all grayed out. So that won't work I don't think. It says owner is Root. I don't think Ubuntu allows root log on through the gui, that I am aware of. I tried 'su' in the terminal, did not unlock anything. Then I went to the users and groups window/app in the gui and unlocked it, didn't work.

---

### Post by philinux on 2009-12-15
> **kakashi_12 said:**
> what's karmic? a distro?

What I want is...
to be able to allow users to access the XP NTFS drive, but not have permissions to MY folder(s). I think what I'll try if I can do, is maybe mount the drive, then right click the folder i want, go to permissions, and add linux permissions on that folder just for my username and deny the other user access. Hopefully that won't affect it in Win though. What do you guys think?

Check that... I just tried opening properties on the ntfs, and it was all grayed out. So that won't work I don't think. It says owner is Root. I don't think Ubuntu allows root log on through the gui, that I am aware of. I tried 'su' in the terminal, did not unlock anything. Then I went to the users and groups window/app in the gui and unlocked it, didn't work.

Karmic is ubuntu 9.10.

Set up a test user without admin rights and see what that user can do on the windows drive.

you could install ntfs-config and disable write access to the ntfs partition.

---

### Post by irfan_ on 2009-12-19
I have a java file to compile...but i cannot go to the location to compile it using my terminal...i dont know the code..One of my drive name is My Library and it is format in Ext3 from ubuntu.....please help me as soon as possible....
with regards..
irfan

---

### Post by kakashi_12 on 2009-12-19
sorry, but i think this is in the wrong thread. i think you need to start a new thread. i'm not exactly sure how to help you or what you mean either sorry. Someone here can help you though probably.

---

### Post by garyed on 2009-12-19
I'm not sure if this is what you want to do but
if you just want to put a name on a partition you can do :
```
sudo e2label /dev/sdb1 NewName 
```
to name or rename partition /dev/sdb1
It only works on ext2 ext3 or ext4 partitions though 
You can use ```
sudo fdisk -l
```
to find how your partitions are referenced.

---

### Post by kakashi_12 on 2009-12-19
thats ok. im just gonna leave as is. thanks though. i wanted to do it from gui, but its ok the way it is.

---

