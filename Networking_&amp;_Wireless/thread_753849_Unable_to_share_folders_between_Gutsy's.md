---
title: "Unable to share folders between Gutsy's"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by saz on 2008-04-13
hi,

i'm trying to share one folder on a pc that is in my office, so i can access it on my bedroom with my other pc. both pc's are running gutsy. i've added that folder to the shared folder, and added the access to it to my local ip in my bedroom, but i can't access the shared folder! if try it through nautilus, there is only windows network, if i try to mount it i get the output that the fs type is wrong...

any help?

if you take a look at this guide, you'll see the exact steps that I tried...

[http://www.techotopia.com/index.php/Sharing_Ubuntu_Linux_Folders_with_Remote_Linux_and_UNIX_Systems#Installing_the_NFS_Services_on_Ubuntu_Linux](http://www.techotopia.com/index.php/Sharing_Ubuntu_Linux_Folders_with_Remote_Linux_and_UNIX_Systems#Installing_the_NFS_Services_on_Ubuntu_Linux)

---

### Post by isparkes on 2008-04-13
Can you show the outputs of the "mount" command on the client machine?

Type "mount"

---

### Post by isparkes on 2008-04-13
Also check that you can physically see the host machine from the client. On the host type 

 ifconfig

Make a not of the dotted number after "inet addr:" For example mine is 1.223.65.17.

On the client machine type

 ping 1.223.65.17

substituting your number from the ifconfig command.

You should see something like

 PING 1.233.65.174 (1.233.65.174) 56(84) bytes of data.
 64 bytes from 1.233.65.174: icmp_seq=1 ttl=64 time=0.040 ms
 64 bytes from 1.233.65.174: icmp_seq=2 ttl=64 time=0.024 ms

If you do, it's not a network problem.

---

### Post by saz on 2008-04-13
no it is not a network problem.. the host pings ok..

here is the mount output:

```
sa@Thorn:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/hda on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=sa)
```

and here is what i get when i try to mount the specific folder:
```
sa@Thorn:~$ sudo mount 192.168.1.140:/home/salapc/DOWNLOADS /home/sa/downloads-share/
mount: wrong fs type, bad option, bad superblock on 192.168.1.140:/home/salapc/DOWNLOADS,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by saz on 2008-04-13
hey c'mon... help?

---

### Post by Iowan on 2008-04-14
You do have Samba server installed on the source (office) machine? Post the **/etc/samba/smb.conf**  file.

---

### Post by saz on 2008-04-14
> **Iowan said:**
> You do have Samba server installed on the source (office) machine? Post the **/etc/samba/smb.conf**  file.

yes i have the Samba server installed, however i wanted to use the NFS server...

---

### Post by Iowan on 2008-04-14
> **saz said:**
> 
```
sa@Thorn:~$ sudo mount 192.168.1.140[COLOR="Red"]_:_[/COLOR]/home/salapc/DOWNLOADS /home/sa/downloads-share/
mount: wrong fs type, bad option, bad superblock on 192.168.1.140:/home/salapc/DOWNLOADS,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
NFS between Ubuntu's DOES make sense - that colon looks out of place, though.

---

### Post by saz on 2008-04-16
> **Iowan said:**
> NFS between Ubuntu's DOES make sense - that colon looks out of place, though.

well.. unfortunately it is not!

---

### Post by blastus on 2008-04-16
Did you solve this problem? I'm having the exact same issue. I only have NFS installed and only want to use NFS as there are only Ubuntu machines on my network.

---

### Post by blastus on 2008-04-16
I got it working. You have to install the NFS client on the machine that is trying to access the shares. After I installed the NFS client I no longer got the "mount: wrong fs type, bad option, bad superblock on..." error. To install the NFS client enter...

```
sudo apt-get install portmap nfs-common
```

I got this info from [Ubuntu Guide - NFS](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NFS_Server)

Edit: I don't have Samba installed, just NFS.

---

