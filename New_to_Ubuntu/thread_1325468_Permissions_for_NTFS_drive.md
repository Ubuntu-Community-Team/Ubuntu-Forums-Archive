---
title: "Permissions for NTFS drive"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by originalsnuffy on 2009-11-13
Hi all,

I tried to access some music files on a NTFS disk.  Ubuntu sees the disk, but is asking for permissions.  To my knowledge, I have no passcode in Windows.  I tried both no passcode and also the Ubuntu passcode, and neither worked.

Any suggestions?

---

### Post by mrothgeb on 2009-11-13
Try this:
System / Admin / Login Window - Security tab: click Allow local system Admin login

Then:
System / Admin / users and groups: give root a password

Then
Sign out and sign in as root

Then:
Right click on the NTFS drive and see if you can edit its permissions to allow your regular login to Read write and execute

---

### Post by delcypher on 2009-11-13
Ubuntu is probably asking you for your password as it needs root permissions to mount the drive.

@mrothgeb - Yuck. I wouldn't encourage that graphical root... big no no. Probably won't work anyway as root account is disable in ubuntu by default.

@originalsnuffy
You can mount the device manually as follows in Terminal (Applications > Accessories > Terminal). The use of sudo will let you act as root and it will ask you to enter your login password.
```

#This command will list all drives attached to your computer you need to figure out which one you want to mount, it'll be something like /dev/sda2 or /dev/hdb1
sudo fdisk -l
#This command will mount your drive ( /dev/sdXX in the folder /mnt/), I'm assuming your ID is 1000, run the command id to find out what your id is.
sudo mount -o uid=1000,gid=1000,umask=022 /dev/sdXX /mnt/
#when you're done umount it
sudo umount /mnt

```

---

### Post by soni1770 on 2009-11-13
or, 

**gksudo nautilus**

then navigate to the drive and change the permissions
:popcorn:

---

### Post by lavinog on 2009-11-13
> **originalsnuffy said:**
> Hi all,

I tried to access some music files on a NTFS disk.  Ubuntu sees the disk, but is asking for permissions.  To my knowledge, I have no passcode in Windows.  I tried both no passcode and also the Ubuntu passcode, and neither worked.

Any suggestions?

can you post a screenshot of the dialog you are getting?  (press PrtScn on your keyboard)
It should be your ubuntu password (if you are an administrator of the computer)

Do not do the root login as mentioned before.

---

### Post by ajgreeny on 2009-11-13
If you want the NTFS drive to be permanently mounted install ntfs-3g (in by default, I think) and ntfs-config, and you can then run ntfs-config and set the mounting and permissions of the drive the GUI way.

---

### Post by mrothgeb on 2009-11-13
I recommended the root solution because i've had this problem and thats what fixed it.  Even though my login is an admin I did sufficient privileges to enable my media drive to be used by all the other users on my machine.  

My wife and I are in the same group admin so: R.W.E.
and our little sis is a user so just R

now all 3 can access the same movie file.

---

### Post by lavinog on 2009-11-13
> **mrothgeb said:**
> I recommended the root solution because i've had this problem and thats what fixed it.  Even though my login is an admin I did sufficient privileges to enable my media drive to be used by all the other users on my machine.  

My wife and I are in the same group admin so: R.W.E.
and our little sis is a user so just R

now all 3 can access the same movie file.

There are a couple of ways to adjust permissions using chown, chmod or adding each user to each others group.

having everyone using root is how things turn sour.

---

### Post by mrothgeb on 2009-11-13
> **lavinog said:**
> There are a couple of ways to adjust permissions using chown, chmod or adding each user to each others group.

having everyone using root is how things turn sour.

Noone uses root.  Root level access, I found, was necessary to change the permissions.  

I didn't know about chown or chmod.

---

### Post by lavinog on 2009-11-13
[Forum policy on log-in-as-root tutorials](http://ubuntuforums.org/showthread.php?t=716201)

here is some information on the use of sudo for root access: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by oldfred on 2009-11-14
All permissions for NTFS and for FAT are given at mounting. As previously mentioned use NTFS config or use pysdm whcih works for all types of partitions.

Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager

These will provide the additional detailed steps if you want to understand what pysdm is doing or to do it manually:
HowTo Mount NTFS Partitions Read Write in Ubuntu & Kubuntu
[http://ubuntu.swerdna.org/ubuntfs.html](http://ubuntu.swerdna.org/ubuntfs.html)
Auto mount NTFS Partition
[http://ubuntuforums.org/showpost.php?p=7342606&postcount=10](http://ubuntuforums.org/showpost.php?p=7342606&postcount=10)

---

