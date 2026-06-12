---
title: "Mount at boot not working"
date: 2020-01-03
forum: Networking &amp; Wireless
---

### Post by makitso on 2020-01-03
Running 19.10 Ubuntu Budgie.

I have a NAS device on my network and have this command below in my fstab file. 
The drive use to be available after a boot on 19.04 but now it is not.  However, if I  $ sudo mount /samba/rob it mounts.  
What am I doing wrong?

//192.168.1.205/rob /samba/rob cifs credentials=/var/credentials,uid=1000,gid=1000,vers=1.0 0

---

### Post by Morbius1 on 2020-01-03
Add two more options to your list: noauto x-systemd.automount
>  //192.168.1.205/rob /samba/rob cifs credentials=/var/credentials,uid=1000,gid=1000,vers=1.0[COLOR=#ff0000]**,noauto,x-systemd.automount**[/COLOR] 0         0

The automounter is designed to mount when the mount point ( /samba/rob ) is accessed.

If you want to have the full automount experience you can also add another option that unmounts the share when it has not been accessed for a specified time: x-systemd.idle-timeout:
>  //192.168.1.205/rob /samba/rob cifs credentials=/var/credentials,uid=1000,gid=1000,vers=1.0[COLOR=#ff0000]**,noauto,x-systemd.automount,x-systemd.idle-timeout=30**[/COLOR] 0         0
After 30 seconds of inactivity on the share it will automatically unmount but remount again if the mount point is accessed. The whole thing is relatively seamless to the user.

Either way when you are done editing fstab:

** Unmount the share:
```
 sudo umount /samba/rob
```
** THen do the systemd 2-step:
```
sudo systemctl daemon-reload
sudo systemctl restart remote-fs.target
```

---

### Post by makitso on 2020-01-03
Wow, good information, Thanks!!

---

