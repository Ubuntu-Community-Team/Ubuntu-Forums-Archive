---
title: "Netgear Sc101 San Disks"
date: 2005-11-08
forum: Networking &amp; Wireless
---

### Post by cherrytree on 2005-11-08
I have just used the live cd version of Ubuntu and I have to say it’s great. It saw all my hardware and I was able to set up my network printers and everything with no problems. The only problem I have is I use a Netgear sc101 for off line storage and backup. Ubuntu won't see it. It works using an ip address given out by my router though DHCP but even Windows needs a special driver before it will see it. Has anyone got any idea how I can get it to connect. Netgear won't answer any of my emails so they don't know...
 I also would like to use MS Access 2003, has anyone got any experience with using this though WINE.

---

### Post by mips on 2005-11-08
It does not look like there is any linux drivers for this device. I did read somewhere that there might be future Mac & Linux drivers from netgear though.

---

### Post by cherrytree on 2005-11-10
Yer i have spoken to Netgear... It took them two weeks. They said they don't support Mac for Linux. They may do in the future but not yet.

---

### Post by redo109 on 2006-11-06
I've got one of these to have you had any success mapping this drive
Richard

---

### Post by rfdparker2002 on 2007-01-02
Well I don't have this device, but I am looking to buy a networked HD/HD Caddy sometime in the future, and saw this one, and have been looking to see if it supports linux, I did find this post on google: [http://www.linuxforums.org/forum/354746-post2.html](http://www.linuxforums.org/forum/354746-post2.html) where someone says they've got it working just using samba and smb4k, but don't know what distro they were using. Also that seems strange as it's been said not to work on standards SMB as its SAN, as you (people on this thread) have been saying.

    On a similar topic, does anybody know of a network HD/networked HD Caddy that will with [K]Ubuntu well, can't you get native ext2/3 ones and isn't there a native linux networked HD thing called NFS or something?

---

### Post by FerGeCo on 2007-03-15
> **rfdparker2002 said:**
> Well I don't have this device, but I am looking to buy a networked HD/HD Caddy sometime in the future, and saw this one, and have been looking to see if it supports linux, I did find this post on google: [http://www.linuxforums.org/forum/354746-post2.html](http://www.linuxforums.org/forum/354746-post2.html) where someone says they've got it working just using samba and smb4k, but don't know what distro they were using. Also that seems strange as it's been said not to work on standards SMB as its SAN, as you (people on this thread) have been saying.


Well .. the user, in the thread you read, mounted the SAN drive in windows and then shared it (via windows). So you're mapping a M$ windows share instead of the SAN-drive ..

I guess that would work but you would still need a windows host to mount the SAN-drive.

I just bought and configured the SC101 .. really nice .. but too bad it doesn't have any linux software/drivers :S

---

### Post by netztier on 2007-03-15
> **rfdparker2002 said:**
> Also that seems strange as it's been said not to work on standards SMB as its SAN, as you (people on this thread) have been saying.

Well.. SAN most commonly refers to FibreChannel, and this is basically "SCSI over a fibre-optical network". The SAN-enabled computer gets one or better two HBAs (HostBus Adapter). To the computer, these loo very much like SCSI adapters. The two HBAs are connected to two completely independent (but symmetrical) FibreChannel networks, with switches routers and fibre optic cables interconnecting them. 

Somewhere else in that network, you'll find a storage unit that also has two HBAs - and a some racks full of harddisks connected to it. The SAN admininistrator then configures which and how many (virtual) disks are made visible to each computer connected to the SAN. 

I consider it a bold move by Netgear calling their SC101 unit a "SAN" device. If at all, it's akin to iSCSI (which is similar to FC, but uses IP and Ethernet to transport SCSI instead of FC HBAs and FC-switches); It's nothing more but a "remote disk". And proprietary drivers just s*&/()=!

> 
    On a similar topic, does anybody know of a network HD/networked HD Caddy that will with [K]Ubuntu well, can't you get native ext2/3 ones and isn't there a native linux networked HD thing called NFS or something?

Have you looked at the **Linksys NSLU2**? It's Linux-based, has USB-2 ports and configures ext3 on it's external drives per default (as far as I can remember). Since it runs Linux, there's alternative firmwares for it, and you can use it for plenty of things - including NFS.


best regards

Marc

---

### Post by CyBuzz on 2007-03-19
I wish I had the resources and knowledge to code a driver myself.  I just don't.  This is the only thing that is holding a windows computer on my network.  I have a windows box that all I use for is to export the shares that access these drives.  I guess I got suckered into a cheap way to attach storage to my network that I could put in my gun safe.

I dont really want to have to look at another solution, but the discussion of writing drivers for this has been floating around the net for a couple of years now with no progress.:(

---

### Post by rfdparker2002 on 2007-03-20
> **netztier said:**
> 
Have you looked at the **Linksys NSLU2**? It's Linux-based, has USB-2 ports and configures ext3 on it's external drives per default (as far as I can remember). Since it runs Linux, there's alternative firmwares for it, and you can use it for plenty of things - including NFS.


Thanks for the the advice this is exactly the thing I was looking for.

---

### Post by CyBuzz on 2007-03-20
> **netztier said:**
> 
Have you looked at the **Linksys NSLU2**? It's Linux-based, has USB-2 ports and configures ext3 on it's external drives per default (as far as I can remember). Since it runs Linux, there's alternative firmwares for it, and you can use it for plenty of things - including NFS.


I have looked into this.  In hindsight, I probably would have gone with it.  The things that make me not go with it is that it requires that you purchase external enclosures or drives that are already external.  My setup sits in my gun safe, where I am limited on room (I would rather take up the room with what is supposed to be in there) so I went with the SC-101.  Now I am stuck with the 101.

:lolflag: Does anyone need an SC-101?  Selling it cheap!:lolflag:

---

### Post by DraK on 2007-10-07
Have a look here, it seems promising..

[http://code.google.com/p/sc101-nbd/](http://code.google.com/p/sc101-nbd/)

---

### Post by DraK on 2007-10-12
Can someone tell me if the mke2fs command will destroy data or partitions already on the drive?

---

### Post by Nelse on 2007-10-25
I have one and after fooling with it for sometime, I wish I had waited and gotten something better.  Anyway, I also have a NSLU2, which I uslung and then deleted the new directory that It created on a flash drive., but that's another story.  I thought it was toast and bought the SC101.  

I also have a Windows XP virtual machine running.  I share the drives from the VM machine and then they appear in Samba.  I could not get this to work while using Gnome.  I switched to KDE and everything started to work.

Funny thing is that NSLU2, even though it's messed up, it still works. It will not accept any changes, IE IP address, but it still works.  It's even visible to Samba.

Nelse

---

### Post by ikn on 2008-01-10
I find this driver in [http://code.google.com/p/sc101-nbd/](http://code.google.com/p/sc101-nbd/)

---

### Post by Zack McCool on 2008-01-17
> **DraK said:**
> Have a look here, it seems promising..

[http://code.google.com/p/sc101-nbd/](http://code.google.com/p/sc101-nbd/)

> **DraK said:**
> Can someone tell me if the mke2fs command will destroy data or partitions already on the drive?

I am using an sc101 with a 250GB EIDE drive using the sc101-nbd driver above.  It works well.  The only downside is that it does require you to have a Windows box available to run the utility to create the partition.

And yes, mke2fs will destroy any data on the drive.  It makes the ext2 filesystem.

Basically, you install the utility on a Windows machine, let it do any firmware updates, then create the partition for linux, but do not attach to it with the Windows machine (or detach it).

Then, go to the linux machine and install the nbd driver (I used the tarball, as I am running Gutsy AMD64 and there was no package available:  make all, checkinstall).

From a command prompt,

```

sudo ut listall     <- lists the available partitions
sudo modprobe nbd     <- Inserts the driver module
sudo ut attach [id] /dev/nbd0     <- Attaches the partition to /dev/nbd0 [id] is from the list
sudo mke2fs /dev/nbd0     <- formats the partition as ext2
sudo mount /mnt/mountpoint /dev/nbd0     <- Mounts the partition for use

```

The author says that this is not shareable between windows and linux, and I haven't tried, but I am guessing that it would work if you installed the ext2 driver for windows...

---

### Post by tan-vinh on 2008-03-08
Thank you very much for the hints. I looked at the maintaining howto and didn't get a clue how to do that. You've saved my weekend. I will never buy a netgear product again. I expected it to run with linux, cause it isn't  an outstanding system in the world.

Unfortunately I could transfer files only as root-user.

My fstab entry:
```

# storage
/dev/nbd0 /mnt/sc101 ext2 user,auto,rw,owner 0 0

```

I mounted the device as normal user, but I can't copy any file to the mounted device. Does anybody know how to achieve this as normal user?

ta

EDIT: I solved this problem. Directory owner was wrong.

---

### Post by magicfab on 2008-06-13
Works fine with Ubuntu Hardy too.

I have two 250GB disks in it, still experimenting different setups.

I formatted the disks to ext3 before using the Windows utility. I also disabled drive sleeping completely.

---

### Post by SonicSteve on 2008-06-21
Hi Fab,
How did you disable drive sleeping? I find that this is the only problem I've come across so far. Sometimes I have to reboot and reconnect the SC101 because it just doesn't want to wake up.

---

### Post by SonicSteve on 2008-06-21
> **Zack McCool said:**
>  
The author says that this is not shareable between windows and linux, and I haven't tried, but I am guessing that it would work if you installed the ext2 driver for windows...

This is true, you can't use the device between windows and linux simultaneously. However you can use filesharing to make it available as a share from the computer you connected it to. I have 3 computers (2 linux, 1 XP) I connect to it with my Ubuntu Gutsy machine and share the mounted folder. It ends up being far easier and less administration.

---

