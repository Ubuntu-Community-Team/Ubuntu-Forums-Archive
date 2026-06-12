---
title: "Was told that this was not fixable!!"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by tbuss on 2007-04-06
Trying to share files across my network using [COLOR="Red"]Samba[/COLOR]
3 pc's all using Ubuntu

The files I'm trying to share are located on a [COLOR="Red"]external hdd
[/COLOR]
I have [COLOR="Red"]mounted[/COLOR] the external hdd and installed [COLOR="Red"]ntfs-3g[/COLOR]

I can read and write to the external hdd with no problems.

I then enable sharing on the file I want to share (on external hdd)

I'll go to another pc on the network: connect to server -> windows share -> IP address.
I can connect just fine, I even see the folder I want to access. When I try to access the folder it fails. It says: 
> The folder contents could not be displayed.
"Home_Productivity" couldn't be found. Perhaps it has recently been deleted.

I then [COLOR="Red"]restarted samba[/COLOR] and tried again; same result.

After that I enabled sharing on a folder located on my internal hdd
The share worked.

Is there something special I need to do so that other pc's can access shared files located on my external hdd? I found this, not sure if it will work because my hdd is a [COLOR="Red"]firewire[/COLOR] connection:

```
[usbdisk]
comment = Ekstern harddisk
path = /media/usbdisk
browseable = yes
read only = no
public = yes

```

Tried changing:
 [usbdisk] *to* [External]
path=/media/usbdisk *to* path=/media/External
restarted samba: sudo /etc/init.d/samba restart
The share still failed.

**If it helps here are the two shares I created as shown in smb.conf**

**This share fails:**
```
[Home_Productivity]
path = /media/External/Home_Productivity
available = yes
browsable = yes
public = yes
writable = yes
```

**This share works:**
```
[docs]
path = /home/tbuss/docs
comment = test share file
available = yes
browsable = yes
public = yes
writable = yes
```

---

### Post by tbuss on 2007-04-07
**I've checked my samba log files**

Not sure if there is any useful info there, saw a lot of permission denied statements for the external hdd; [COLOR="Red"]since ntfs-3g doesn't know permissions I figured the problem is with the fake permissions that are set with mount options[/COLOR] (something needs to be changed in there so that all users on the network can access and read and write to the external hdd) 
[B]
output from mount:[/B]

```
tbuss@tbuss-desktop:~$ mount
/dev/hdb5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
/dev/sda1 on /media/External type fuse (rw,nosuid,nodev,noatime,allow_other,default_permissions)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
tbuss@tbuss-desktop:~$ 
```

Anyone have any suggestions?

---

### Post by tbuss on 2007-04-07
Well apparently it is not possible to share files from a external hdd, you can write to it and you can even read the contents, but don't  try to share the files. Plus, I think I'm the only Ubuntu user in the world that is trying to share files from a firewire external hdd. You could backup all your data and format the drive to something like FAT32, but where is my data going to go. So, I have two options forget about sharing files from the external hdd, if I need to access files across the network I can just log into the pc that the drive is connected to. Or I could spend more money on hardware (already had to buy a wireless card that would work) and buy another hdd for my pc (one of those types that go inside the pc).

If anyone reads this, apparently some people do, they will say that I haven't searched or I haven't asked for help or I'm to impatient.  

If you been reading this forum or had been involved with the many sessions on #ubuntu, what else is there to do.  

Have you mounted the drive correctly......yes
Have you installed samba?......yes
Show me the contents of mount   I'm sorry, ntfs-3g looks different I can't help you
Can you access the external hdd from you pc ?.......yes
Try mounting the share with smbfs............yes
Try editing the smb.conf for external drive..........yes
Search samba website...............yes
Samba man pages...............greek

User friendly, Linux for human beings (we just say that)

---

### Post by gbesso on 2007-04-07
Just a thought, I have no idea if it works...
Did you try creating a link to the file outside /media/External?
say, in your home directory and sharing that?

It probably won't work, but hell, I thought I'd suggest it >_<

---

### Post by tbuss on 2007-04-07
I tried what you said, it didn't work. I think I'm going to try and use something other than samba to share files on the network. For some reason external hard drives have a major issue with file sharing in Ubuntu. Doesn't make sense to me; if you are able to mount the external drive and format it to use the same file systems as your os, why would sharing a file on that drive be such a headache.

---

### Post by tbuss on 2007-04-07
**The saga continues, my quest to one day realize the pleasure of accessing a file on one computer from another computer on a local network. Impossible you might say, maybe. others might think I'm crazy, maybe. But I'm going in, I'm giving it a shot.**

Decided I wouldn't use samba anymore, anyone that has helped said samba is not the way to go. I have since gone on to bigger and better things. I am now trying to set up a NFS client/server configuration so I can share files on my network. But, yes, there is a but. I have run into problems. 

```
Install NFS Server
sudo apt-get install nfs-kernel-server nfs-common portmap

sudo vi /etc/exports (Created Share)
sudo /etc/init.d/nfs-kernel-server restart
sudo exportfs -a
sudo apt-get install portmap nfs-common

cd /
sudo mkdir Home_Productivity

**Problem with mounting:**
sudo mount 192.168.2.3:/Home_Productivity /Home_Productivity

```
> [COLOR="Red"]ERROR[/COLOR]: mount: 192.168.2.3:/Home_Productivity failed, reason given by server: Permission denied


So, what I now need is a, well I don't know. I guess I will be installing a high speed sneakernet. Or maybe I could just set up a ftp server and access my files that way, It seems easier to setup proftpd than it does to share files from a local computer to another. But, I can share files, just not when they are located on a external hdd. Maybe I should just get rid of the external hdd and put a bigger hdd in my pc. Then I could share all the files I wanted. But how is it possible to read and write files to the external hdd from the local pc but not be able to share files on the network.

---

### Post by tbuss on 2007-04-08
Well, I **** canned the external hdd, after many hours in forums with people who obviously feel they are superior to anyone that would ask such an elementary question; and posting endless question across all forums, and reading every piece of information that Google could spit at me on how to share a freakin file on a external hard drive. I thought to my self   **"why am I doing this, why am I bothering with trying to get things to work all the time, why would I settle to spend more time trying to figure out how to get my pc to work, than time actually spent being productive?" **These are the same questions that plagued me before I switched, Ironic isn't it. I'm just upset because I have literally not left my computer during every piece of free time I have; all for trying to figure this out. I guess you just don't realize how good something actually is until it's gone. Does that mean I'm going back? No, just not convinced I'll stay for everyday activities, maybe as just a hobby.

---

### Post by Smerity on 2007-04-21
You're not the only person in the world having this problem =]

I mounted an old NTFS hard drive using ntfs-3g and when I wanted to share a folder using SAMBA it gives me the exact same error you had. I unfortunately have to copy the files to my original hard drive and use it from there :S

This will be a real pain me thinks...

If I find a solution I'll throw it back at you - good luck mate

---

### Post by tbuss on 2007-04-21
I just use ssh for accessing files across the network now. I would have liked to use samba, but ssh seems to work alot better

---

