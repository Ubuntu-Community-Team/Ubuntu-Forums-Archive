---
title: "mount a windows drive on startup"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by funkyali on 2009-03-10
Hi

I am able to access some shared folder/drives on my other windows pc. I am using Ubuntu 8.10. 

what I would like my setup to do is to mount the shared folders on start up and if they are not availible (i.e the windows pc is turned off) then to just fail gracefully)

Another question when I go to my shared folders/drives on my ubuntu machine I see some folders has $ at the end what does this mean? for example C$ I take it this is my C: but when I click on it it asks me for a password. what password is this can I mount a drive that is password protected as at the moment I am sharing without passwords and I would like to secure it.

---

### Post by Peter09 on 2009-03-10
You need to use a file call 'fstab' to mount your share at boot time. 

Its worth looking around the internet for the details of the syntax to mount shares in Fstab.

---

### Post by tarps87 on 2009-03-10
> **funkyali said:**
> Hi

I am able to access some shared folder/drives on my other windows pc. I am using Ubuntu 8.10. 

what I would like my setup to do is to mount the shared folders on start up and if they are not availible (i.e the windows pc is turned off) then to just fail gracefully)

Another question when I go to my shared folders/drives on my ubuntu machine I see some folders has $ at the end what does this mean? for example C$ I take it this is my C: but when I click on it it asks me for a password. what password is this can I mount a drive that is password protected as at the moment I am sharing without passwords and I would like to secure it.


For mounting windows shares on boot you will need to add them to the fstab file:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

If you would like help with this can you post the output of
```
sudo fdisk -l
sudo blkid
```
(l = lower case L)

For the windows share this is probably you windows login username and password, some installs of windows share the enter c: drive, you may want to remove this share and use a file one the c: drive instead. 

> **funkyali said:**
> 
I mount a drive that is password protected as at the moment I am sharing without passwords and I would like to secure it

Is this a network share/drive or local drive?

---

### Post by vginov on 2009-03-10
The command goes like this 

**sudo gedit /etc/fstab **

In side the FSTAB file you need to do the following (Change it according to your hard disk )

**/dev/hda1       /mnt/WinXP      ntfs-3g      quiet,defaults,locale=en_US.utf8,umask=0	0 0**

/dev/hda1 = device name(if SATA then sda)
/mnt/WinXP= Mount Point 
ntfs-3g   = File system Type 


There is another one more demaon called AUTOFS in RedHat but I am not sure about it in Ubuntu

---

### Post by tarps87 on 2009-03-10
> **vginov said:**
> 
/dev/hda1 = device name(if SATA then sda)


In Ubuntu UUID's are now used and all drives are identified as sdx due to there driver it is using

---

### Post by joey-elijah on 2009-03-10
or mount/automount them via a programme called 'NTFS Configuration' that you can find in add/remove.

No faffing about with files just open the programme, select the drives and that's, er, that!

---

### Post by funkyali on 2009-03-10
> **joey-elijah said:**
> or mount/automount them via a programme called 'NTFS Configuration' that you can find in add/remove.

No faffing about with files just open the programme, select the drives and that's, er, that!

I installed it but it does not give and option to select drives.


These shared drives/folders are on another desktop pc Harddrive that I want to access on a ubuntu 8.10 laptop.

---

### Post by tarps87 on 2009-03-10
> **funkyali said:**
> I installed it but it does not give and option to select drives.


These shared drives/folders are on another desktop pc Harddrive that I want to access on a ubuntu 8.10 laptop.

I haven't used the ntfs configuration program in a while. So I can't help with that. The other way should be one line once I have the output of the previous two commands.

Assuming you are using windows on the other pc you should be able to right click -> properties -> sharing(tab) now you can select the users you wish to have access to the file/folder with that users password.
If the other pc is running Ubuntu, if you search in "add programs" for samba you should see two GUI configuration programs, the one called samba is the simplest the other one (gsamba) is a more advanced tool

---

### Post by funkyali on 2009-03-10
> **tarps87 said:**
> I haven't used the ntfs configuration program in a while. So I can't help with that. The other way should be one line once I have the output of the previous two commands.

Assuming you are using windows on the other pc you should be able to right click -> properties -> sharing(tab) now you can select the users you wish to have access to the file/folder with that users password.
If the other pc is running Ubuntu, if you search in "add programs" for samba you should see two GUI configuration programs, the one called samba is the simplest the other one (gsamba) is a more advanced tool

The first command returned this
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd91ac89e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2           19327       19457     1052257+  82  Linux swap / Solaris
/dev/sda3            1825        5471    29294527+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 252 MB, 252706816 bytes
255 heads, 63 sectors/track, 30 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d1bc490

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          30      240943+   b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 1) logical=(0, 1, 1)

```

the second command returned this
```
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: LABEL="linpus" UUID="8250323c-6b17-4f6f-8ab9-60e0a96b00aa" TYPE="ext2" 
/dev/sda2: TYPE="swap" UUID="e671a70f-6d42-451e-be21-83fbac9a0ebb" 
/dev/sda3: UUID="e0a7e8ef-f411-4b5b-b074-5046a0b663bd" TYPE="ext3" 
 
```

---

### Post by tarps87 on 2009-03-10
Ok maybe one more command
```
sudo vol_id -u /dev/sdb1
```

Is this a acer aspire one?

---

### Post by funkyali on 2009-03-10
It is an acer aspire one it has 160gig and is dual booting with Linus linux distro and ubunto. I might put XP on it but not at the moment.

---

### Post by tarps87 on 2009-03-10
This will make the directory where the drive will be mounted
```
sudo mkdir /media/windows
```

This opens the fstab file
```
sudo gedit /etc/fstab
```

Add this line to the end of the file followed by a blank line(some files need the blank line at the end so it is safer to add it)
# windows drive
# /dev/sdb1
UUID=**"output from sudo vol_id -u /dev/sdb1"** /media/windows  ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0

This will add a shortcut to the desktop
```
ln -s /media/windows ~/Desktop/windows
```

This will add a shortcut in /home
```
ln -s /media/windows ~/windows
```

I thought I recognised the linpus drive label I'm using the same one but it's running Ubuntu, Slackware and Arch

---

### Post by funkyali on 2009-03-10
I tried that last command and it gave me the following error
```
/dev/sdb1: error opening volume

```

---

### Post by tarps87 on 2009-03-10
> **funkyali said:**
> I tried that last command and it gave me the following error
```
/dev/sdb1: error opening volume

```

Can you mount the drive normally?

Adding the following line instead my work but it is worrying that vol_id can't get access

# windows drive
# /dev/sdb1
/dev/sdb1 /media/windows  ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0

If this doesn't work try:
```
sudo -t ntfs-3g mount /dev/sdb1 /media/windows 
```

This may be why the other ntfs config tool did not work

---

### Post by stchman on 2009-03-10
> **funkyali said:**
> Hi

I am able to access some shared folder/drives on my other windows pc. I am using Ubuntu 8.10. 

what I would like my setup to do is to mount the shared folders on start up and if they are not availible (i.e the windows pc is turned off) then to just fail gracefully)

Another question when I go to my shared folders/drives on my ubuntu machine I see some folders has $ at the end what does this mean? for example C$ I take it this is my C: but when I click on it it asks me for a password. what password is this can I mount a drive that is password protected as at the moment I am sharing without passwords and I would like to secure it.

You will have to use Samba.

My personal thoughts on Samba are that Linux boxes have a difficult time connecting to Windows shares.

Windows boxes can connect very easily to Linux shares that use Samba.

I use NFS for sharing all my Linux boxes and since I do not use Windows anymore I have no need for Samba.

You need to install Samba and then you might be able to connect to the Windows box via Places--->Networks.

---

### Post by funkyali on 2009-03-11
> **tarps87 said:**
> Can you mount the drive normally?

Adding the following line instead my work but it is worrying that vol_id can't get access

# windows drive
# /dev/sdb1
/dev/sdb1 /media/windows  ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0

If this doesn't work try:
```
sudo -t ntfs-3g mount /dev/sdb1 /media/windows 
```

This may be why the other ntfs config tool did not work
Its a new installation. what I have done is just gone to Places>Network it has seen my Windows PC on the network and I just double click on the folders that I have shared.

What do I need to replace in your example?

---

### Post by tarps87 on 2009-03-11
Deleted post my mistake, correct post below

---

### Post by funkyali on 2009-03-11
> **tarps87 said:**
> I this to do with the network issue or the drive you want to auto mount?




This is my previous post with the changes in it
Hi

I added the bit in the fstab file and restarted the machine and it did not auto mount it. Could it be that I'm connection to my network wirelessly and therefore there would have to be a network connection in order for it to work?

Could I also create those shortcuts in the same process that this will mount the drive as I dont want it to be there if it is not online.

Thanks for all you help I really appreciate it.

---

### Post by tarps87 on 2009-03-11
> **funkyali said:**
> Hi

I added the bit in the fstab file and restarted the machine and it did not auto mount it. Could it be that I'm connection to my network wirelessly and therefore there would have to be a network connection in order for it to work?

Could I also create those shortcuts in the same process that this will mount the drive as I dont want it to be there if it is not online.

Thanks for all you help I really appreciate it.

Ah, sorry I got mixed up with two threads, the previous changes were for an internal drive, this one is for a windows network drive

This will make the directory where the drive will be mounted
```
sudo mkdir /media/windows
```

This opens the fstab file
```
sudo gedit /etc/fstab
```

Add this line to the end of the file followed by a blank line(some files need the blank line at the end so it is safer to add it)
# windows drive
# /dev/sdb1
**//server/share** /media/windows  cifs user=user,uid=1000,gid=100  0  0

replace //server/ with the machine name or machine ip e.g.
//192.168.123.2/
and
share with name of the folder being shared

In this case I am not sure about the links, as it is there link point to the directory where the share will be mounted, if it is not mounted the directory will be empty.

If you want to use a password on the share the current set up will ask you to enter your password.
To change this you can create a credentials file

```
sudo gedit /etc/samba/credentials
```

In this file out these two lines

username=your username
password=your password

Now make this file accessable only by root/admin and ro/read only
```
/sambachown root.root /etc/samba/credentials && sudo chmod 400 /etc/samba/credentials
```

now replace
replace "user=user" with "credentials=/etc
e.g.

]//server/share /media/windows  cifs user=user,uid=1000,gid=100  0  0

//server/share /media/windows  cifs credentials=/etc/samba/credentials,uid=1000,gid=100  0  0

Apologies for the confusion

---

### Post by funkyali on 2009-03-11
Hi Tarps,

Thanks for you help.

I will do the following as your post suggested. I have a few other questions.

1. At the moment I just go "places>network>lounge" (of course my windows pc is named lounge). When I click on lounge it should me the folders I share it also shows me another version of these shared folders which have a $ appended to it. eg my C: drive is shared. In ubuntu I see two version one just "C" which is what I named the share and "C$". If I click C$ it asks me for a username and password with DOMAIN: WORKGROUP. What username and password is this? I tried my windows username and password with no luck. Could I use this method rather? Is this what you meant in the second part of your reply when you started mentioning passwords on the share?

2. How will this work if my network connection is only established once I have logged in as I am using wireless?

---

### Post by Paqman on 2009-03-11
> **funkyali said:**
> 
2. How will this work if my network connection is only established once I have logged in as I am using wireless?

It'll work fine. Once your connection comes up, your shares will be mounted.

The only time this won't happen is if you turn on the PC containing the shares *after* your other PC. In that case you can tell your machine to go find the shares and mount them with the command:
```

sudo mount -a

```
I have that command in a little script on my desktop, because I like to click on things :)

---

### Post by tarps87 on 2009-03-11
> **funkyali said:**
> 1. At the moment I just go "places>network>lounge" (of course my windows pc is named lounge). When I click on lounge it should me the folders I share it also shows me another version of these shared folders which have a $ appended to it. eg my C: drive is shared. In ubuntu I see two version one just "C" which is what I named the share and "C$". If I click C$ it asks me for a username and password with DOMAIN: WORKGROUP. What username and password is this? I tried my windows username and password with no luck. Could I use this method rather? Is this what you meant in the second part of your reply when you started mentioning passwords on the share?

2. How will this work if my network connection is only established once I have logged in as I am using wireless?

On the windows machine you should be able to right click on the C: drive icon and then properties, click on the sharing tab and then select permissions, this should list all the users that have access to the share. I'm currently connecting to a Ubuntu server using samba so I am doing it the other way round but will test that this is correct when I get home.
You are correct, the second part of my reply was referring to storing you password so that you don't need to enter it each time

You network driver should be loaded during the boot sequence but I think it connects after you login, you may need to run```
mount -a
``` which should mount all the drives in the fstab file. If this works you can add it to the auto started/run programs. I only auto mount shares on the desktops (connected by wired cards) so I can not be sure how it work until I try it.
Edit: or Paqman tells me :)

---

### Post by funkyali on 2009-03-11
> **tarps87 said:**
> On the windows machine you should be able to right click on the C: drive icon and then properties, click on the sharing tab and then select permissions, this should list all the users that have access to the share.
I had a look and all it askes me is if I want to share this folder or not. it also askes me whether I want to allow network user to change my files. I did see this option when I right click on My computer and select properties>remote it then allowed me to select remote users.

---

### Post by tarps87 on 2009-03-11
> **funkyali said:**
> I had a look and all it askes me is if I want to share this folder or not. it also askes me whether I want to allow network user to change my files. I did see this option when I right click on My computer and select properties>remote it then allowed me to select remote users.

I forgot, first you need to go into control panel -> folder options and un-select "Use simple file sharing"

The remote options are for remote desktop

---

