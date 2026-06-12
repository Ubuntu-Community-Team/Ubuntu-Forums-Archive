---
title: "Can't access Samba directories."
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by grs on 2008-05-07
I have ClarkConnect setup as a storage server using Samba. When I go to my Windows Explorer on my Win XP machine I can access the server directories fine, it just asks for a password the first time. But when I try to access the server on my Ubuntu machine I can get to the server and it lists the directories. I don't get asked for a password so I can't access or see my Home directory (called grs). When I click on a directory the Shared directory it opens fine.
I have two other directories I setup with Samba and when I try to access them I get the following error message

Failed to mount Windows share

How do I access the directories, where do I login with my username and password?

---

### Post by grs on 2008-05-08
I've been told I can mount drives from my Samba server onto my Ubuntu machone by adding the following to /etc/fstab

//192.168.1.110/mnt/Films   /home/myname/Films   smbfs   defaults   0 0

I'm not sure about the 'defaults' bit the guide I was looking at had some reference to Mac passwords in there.

I made the changes anyway and rather than restart the PC I typed 'mount -a' but I got the following reply

mount: wrong fs type, bad option, bad superblock on //192.168.1.110/mnt/TV,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on //192.168.1.110/mnt/Films,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I also tried to change the 'smbfs' bit to 'ext3' (that is the Samba drive format) but I got this reply

mount: special device //192.168.1.110/mnt/TV does not exist
mount: special device //192.168.1.110/mnt/Films does not exist

Anyone got ideas?

---

### Post by zagevent on 2008-05-08
i had the same fault, then i found on this forum you need to do this in your terminal sudo aptitude install smbfs then it will work

---

### Post by grs on 2008-05-09
What exactly does the sudo aptitude install smbfs command do?

---

### Post by Iowan on 2008-05-09
**sudo** - run command as root user
**aptitude** - a package installer/manager
**install** - installs (as opposed to listing or removing)
**smbfs** - Samba's file system.

BTW, CIFS is replacing (or already has) SMBFS - dunno if there's a separate CIFS install, though.

---

### Post by grs on 2008-05-10
I got smbfs running, I've added the lines to fstab that I think are right and I restarted the machine but the drives are not mounting. Also when I run mount -a I got an error message that referred to something else in the file

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-rt/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=myname)

If anyone has done tried to mount a Samba server drive onto a Linux PC please tell me how you did it.

---

### Post by balagosa on 2008-05-10
> **grs said:**
> 

mount: special device //192.168.1.110/mnt/TV does not exist
mount: special device //192.168.1.110/mnt/Films does not exist



surely the folder "TV" & "Films" does not exitst on "//192.168.1.110/". you might want to check it first if it exists.


as for me...this is how i did it on my /etc/fstab:
//127.0.0.1/winshares  /media/winshares  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0

i folllowed this guide: [https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=(cifs)]("https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=(cifs)")

i also use "smb4k" to work hand-in-hand with Samba

---

### Post by grs on 2008-05-10
I didn't get any further. Did the changes, ran mount -a and got the same result as my last post, I tried several of the examples given in the guides.

Why do I need samba though, the files are stored on a Linux PC in a Linux format.

---

### Post by sges on 2008-05-10
This is a bug in gvfs (new in Gnome 2.22 replacing GnomeVFS in 2.20) I think it have been fixed but I cannot test it right now. At least my Gnome is now 2.22.1.  Update your Ubuntu. Over 50 update have come out since 8.04 was launched

---

### Post by bobd72 on 2008-05-10
I am using a fully updated Kubuntu box and am having the same problems.  Trying to set up boot access to a Windows machine just will not work.  I have tried every combination of fstab setup for cifs known to man or woman.  

The share is set up at boot but cannot be mounted - either at boot time or when the machine is running -even though smb4k can mount the same drive perfectly - just not at boot time.
When trying to mount the share it says Permissions denied - even though the drive can be mounted OK using smb:// and there is no password security applied to the windows drive - access to everyone - and guest is enabled.

I have been working on this for three days  -still no resolution.

---

### Post by grs on 2008-05-11
Because of this bug the current version Linux Ubuntu only has very limited access to network storage?
I that right?
How could they have released it if has such a bug?




Also I've been trying nfs from a guide I found at [http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)

I think I got the server end running when I wne to the client and run the mount option I got

sudo mount 192.168.1.110:/mnt/TV /mnt/TV
mount: wrong fs type, bad option, bad superblock on 192.168.1.110:/mnt/TV,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I'm not sure what to do from here.

---

### Post by bobd72 on 2008-05-11
I'm not sure if it's a "bug" or just a complex config issue yet.  It is certainly an issue that has been causing problems for a long time though - problems with this config on this forum go back years.

As for your mount command:

sudo mount 192.168.1.110:/mnt/TV /mnt/TV

I don't know why the colon is there? You also haven't specified the file system

Try some thing like:

sudo mount -t nfs 192.168.1.110/mnt/TV /mnt/TV

Have a look at man mount for more options

---

### Post by grs on 2008-05-11
> **bobd72 said:**
> I'm not sure if it's a "bug" or just a complex config issue yet.  It is certainly an issue that has been causing problems for a long time though - problems with this config on this forum go back years.

As for your mount command:

sudo mount 192.168.1.110:/mnt/TV /mnt/TV

I don't know why the colon is there? You also haven't specified the file system

Try some thing like:

sudo mount -t nfs 192.168.1.110/mnt/TV /mnt/TV

Have a look at man mount for more options

I tried a few more variations and just come up with the same results. Do you have a network storage setup through Linux? If so, can you give me a guide on how you did it?

---

### Post by sges on 2008-05-11
I was in error. The problem has not been fixed in ubuntu updates. Currently the only solution in to rebuild gvfs from the SVN

See David horns final post in [https://answers.launchpad.net/ubuntu/+source/nautilus/+question/31217](https://answers.launchpad.net/ubuntu/+source/nautilus/+question/31217)

---

### Post by sges on 2008-05-11
> **sges said:**
> I was in error. The problem has not been fixed in ubuntu updates. Currently the only solution in to rebuild gvfs from the SVN

See David horns final post in [https://answers.launchpad.net/ubuntu/+source/nautilus/+question/31217](https://answers.launchpad.net/ubuntu/+source/nautilus/+question/31217)

Applying unofficial Patches and recompiling source code is done at your own risk. If you are unfamiliar with using diff files, C code and compiling source code I would wait.

---

### Post by sges on 2008-05-11
There has been a suggestion to Use GNOME Commander (Available under Applications | Add/remove) as a workaround.

---

### Post by grs on 2008-05-11
I think I'll give the code compiling etc.. a miss and wait till the problem is fixed by someone who knows what their doing!

I was just thinking of a way around the problem. My CC server uses Flexshare, which Linux is able to see and access. When you create a share on CC through the webgui it automatically points towards a folder named after the share on the same HDD as the OS. If I then go to /etc/samb/flexshare.conf I should be able to change the path to point at the TV and Films folders instead.

I'll give it a go later and let you know how I got.

GNOME Commander doesn't seem to allow access either, it's just a file browser unless I'm missing what I'm supposed to do with it.

---

### Post by grs on 2008-05-11
That Flexshare idea didn't work.

---

### Post by bobd72 on 2008-05-11
> **grs said:**
> I tried a few more variations and just come up with the same results. Do you have a network storage setup through Linux? If so, can you give me a guide on how you did it?

No - sorry I can't help you there

---

### Post by dmizer on 2008-05-11
if your nas device serves nfs, have a look at the nfs server/client howto in my sig.

no garantees about making it work with samba, but you can also try the "mounting windows/samba shares with CIFS" howto in my sig.

---

### Post by grs on 2008-05-12
I've run into a problem with the guide, when I try to install nfs-kernel-server I get an error message saying it can't find the package. How do I get this package?

sudo dpkg-reconfigure portmap

Won't run, it doesn't know dpkg-reconfigure but I can use the restart command.

---

### Post by dmizer on 2008-05-12
probably just need to enable the multiverse and universe repositories:
[https://help.ubuntu.com/community/Repositories/Ubuntu?#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu?#head-5bbef89639d9a7d93fe38f6356dc17847d373096)

also, if you only want to connect to nfs shares, you don't need to follow the "server" section of the howto.  you only need the server section if you want to allow other computers to connect (via nfs) to your ubuntu computer.

if you only want to connect to your nas via nfs, just follow the section labeled "Install NFS client support" in the howto.

---

### Post by grs on 2008-05-12
> **dmizer said:**
> probably just need to enable the multiverse and universe repositories:
[https://help.ubuntu.com/community/Repositories/Ubuntu?#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu?#head-5bbef89639d9a7d93fe38f6356dc17847d373096)

also, if you only want to connect to nfs shares, you don't need to follow the "server" section of the howto.  you only need the server section if you want to allow other computers to connect (via nfs) to your ubuntu computer.

if you only want to connect to your nas via nfs, just follow the section labeled "Install NFS client support" in the howto.

I have the client end setup according to the guide, its the server end (ClarkConnect) that I can't get sudo dpkg-reconfigure portmap working on.
And this link [https://help.ubuntu.com/community/Repositories/Ubuntu?#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu?#head-5bbef89639d9a7d93fe38f6356dc17847d373096) only tells my how to setup multiverse and universe through the gui - even that is different though to my Ubuntu, there is no Software Properties under Admin.

---

### Post by dmizer on 2008-05-12
> **grs said:**
> I have the client end setup according to the guide, its the server end (ClarkConnect) that I can't get sudo dpkg-reconfigure portmap working on.
And this link [https://help.ubuntu.com/community/Repositories/Ubuntu?#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu?#head-5bbef89639d9a7d93fe38f6356dc17847d373096) only tells my how to setup multiverse and universe through the gui - even that is different though to my Ubuntu, there is no Software Properties under Admin.

okay ... this forum does not support your clarkconnect nas device.  to set up your clarkconnect nas for nfs, you should look for help here: [http://www.clarkconnect.com/forums/ubbthreads.php](http://www.clarkconnect.com/forums/ubbthreads.php)

if your clarkconnect device is running ubuntu, then all you have to do is uncomment (remove the pound [#] sign) the multiverse and universe lines in the /etc/apt/sources.list file.

```
sudo nano /etc/apt/sources.list
```

---

### Post by grs on 2008-05-12
I had posted there before trying to get it working, I have some more info this time so I might get a bit further. Thanks

---

