---
title: "Auto mount share on boot"
date: 2020-06-04
forum: Networking &amp; Wireless
---

### Post by martin9992 on 2020-06-04
I'm new to Linux and have been following online guides to get a machine running(Ubuntu 18.04), but have run into a snag.  I can't get a share to mount on boot. I've added this to /etc/fstab

//WINDOWS_SERVER/SHARE /mnt/ftproot cifs credentials=/etc/samba/user

with my server and share name in the first bit.  I've got a credentials file with the user and password specified.  It's a Windows AD domain.  This works fine if I enter

sudo mount -a

but it doesn't mount on boot.  Any ideas?  I've searched all over, tried putting the script in /etc/network/if-up.d, and tried all sorts of options in fstab.  Why does it work fine if I type mount -a, but not when booting?

---

### Post by Morbius1 on 2020-06-04
Systemd has an automounter that might work for your situation. An automounter works by mounting on access of the mount point not at boot.

What may be happening here is that when you boot the network stack is not fully operational when fstab is read so it cannont connect to anything. Since the automounter works on access it should be after boot and after login.

[1] Unmount the share:
```
sudo umount /mnt/ftproot
```
[2] Change your fstab declaration to this:
> //WINDOWS_SERVER/SHARE /mnt/ftproot cifs credentials=/etc/samba/user[COLOR=#ff0000]**,noauto,x-systemd.automount**[/COLOR] 0 0
[3] Make systemd happy:
```
sudo systemctl daemon-reload
```
```
sudo systemctl restart remote-fs.target
```
[4] Now access /mnt/ftproot to verify its contents.

There is another option to have the mount automatically unmount after non use for a period of time: **x-systemd.idle-timeout=300**

After 300 seconds ( user definable ) of inactivity the share will unmount itself.

---

### Post by martin9992 on 2020-06-04
Ah, excellent, that worked!  Thank you.  I'll have to confirm once I get the FTP software configured that it gets mounted when the software tries to access it.  My hope is that I don't need to login to this machine at all once it is running, and if it reboots the software still has access to the mount.  But that's a next week problem, I think...

---

