---
title: "The visible and working mounted drive that does not exist!"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by PiggiePaul on 2008-02-20
Perhaps someone can explain this?

On the Ubuntu Menu's I went to the PLACES menu and ran the CONNECT TO SERVER program.

I put in the name of my remote PC (on my network) and my username and the folder, I wanted to see, and (as if by magic) I got a lovely mounted drive folder on my desktop.

If I double click it, It gives me the correct view of all the files on the remote PC's folder.

If I right click it, I can select "Unmount" which I have not done.

It is still on my desktop after a reboot (which is superb)

But, according to my file system Browsing and Searching everywhere, this shared (mounted) drive/folder icon on my desktop does no exist anywhere.....:confused:

anyone know what's going on?

---

### Post by amohanty on 2008-02-20
You can do a 
mount -l 
in a terminal to see where it is mounted.

HTH
AM

---

### Post by PiggiePaul on 2008-02-20
> **amohanty said:**
> You can do a 
mount -l 
in a terminal to see where it is mounted.

HTH
AM

Thanks, did that, but to be honest, it's not apparent it's actually there.

/dev/hda2 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096) []
securityfs on /sys/kernel/security type securityfs (rw)


There is one other mounted drive icon on my desktop and that's "hda1" which is the 1st partition on my hard drive.

This other one looks like a folder, with the network graphic on the bottom.

---

### Post by amohanty on 2008-02-20
Sorry my bad. Mixed up the replies.

Its possible that the remote 'mount; is completely managed by gnome-vfs and it will not have a mount point.

In that scenario you really dont have mounted folder to search in. You could use samba (assuming it is a PC share) and use smbmount (sudo apt-get install smbfs) to mount it on a local mount point and then use it as a regular folder.

HTH
AM

---

### Post by PiggiePaul on 2008-02-20
> **amohanty said:**
> Sorry my bad. Mixed up the replies.

Its possible that the remote 'mount; is completely managed by gnome-vfs and it will not have a mount point.

In that scenario you really dont have mounted folder to search in. You could use samba (assuming it is a PC share) and use smbmount (sudo apt-get install smbfs) to mount it on a local mount point and then use it as a regular folder.

HTH
AM

Ah, I see, yeah, you're probably right there.
I did a full search of the system with the search tool and did not fine the folder name.

So back to your other option (yes it is a PC share)


You suggest the following command:
[COLOR="Blue"]sudo apt-get install smbfs[/COLOR]


Someone else (in another similar question of mine, suggested:
[COLOR="Blue"]sudo aptitude install smbfs[/COLOR]

When I typed this other guys command above, I got the following text in the terminal:


[COLOR="Blue"]
[sudo] password for USERNAME:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
kcontrol kdebase-data kfind kicker
The following NEW packages will be installed:
smbfs
0 packages upgraded, 1 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B/485kB of archives. After unpacking 32.1MB will be freed.
Do you want to continue? [Y/n/?] [/COLOR]


I said NO by the way, just in case!

---

### Post by amohanty on 2008-02-20
apt-get is simply a sort of 'backend' for all apt using tools. They both do the same thing and will prompt you in the same manner. If you want to install smbfs, you can use either or synaptic which is the gui frontend.

HTH
AM

---

### Post by PiggiePaul on 2008-02-20
> **amohanty said:**
> apt-get is simply a sort of 'backend' for all apt using tools. They both do the same thing and will prompt you in the same manner. If you want to install smbfs, you can use either or synaptic which is the gui frontend.

HTH
AM

Ok, sorry if I'm being a bit dim, but to clarify:

apt-get and aptitude are the same thing and end up with the same result?

If I want to mount any drives/folders from my PC and have them pretend to be drives/volumes in Linux then I must install smbfs?

You kinda lost me on the way you explained the last bit about synaptic?

Oh hang on, did you mean, to install smbfs on my system I can use either of those command line versions or use the synaptic package manager to install smbfs instead?

either way, if I don't I'm never going to be able to mount remote drives?

---

### Post by amohanty on 2008-02-20
> Oh hang on, did you mean, to install smbfs on my system I can use either of those command line versions or use the synaptic package manager to install smbfs instead?


Exactly.

No you can always mount remote drives. Only if they are windows servers or windows machines you need samba and smbfs to mount the drives to a local mount point.

AM

---

### Post by discorsage on 2008-04-03
I think I may have a similar issue - 

I have a drive which is mounted, I know because I can see the files and interact with them.

However, the drive does not show up in /dev, or with the mount command.  Is there a way to check if gnome-vfs is handling this?

This drive is a backup drive and it is mounted on my server as /mnt/Backups

Another oddity - I have a rsync job running that backups to this drive nightly, and it has been failing, which my job email says is due to it being read-only, however, when I go into the folder myself, I can modify files and delete them just fine.

---

