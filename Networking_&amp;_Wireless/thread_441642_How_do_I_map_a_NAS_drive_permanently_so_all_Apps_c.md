---
title: "How do I map a NAS drive permanently so all Apps can use it"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by Shinobi326 on 2007-05-12
I keep browsing through the forums and I try out a few things but I can't seem to find solution that works for me.

I have a NAS drive (well actually 2 but if I just figure one out I'm sure I can do the other) that has all of my music, pictures, .ISO's, etc.  I figured out how to mount (map) it in Nautilus but it's only good in that app.  I need a permanent mount so all applications can use it.  I really need a step-by-step Barney Style approach because I can't seem to get this right.

the URL for the share in Nautilus is "smb://storage-0222/public"  How do I permanently mount this?

It still boggles the mind that something as simple as a permanent network share map (mount) is this difficult in Ubuntu / Linux while in the Windows world it's a 2 second task.

---

### Post by benanzo on 2007-05-12
You need to install smbfs/cifs and add it to your /etc/fstab to mount it permanently.

```
sudo apt-get install smbfs
```

```
sudo gedit /etc/fstab
```

create a directory to mount the share in (in the example /mnt/nas_disk):
```
sudo mkdir /mnt/nas_disk
```

add this line to /etc/fstab:
```
\\storage-0222\\public /mnt/nas_disk smbfs user,defaults 0 0
```

---

### Post by Shinobi326 on 2007-05-12
Cool...thanks for the steps! However, I'm not seeing anything show up in that new mount....  I have the "/mnt/nas_disk" folder there but it appears nothing is there.  I also did a reboot and it's the same thing.

Here is my current fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=1d577556-342e-41d1-bc12-8ed5d1111410 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=8bddecf9-d5f9-484b-869a-47e2db92f50f none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
# //storage-0222/PUBLIC /net smbfs 0 0
\\storage-0222\\public /mnt/nas_disk smbfs user,defaults 0 0
```

Is there something else I'm missing?

THANKS AGAIN!

P.S. I'm also in the Seattle area...cool... fellow Ubuntu user nearby....

---

### Post by benanzo on 2007-05-13
you will need to add storage-0222 to your /etc/hosts file otherwise just substitute it's IP address for storage-0222 in fstab.

/etc/hosts:
```
192.168.1.101 storage-0222
```

or just put the IP in /etc/fstab:
```
\\192.168.1.101\\public /mnt/nas_disk smbfs user,defaults 0 0
```

otherwise your local machine wont be able to find it.  I should have specified that.

---

### Post by Shinobi326 on 2007-05-13
Wow.... I'm still floored I STILL can't get this work.  I'm a pretty patient guy but this is now getting to me.

I noticed you had (notice the double "\\" after the IP address)

```
\\192.168.1.101\**\**public /mnt/nas_disk smbfs user,defaults 0 0
```

which I tried in my Fstab file to no avail.  I tried with just a single "\" between the IP address and "public" to no avail.  I've tried upper and lower case on "PUBLIC" to no avail.

Here is my latest Fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=1d577556-342e-41d1-bc12-8ed5d1111410 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=8bddecf9-d5f9-484b-869a-47e2db92f50f none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
# //storage-0222/PUBLIC /net smbfs 0 0
\\192.168.1.152\PUBLIC /mnt/nas_disk smbfs user,defaults 0 0
```

I also added in the line to the hosts file like you said.  I actually just did this first without touching the Fstab file but it didn't work thus the reason why I started to also modify the Fstab file too.

Current Hosts File:
```

127.0.0.1 localhost
127.0.1.1 Office-Desktop.workgroup
192.168.1.152 storage-0222

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

As soon as I clicked save on the Fstab file a window popped up asking if I wanted to open the new mount which sounded like a good thing.  I go to root/mnt and I see a drive icon with "nas_disk" but when I click on it nothing is there.  I've restarted the machine and same thing, nothing there.

Where am I going wrong (again!)??  Thanks for your help so far!  I'm sure I'm missing something really stupid somewhere....

---

### Post by benanzo on 2007-05-13
I'm actually not sure it matters if there's a single \ or double \\ slash between the host and share in the address.  I just looked at mine and I have some with \ and some with \\   so take your pick I guess.

It could be that they're just not mounting at boot-time.

try:
```
sudo mount -a
```

this will attempt to mount everything listed in /etc/fstab.

If it has a problem with your samba share it will print some error in the console.  If you get no output then it didn't have any problems, so see if it mounted then.  You can look at dmesg to see what (if any) specific error you get:
```
dmesg | grep mount
```

---

### Post by dasunst3r on 2007-05-13
Before I mount a folder, I would first create the mount point.  See if that works.
```
sudo mkdir /mnt/nas_disk
```

You could also try mounting it via NFS, if your NAS devices support it.  I don't know how to do that very well, though...

---

### Post by Shinobi326 on 2007-05-14
Thanks guys!  When I finally did a complete power down and restart, somehow the share started to work.  I think it was an I/O error (idiot operator!) because I've been getting so used to simply just doing cntrl+alt+backspace for xserver starts it didn't dawn on me to maybe do a complete shutdown.  It's amazing how I have yet to "crash" this linux box.  I'm getting spoiled about not having to doing numerous restarts (windows) when you change anything about the pc.

THANKS!

---

### Post by stylofone on 2007-05-19
Hi guys, 
I've studied this thread and others, and have successfully got my Nexstar LX to mount at startup. It's called "eggplant", and I have the following line in my fstab for it:

\\eggplant\eggplant /media/eggplant smbfs auto,user,defaults,rw 0 0

This causes it to be mounted at bootup and its icon to appear on the desktop. The problem is, if I open it through this icon, or if I open it at its mount point (i.e. opening the folder /media/eggplant) I get read only access. 

If I open it by going through "Network" from the places menu, i.e. by opening smb://eggplant/, I can read AND write. 

I've tried changing the permissions on the media/eggplant folder, and added "rw" the the fstab (which shouldn't be needed anyway because it should be rw by default), but it's to no avail - the mounted drive is read-only. 

So can anyone tell me how to mount it with read AND write access? 

Many thanks for the advice I've already benefited from... and thanks in advance for anyone who can help me with this finishing touch!

---

### Post by Shinobi326 on 2007-05-19
And you are sure you have your NAS setup ALL USER & NO PASSWORD login?  Sounds more of a permission thing on the NAS side than the Linux box side.

Just a thought from a newbie!

---

### Post by stylofone on 2007-05-20
I'm pretty sure that's not the problem. The NAS does not require a password, and I can write to it if I access it through the network. Just not the mount path.

> **Shinobi326 said:**
> And you are sure you have your NAS setup ALL USER & NO PASSWORD login?  Sounds more of a permission thing on the NAS side than the Linux box side.

Just a thought from a newbie!

---

### Post by davidsandilands on 2007-10-15
I have just been running through the same problem. Then it hit me try sudo touch test and you will see you need to be root user to write to the drive.

---

### Post by Shinobi326 on 2007-10-22
So how do I permanently setup the connection/mapping so that it can have write permissions.

I'm still having problems with this issue even though it's been awhile since I originally posted this thread.

---

### Post by MegaJim on 2007-10-22
If you add "**uid=myusername**" after the other options in your fstab then any application launched with your credentials will have full read/write access to the mount, as this directs the smbfs daemon to mark all files and folders in the mount as belonging to your username.

However, it is more elegant to use "**gid=users**", so as to allow other users to access the shares (given that users is a group for all users of the system).

For example, mine is:

```

# <file system> <mount point>   <type>  	<options>       	<dump>	<pass>
# \\phoenix\UniSyncFolder - University backup mount for Grsync
\\phoenix\UniSyncFolder	/mnt/UniSyncFolder smbfs user,defaults,**gid=users** 0	0

```

You can list groups to which a user belongs

```

$groups myusername
james : james adm dialout cdrom floppy audio dip video 
plugdev users scanner netdev lpadmin powerdev admin

```

or simply

```

$groups
james adm dialout cdrom floppy audio dip video plugdev 
users scanner netdev lpadmin powerdev admin

```

to see groups of the current user.

Have fun.

---

### Post by dmizer on 2007-10-22
try the second link in my sig.  using cifs instead of smbfs allows for higher file transfer speeds, as well as eliminates the 2gb file size limit that comes with smbfs.

---

