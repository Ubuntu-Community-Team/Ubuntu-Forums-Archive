---
title: "CD Rom problem"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by jeremyblake on 2009-01-31
I was trying to use my cd rom earlier and i keep getting this error:

[mntent]: line 9 in /etc/fstab is bad
mount: can't find /media/cdrom0 in /etc/fstab or /etc/mstab

so i ran sudo mount and got this..

jeremy@jeremy-desktop:~$ sudo mount
[sudo] password for jeremy: 
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jeremy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jeremy)
jeremy@jeremy-desktop:~$ 


Any idea on how to get my cd rom working again? I'm trying to format the entire hard drive to put WinXP back on here, then going to dual boot with Ubuntu 8.10

---

### Post by mcduck on 2009-01-31
> **jeremyblake said:**
> 
Any idea on how to get my cd rom working again? I'm trying to format the entire hard drive to put WinXP back on here, then going to dual boot with Ubuntu 8.10
In that case there's no reason to get the CD drive working in Ubuntu. You have no use for it for now, as the Windows install CD is a bootable disk and you won't be running it from inside Ubuntu anyway..

---

