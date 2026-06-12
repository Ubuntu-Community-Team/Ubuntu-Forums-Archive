---
title: "Manual fsck, how do do one?"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by scotcella on 2009-02-18
FYI, I am dual booting using Ubuntu 8.04 and Vista on a laptop.

Okay, here is my problem.

I am having problems with my laptop battery, recently stopped working so I am only able to use it when it's connected to an electrical outlet. The electrical outlet accidentally was ripped of my laptop a couple times and now and the laptop has decided to come up with a black screen. 

```
/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
     (I.E., without -a or -p options)
fsck died with exit status 4

*an automatic filesystem check (fsck) of the root filesystem failed. A manuall fsck must be freformed then the filesystem restarted. The fsck shoulbe be pre formed in maintenance mode with the root file system mounted in read-only
*root filesystem is currently mounted in read only mode. a maintenace shell will now be started. After preforming a system maintence, press Controll-D. to terminate the mainience shell and restart the system.
bash: no job control in the shell
bash: groups: command not found
bash:lesspipe: command not found
bash dirclass: commnand not found
```

So before I do anything, I want to check that I am doing the correct steps to fix it up. Obviously I need to use my live CD to ensure that my drive is not mounted and then run the fsck. I'm not sure how this will affect my laptop as I am dual booting with Ubuntu and Vista.

```
sudo fsck /dev/sda5
```

I would like some advice where to proceed next. I can't find my 8.04 Live Cd, if i burn the latest 8.10, is this okay to use or must i use 8.04 only? (As I can't find where I can download 8.04 on the ubuntu website)

Thanks in advance

---

### Post by gn2 on 2009-02-18
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Select the 8.04 by clicking the circle beside the 8.04 LTS line, select a location near you then click Begin Download.

---

### Post by bodhi.zazen on 2009-02-18
From a live CD (any live cd will work), with the partition un mounted :

sudo e2fsck -C0 -p -f -v /dev/sdxy

(Assuming it is an ext2/3 partition).

if that fails

        fsck -fvy /dev/sdxy

        *** How to fsck: [http://www.linux.com/feature/32026](http://www.linux.com/feature/32026)

---

### Post by scotcella on 2009-02-18
Great thanks for your replies.

How do I know my partition is unmounted?

---

### Post by bodhi.zazen on 2009-02-18
You can use grparted if it is on the live CD (it is on Ubuntu) or from the command line :

```
mount
``` , with no arguments mount will list the mounted partitions.

( or cat /etc/mtab)

---

### Post by scotcella on 2009-02-18
Great thank you...Now I am running the Live CD...

well I run the mount command and it came up with

```
ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
ubuntu@ubuntu:~$ 
```

Do I need to unmount these things? how do I do this?

---

### Post by oldos2er on 2009-02-18
> **scotcella said:**
> Great thank you...Now I am running the Live CD...

well I run the mount command and it came up with

```
ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
ubuntu@ubuntu:~$ 
```Do I need to unmount these things? how do I do this?

 No, you don't need to unmount those; only your /dev/sdx devices (hard disk partitions).

---

### Post by scotcella on 2009-02-18
Thank you to all who responded to my request for help.

I did everything and now everything is back to normal.

I now know what to do if something like this happens again!!!

Thanks again everyone! This is why I love Ubuntu and the Ubuntu Community so much, "it just works!"

ETA: I've noticed that I can't mark this thread as solved..  has this feature been removed?

---

