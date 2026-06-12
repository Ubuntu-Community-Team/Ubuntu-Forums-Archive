---
title: "how to access network disk (seagate) thru router (d-link) with ubuntu 14.04"
date: 2017-07-19
forum: Networking &amp; Wireless
---

### Post by uinwin on 2017-07-19
I've searched for the last three days and can't figure out what to do...

I have a seagate 1TB network drive connected to a d-link router.  I want to access this disc from my Gateway P170 laptop, recently converted to ubuntu 14.04 and to a solid state drive.

From this thread I get that I probably need to edit fstab to include the ip address of the network drive and my user ID:

[URL="https://ubuntuforums.org/showthread.php?t=1778060"]https://ubuntuforums.org/showthread.php?t=1778060
[/URL]

I'm baffled by the reference in that thread to "openshare".  I don't know what it is and can't tell if it's relevant to my goal.  If I'm right about editing fstab, I need to know exactly what to add to it so my laptop can "see" the network drive.

Also, assuming I need to edit fstab, is the text editor available from the gui suitable or do I need to learn how to use ed?

Me: 30+ years ago I worked for Sun and used unix command line windows a lot.  That was then.  This is now.  I'm old(er) and have forgotten most of what I knew back then.   So speak slowly and simply in monosyllabic words, please.

Thanks in advance,
Jim

---

### Post by slickymaster on 2017-07-19
Thread moved to **Networking & Wireless** for a better fit

---

### Post by Tadaen_Sylvermane on 2017-07-19
If it's a usb drive plugged into a router you have to set it up to be shared. Normally they use samba. Once it's shared then you can browse to it I'd imagine. If it's a ethernet "nas" drive then you should be able to go into it''s web ui and set it up from there. After it's properly set and shared then you can add it to your /etc/fstab.

---

### Post by uinwin on 2017-07-21
> **Tadaen_Sylvermane said:**
>  If it's a ethernet "nas" drive then you should be able to go into it''s web ui and set it up from there. 

This worked and I appreciate the suggestion.   It raises a new question, though:  How do I discover the IP address of the network disk using Ubuntu?  I used my other PC running Windoze to get the IP address and had I not had that PC, I don't know how I would have discovered it using Linux.  Any hints?

> 
After it's properly set and shared then you can add it to your /etc/fstab.

OK, now you've confused me (not hard to do).   

1. If I can reliably get to my network discs using firefox and logging in, why do I need to fiddle with /etc/fstab?  What is the benefit?

2. If I still need to edit /etc/fstab, then this circles back to my original question.... what should the /etc/fstab entry look like?  

Again, thanks for the help.

Jim

---

### Post by vocx on 2017-07-21
> **uinwin said:**
> This worked and I appreciate the suggestion.   It raises a new question, though:  How do I discover the IP address of the network disk using Ubuntu?  I used my other PC running Windoze to get the IP address and had I not had that PC, I don't know how I would have discovered it using Linux.  Any hints?

Well, if you are in control of your network, that is, if you control the router, then typically you can access the web interface of the router and find the IP address of all the devices in this local network. Many devices also come with a predefined IP address, so when you reset the router, or hard drive in this case, you can access it with that factory default IP address.

Ubuntu comes with Avahi, which is a system to find and resolve the names of network devices in a local network. If the NAS drive has a name, probably you can find it by running "avahi-discover" from your terminal.

> 
OK, now you've confused me (not hard to do).   

1. If I can reliably get to my network discs using firefox and logging in, why do I need to fiddle with /etc/fstab?  What is the benefit?

2. If I still need to edit /etc/fstab, then this circles back to my original question.... what should the /etc/fstab entry look like?  

Again, thanks for the help.

Jim
You do not need to fiddle with "/etc/fstab" if you don't want to. It's at your discretion. The "/etc/fstab" is typically used to mount partitions as if they were a local directory in your computer, that is, as if they were permanent or fixed in your system. If you have a USB drive, and you plan to move it a lot, disconnect it, and reconnect it many times, there is no need to to alter "/etc/fstab". But if you get a hard drive for a desktop PC, probably you will connect it once and leave it inside the case for years. So, in this case, editing the "/etc/fstab" is good, to mount it permanently as part of your system. So, what do you plan to do with your NAS drive? Do you intend it to move a lot, or do you plan on leaving it fixed in the same spot for years. This should tell you whether you add it or not to "/etc/fstab".

The drive you describe may provide both the web interface and the possibility of mounting it permanently through "/etc/fstab". The thing is there is usually more than one way to do things that ultimately are equivalent, and this depends on the specific device. For example, there are security cameras which connect to a computer through USB. Others connect through an Ethernet cable. Others connect using a coaxial cable, etc. The result is the same, the camera records video or images, and transmits the information to your computer, but the specific way may be different. So the same is true for your hard drive, there may be two or three ways to access the data, which is best depends on your usage of the disk.

In the case of the NAS disk, if you are able to access it through the web interface that means it is running a server that you can access through its IP address. If you want to mount it as part of your system, these network drives typically "share" a folder, so this folder has to be identified in the documentation of your hard drive.

In the thread that you linked [https://ubuntuforums.org/showthread.php?t=1778060](https://ubuntuforums.org/showthread.php?t=1778060) the IP address of the network device is 192.168.1.102, and directory shared was "openshare". Therefore, the remote disk is "192.168.1.102/openshare", which is mounted in the local system as "/media/openshare". That is, "openshare" is nothing special, it's just the name of the directory.

You can open your own "/etc/fstab" and see the entries there to try to understand how the entries should be. It is not too complicated. If you check the previous thread it has:
```

192.168.1.102/openshare   /media/openshare   cifs    uid=1000    0   0

```
There is one line per drive, with the options separated by whitespace. The first value is the name of the partition or shared directory, the second is the name of the directory in your local system where you wish to mount it, the third is the type of file system; this could be a native Linux file system, such as "ext4", "nfs", "resiserfs", etc.; for Windows partitions this could be "vfat", or "ntfs"; in the example, it is using the "cifs" file system, which means a remote drive shared with SMB protocol, which is a method for sharing drives. The fourth value is comprised of additional options for mounting, in that case "uid=1000"; this sets the permissions to the owner of the drive as the user with id 1000, which is normally your main user; if you don't set the ownership of the mount, you might see the drive, but you might not be able to edit, add, delete, or operate on the files. The last two values, "0" and another "0", are remnants from the past, and don't actually do much today. Just leave them there.

You can read more about it in [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

So, for your specific case, you need to know what folder is being shared by your disk, and use that in the "/etc/fstab" file. Check the documentation or web interface of the drive. If the drive has a name, or it allows you to set one, you may actually access it by that name, instead of IP address. That is, if you use the name you don't have to worry about the IP address changing, and the fstab entry will always remain valid.

In Windows documentation the device and share are commonly stated as "\\DEVICE\share". The process of mounting disks in Windows is typically called "mapping a drive", which assigns a drive letter, such as "X:", "Y:", "Z:", etc. In Linux the equivalent would be to add a line to "/etc/fstab"; the mount point could be any directory.
```

DEVICE/share   /media/mydrive   cifs    auto,umask=0022,uid=1000,gid=1000    0   0

```

Of course, you need to make sure the "/media/mydrive" directory actually exists first.

See this other thread explaining how to create the directory and add the appropriate permissions [https://ubuntuforums.org/showthread.php?t=2366697&p=13668208#post13668208](https://ubuntuforums.org/showthread.php?t=2366697&p=13668208#post13668208)

---

