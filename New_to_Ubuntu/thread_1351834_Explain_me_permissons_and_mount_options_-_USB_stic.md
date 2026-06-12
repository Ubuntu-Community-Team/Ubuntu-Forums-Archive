---
title: "Explain me permissons and mount options - USB stick ext4"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by nomnex on 2009-12-10
16 GB USB stick Buffao (I am on jaunty). I format it with Gpart 8 GB ext4/8 GB fat (to use it on Windoze).

When I plug the USB the 2 volumes pop-up automatically - the auto mount feature is fine, but I don't want the windows to open on the desktop, how?

the ext4 part question:

Permission (see: printscreen):
Owner: root
Group: root

Problem: external usb stick formated in ext4. I want to mount it (preferably auto-mount, as it is now) in any box without encountering permission issues. How?

I welcome verbose explanation. It helps me not to only reproduce some commands, but to understand them.  Thank you.

---

### Post by jbrown96 on 2009-12-11
There are two aspects to Linux permissions: the people who have access and the access they are granted. There are three groups of people: owner, group, and others. There are three types of permissions read (2), execute (1), and write (4). You simply add the permissions that you want (i.e. read and write is 2+4=6). You get three sets of permissions, which get combined to form a three digit number. 

For example,
to give the owner, group, and others read and write access the permissions would be 666. To allow only the owner to read/write and group/others to read only, then the permissions would be 622.

Now that you have a basic understanding of permissions it's important to understand some best practices.

1) Execute permissions should very rarely be granted. There aren't very many good reasons for this, so avoid it and only apply it when necessary. Since execute (1) is the only odd numbered permission, then all combinations that include execute will be odd; avoid odd permissions.
2) It is more secure to give groups and owners permissions rather than others. A side note about owners and groups. the owners and groups are actually just numbers. Your "user" is actually a number (in particular 1000), so your files are actually owned by user 1000. Ubuntu translates this to be your username. This is a serious security implication. Let's say you give your user read/write permissions, if you take your USB drive to another computer with Ubuntu, then the user on there will be able to access your files. This is because the first user on that system is also user 1000. 
3) Granting permissions to "others" is generally a simple way to fix problems, especially with removable media. 

Here's my suggestion. Root shouldn't be the owner/group that those files belong to. Furthermore, if you plan to use this on systems where you are not the first user (1000), then you should also give "others" permission.

```
sudo chown -R $USER:$USER /media/
``` this command changes ownership to you. Once you type /media then press tab twice. You should get a couple directories. The one you are probably looking for is called disk (so /media/disk), but it could be something weird like buffalo or external. Once you are the owner, then you can fix the permissions. We are going to assume that you want to grant read/write permissions to everyone. ```
sudo chmod -R 666 /media/disk
``` but change that accordingly.

---

### Post by nomnex on 2009-12-11
Thank you that's clear.

```
sudo chown -R $USER:$USER /media/
```Will change owner ship of 'media' from 'root/root' (user/group) to user/user -R (recursively), but I am wondering:

q1a - On the default Ubuntu installation, with a USB stick plugged-in:
```
/media
```belongs to root (see: first print screen)

```
/media/ONE <my USB ext4 volume>
```also belongs also to root - my problem (see: second print screen)

However
```
/media/disk <USB fat32 volume>
```belong to me (see: third print screen). How?

q1b - What difference/benefit does it make changing ownership of the media directory
```
sudo chown -R $USER:$USER /media/
```vs. the ext4 volume only
```
sudo chown -R $USER:$USER /media/ONE
```q3 - Anytime I plug a USB stick formatted as ext4 in a new machine: It will auto-mount (with root permissions), then I will have to pass 2 commands (chown/chmod). Is this my only option?

q2 - What now if I am not member of the admin group on some machines (i.e. no sudo)?

q3 - Advice please: Is it bad practice on Linux-Ubuntu to format a USB stick in ext3/4? I have chosen to format the USB stick in ext4 after noticing fat32 was not preserving my permissions (backup documents/import documents USB <> PC).

---

### Post by Dennis N on 2009-12-11
Let's say the ext4 partition mounts at /media/name. You only want to change ownership and permissions of /media/name, not /media.

FAT partitions don't have any owners or permissions stored with their files, so when you mount that type of filesystem, the current user gets assigned ownership when they are mounted in Linux. That also explains why permissions are not preserved when you move files from ext3/ext4 to fat and back again.

When you format a partition with ext3 or ext4, root becomes the default owner since you are using sudo (root powers) to do that.

---

### Post by nomnex on 2009-12-11
@ Dennis N

Thank you to clear that up.

Advice about USB stick formatting. Does ext4 (knowing I will have to change ownership/permission every time I plug the stick in a new machine) formatting offer some benefit over Fat32 for a USB stick used on a Linux only environment?

---

### Post by Dennis N on 2009-12-11
You should not have to change ownership and permissions each time you plug in the usb device. I have a usb hard drive I formatted in ext3 and I only had to change the ownership and permissions once and that was it.

Fat filesystems have a file size limitation of 4gb.

Ext3/Ext4 on external drive will preserve permissions when transferred there and back.

---

### Post by nomnex on 2009-12-11
> **Dennis N said:**
> I have a usb hard drive I formatted in ext3 and I only had to change the ownership and permissions once and that was it.

Good news, thanks Dennis.

---

### Post by Cheesemill on 2009-12-11
> **nomnex said:**
> 16 GB USB stick Buffao (I am on jaunty). I format it with Gpart 8 GB ext4/8 GB fat (to use it on Windoze).
Do bear in mind that Windows only ever expects **one** partition on a USB device, it wont recognise any more than the first partition.

---

### Post by 3rdalbum on 2009-12-11
> **Cheesemill said:**
> Do bear in mind that Windows only ever expects **one** partition on a USB device, it wont recognise any more than the first partition.

Definitely not true. My external hard disk has Fat32, NTFS and Ext3 partitions on it. Windows mounts the Fat32 and NTFS partitions.

If you don't want the windows to open on the desktop, then in any Nautilus window go to Edit > Preferences, click the Media tab, and uncheck "Browse media when inserted". It annoys me too.

---

### Post by Cheesemill on 2009-12-12
> **3rdalbum said:**
> Definitely not true. My external hard disk has Fat32, NTFS and Ext3 partitions on it. Windows mounts the Fat32 and NTFS partitions.

If you don't want the windows to open on the desktop, then in any Nautilus window go to Edit > Preferences, click the Media tab, and uncheck "Browse media when inserted". It annoys me too.

What version of Windows are you using?

---

### Post by MooPi on 2009-12-12
I need a tangent to this thread. I have an 8GB sd flash module I use for file transfer on a netbook. It is fat32 and say I want to move a file larger than that what would be the best for an all Linux environment. Meaning there no need for fat32 should I use ext2/ext3/ext4 ?. The drive is used only for multimedia storage, music and video files.

---

### Post by boarderpatrol on 2009-12-12
Hey great post jbrown96.      Very informative an helped me fix a usb drive and get a nice understanding of chmod 666  an 777 and why!!

---

### Post by jbrown96 on 2009-12-12
> **MooPi said:**
> I need a tangent to this thread. I have an 8GB sd flash module I use for file transfer on a netbook. It is fat32 and say I want to move a file larger than that what would be the best for an all Linux environment. Meaning there no need for fat32 should I use ext2/ext3/ext4 ?. The drive is used only for multimedia storage, music and video files.

Fat32 can't handle individual files larger than 4GB, so that might matter for your video. Otherwise, there's no compelling reason to switch to a linux FS. The read/write performance would be better, but even HD video wouldn't have transfer problems, based on the file system.

It's generally not worth dealing with permission, unless you know what you're doing (my first post in this thread is a good intro).

---

### Post by nomnex on 2009-12-13
> **3rdalbum said:**
> If you don't want the windows to open on the desktop, then in any Nautilus window go to Edit > Preferences, click the Media tab, and uncheck "Browse media when inserted". It annoys me too.

Thanks for this one.

---

### Post by Dennis N on 2009-12-13
> **MooPi said:**
> I need a tangent to this thread. I have an 8GB sd flash module I use for file transfer on a netbook. It is fat32 and say I want to move a file larger than that what would be the best for an all Linux environment. Meaning there no need for fat32 should I use ext2/ext3/ext4 ?. The drive is used only for multimedia storage, music and video files.

If you want to simply move files between computers with the flash drive and they are less than 4gb, I would use FAT. If the flash drive is formatted in ext3/ext4, you will quite possibly encounter access problems (ownership and permissions) when plugging the flash drive into a different Linux computer.  Ext file systems work great if the external drive is used with ONE machine.

Alternative: You can also transfer any size file via network connection, such as SSH.

---

### Post by nomnex on 2009-12-13
Dennis N

ext3/ext4 give you permission/ownership problems if you transfer files on another computer, while Fat32 does not preserve permission.

In either ways you have to use bash commands to rectify right?

---

### Post by Dennis N on 2009-12-13
> **nomnex said:**
> Dennis N

ext3/ext4 give you permission/ownership problems if you transfer files on another computer, while Fat32 does not preserve permission.

In either ways you have to use bash commands to rectify right?

FAT transfer works like this:

On the USB with FAT, the file will really have no permissions stored with it. Linux (terminal) displays this, however:

-rwx------ dennis:root

*EDIT: above is how it appears if you browse TO the USB drive! On the computer, after transfer, you get: -rwx------ dennis:dennis so I also remove the erroneous section about group being root that was below.* 

I (dennis) have full read, write and execute permissions. No one else has permission to do anything.

---

### Post by nomnex on 2009-12-13
is there a script I can run recursively to list all files with incorrect file permissions in my home folder?

---

### Post by Dennis N on 2009-12-13
You don't necessarily want all the file permissions to be the same. Some files might be scripts that must be left executable. Folders have to remain executable or they won't open. So I would be careful. 

I don't have a script for what you describe, maybe someone else that knows more than I do might help with that.

Ext3/ext4 may cause ownership/permission problems only if you physically plug the drive into another computer (it does for me at least). But, I can transfer files to my desktop's external ext3 hard drive from another computer by using the local network, and the transfered files retain their ownership/permissions.

*EDIT: note that content of post 17 has been corrected!*

---

