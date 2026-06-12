---
title: "Moveing the /home folders to another drive shared with Win7"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by akira2501 on 2010-07-29
Hello!  I'm pretty new to Linux and I've got a question I'm hoping that I can get some help on.
 I've got a small SSD drive that I have Ubuntu 10.04 and Windows 7 loaded on.  Then I have a separate hard drive for my data.
 

 In Windows, I've redirected &#8220;My Documents&#8221; and other such folders to the data drive which is formated with NTFS.   I'm trying to do the same with Ubuntu and move the folders in the /home directory to the **SAME** folders that Windows is using so that I can share the same data pool.
 

 In my search I found a old answer that gave me the command nano ~/.config/user-dirs.dirs
 Now command lines are all Greek to me, but I followed the instructions and edited the file to:
 from:
 XDG_DOCUMENTS_DIR=&#8221;$HOME/Documents&#8221; 
 to  
 XDG_DOCUMENTS_DIR=&#8221;/media/*drivename*/docs&#8221;
 

 I save and exit, but the Documents folder under places has not redirected.
 What did I do wrong?

---

### Post by S.R on 2010-07-29
Might be wrong but I think your /home folder has to be on an ext2, 3, or 4 partition not an NTFS

---

### Post by chrisinspace on 2010-07-29
> **S.R said:**
> Might be wrong but I think your /home folder has to be on an ext2, 3, or 4 partition not an NTFS

I'm not sure if you can mount /home on NTFS, but what I did was put /home on its own partition and then access it in Windows using [Ext2 IFS]("http://www.fs-driver.org/").  It's called "Ext2 IFS", but it works with EXT3, too.

---

### Post by akira2501 on 2010-07-29
> **chrisinspace said:**
> I'm not sure if you can mount /home on NTFS, but what I did was put /home on its own partition and then access it in Windows using [Ext2 IFS]("http://www.fs-driver.org/").  It's called "Ext2 IFS", but it works with EXT3, too.

Ok, thanks. So even though Ubuntu can read, write, and mount NTFS volumes I cannot redirect the default save locations to NTFS?

Seems odd, but I'll give Ext2 IFS a try.  Even if it doesn't work out for what I'm trying to do it's still looks like a useful application. Thanks.

---

### Post by akira2501 on 2010-07-30
There must be something else I'm doing wrong.
 I re-formated the partition to EXT3 and changed the data path in “user-dirs” to:
 XDG_DOCUMENTS_DIR=“/media/data/docs”
 

 “data” represents the drive name.  
 But its still not moving the reference “documents” reference under “places” to the data drive.
 Any suggestions?

---

### Post by oldfred on 2010-07-30
Linux partitions have permissions and ownership that windows NTFS & FAT do not suppport. Part of why linux is more secure. So you cannot share /home with a NTFS partition.

I use data linking or directly mounting partitions into /home. You have to create a mount point & mount the partition to that mount point. To permanently mount it add it to fstab.

I suggest a shared NTFS partition for data. I used that for almost 4 years with my XP install and have firefox & thunderbird profiles in it to share all data which ever I boot. I directly mount my shared partition into /home. But I will change that to a link when I totally convert from Karmic to Lucid. I now have most of my data in /data an ext3 partition that has all the standard folders in /home for data and then link the folders into /home.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
Link XP my docs
[http://www.techsupportalert.com/how_to_move_my_documents.htm](http://www.techsupportalert.com/how_to_move_my_documents.htm)

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

### Post by akira2501 on 2010-07-30
Hi Oldfred - I'm in the Chicago burbs too - small world!
 
I've been reading these links and I think I'm doing this right now, except for perhaps the routing of the default folders themselves.  For example I dont know if this mount point is correct:
XDG_DOCUMENTS_DIR=&#8220;/media/data/docs&#8221;

Is there any way to display the exact mount point of a folder on the system?

---

### Post by akira2501 on 2010-07-30
Also the EXT2 mounter does not work with Windows 7.

Any other suggestions.  Please!

---

### Post by oldsoundguy on 2010-07-30
Just an FYI .. I save my ~/home folder with all the contents to a thumb (usb) drive.  The folder itself is not that large.

IF you are concerned with data you have accumulated such as photos and your office work and so on, those I keep on a SEPARATE internal drive.  Not that much of a task on a desktop to put in another drive and it has saved my bacon far more than once.
In today's day and age you can also use an external USB hard drive for the storage for either a desktop or a laptop.  NOT that expensive when you consider that it is an insurance policy to cover the hours of work you have tied up!

---

### Post by oldfred on 2010-07-30
Your /media looks like a standard automount by Nautilus or did you intentionally use that?

It is better to use other mounts for those you assign. I direct mount into /home but I do get double mounts in the left pane of Nautilus. That is why now I mount to a hidden folder in root and change permissions to me. Then I link those folders to /home to replace the folders. If your fold is NTFS the mount is critical for default permissions as they cannot be changed.

mkdir /home/fred/shared
sudo blkid
gksudo gedit /etc/fstab

# Entry for /dev/sda2 :
UUID=2A87EC53669130A9                      /home/fred/shared  ntfs-3g      defaults                             0  0  

sudo mount -a

ln -s /usr/local/fred/shared

For my ext3 data partition I mount

sudo mkdir /usr/local/fred
sudo mkdir /usr/local/fred/data
sudo chown -R fred:fred /usr/local/fred
sudo chmod -R 766 /usr/local/fred/data

fstab entry:
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2 

mv Documents oldDocuments
ln -s /usr/local/fred/data/Documents

---

### Post by mapes12 on 2010-07-30
Hi akira2501

It looks like you have lots of useful guidance in this thread but I thought I would throw in something that was useful for me. A while back I did a standard install on my laptop but then I discovered that having /home in a separate location would be much easier to manage system upgrades and the like. I followed this How To to move it:-

[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

It worked perfectly.

Mark

---

### Post by akira2501 on 2010-07-30
> **oldfred said:**
> Your /media looks like a standard automount by Nautilus or did you intentionally use that?

It is better to use other mounts for those you assign. I direct mount into /home but I do get double mounts in the left pane of Nautilus. That is why now I mount to a hidden folder in root and change permissions to me. Then I link those folders to /home to replace the folders. If your fold is NTFS the mount is critical for default permissions as they cannot be changed.

mkdir /home/fred/shared
sudo blkid
gksudo gedit /etc/fstab

# Entry for /dev/sda2 :
UUID=2A87EC53669130A9                      /home/fred/shared  ntfs-3g      defaults                             0  0  

sudo mount -a

ln -s /usr/local/fred/shared

For my ext3 data partition I mount

sudo mkdir /usr/local/fred
sudo mkdir /usr/local/fred/data
sudo chown -R fred:fred /usr/local/fred
sudo chmod -R 766 /usr/local/fred/data

fstab entry:
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2 

mv Documents oldDocuments
ln -s /usr/local/fred/data/Documents

Ok, this is a total noob question, but how do I know what the mount point for a drive is exactly?  Assuming that it is already auto-mounted by the OS on boot?

---

### Post by oldfred on 2010-07-30
You can see all the mounts
```

mount -l
```

I did not know how to list all mounts, I use blkid or fstab normally. But man mount showed above code.

---

### Post by akira2501 on 2010-07-30
> **mapes12 said:**
> Hi akira2501

It looks like you have lots of useful guidance in this thread but I thought I would throw in something that was useful for me. A while back I did a standard install on my laptop but then I discovered that having /home in a separate location would be much easier to manage system upgrades and the like. I followed this How To to move it:-

[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

It worked perfectly.

Mark


Hi Mark, followed the instructions and moved my /home.  Its working fine in Linux.  The only problem I have now is that Windows 7 cannot see it because of the EXT3 formating.  EXT2 IFS doesn't work on Win7.  Any suggestions or perhaps I should re-post this question with a diffrent heading that more accuratly represents the new situation?

---

### Post by chrisinspace on 2010-08-02
> **akira2501 said:**
> Hi Mark, followed the instructions and moved my /home.  Its working fine in Linux.  The only problem I have now is that Windows 7 cannot see it because of the EXT3 formating.  EXT2 IFS doesn't work on Win7.  Any suggestions or perhaps I should re-post this question with a diffrent heading that more accuratly represents the new situation?

Ext2 IFS works for me in Windows 7.  There was an issue with the disk formatting, but I was able to fix it.

From [another forum]("http://www.networkedmediatank.com/showthread.php?tid=23220"):

"Your drive has to be formatted with an inode size of 128 in order to be readable on windows 7 using Ext2IFS. If your drive has an inode size of 256 bytes Ext2IFS will not be able to mount the drive and windows will constantly keep asking you if you want to format your drive. This can be done by re-formatting [using a linux live cd] the 3rd partition on your drive using the ext2 format with journaling enablde and an inode size specified as 128 bytes. [example: mkfs.ext2 -j -i 128 /dev/sdb3]".  **Warning**: this method requires you to wipe the NTFS partition, so back up your data to another drive/partition first.

Also, here is another [Ubuntu Forums thread on the topic]("http://ubuntuforums.org/showthread.php?t=979523").  They mention solutions and alternate projects.  You might also look at [Ext2Fsd]("http://www.ext2fsd.com/").  I haven't tried it, but I know it's another popular solution.

---

### Post by mapes12 on 2010-08-02
> Hi Mark, followed the instructions and moved my /home. Its working fine in Linux. The only problem I have now is that Windows 7 cannot see it because of the EXT3 formating.I think you will find that the ext3 formatting issue is a red herring.

I work from the perspective that my Ubu box is my main client and everything else on my home network is accessable from Ubu. Within my LAN the main work needs to be done on the windoze box. I only have XP. Now that Ubu is my main working environment I haven't the need to buy any more MS licences.

In XP, the folder(s) I want Ubu to have access to, I right click and enable file sharing. Then in Ubu I go Places>Network>MS Home (the name of my MS workgroup)>My Documents (the shared folder) and I can transfer stuff between the 2 boxes. Just done it with over 8GB of video files I want on my Ubu box.

No need for Samba or anything else that could make life difficult. Just simple file sharing between the 2 boxes.

My Ubu machine is formatted with ext3 and my XP box with NTFS.

Mark

---

