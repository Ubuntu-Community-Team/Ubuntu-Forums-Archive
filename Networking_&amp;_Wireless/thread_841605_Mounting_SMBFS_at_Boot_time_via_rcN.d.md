---
title: "Mounting SMBFS at Boot time via rcN.d"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by cmfarley19 on 2008-06-26
I have created the following bash script in /etc/init.d called mnt_gcctfs1.sh with the following contents.
```
#! /bin/sh
case "$1" in
start)
echo "Mounting GCCTFS1..."
mount -t smbfs //gcctfs1/engineer /media/engineer -o username=uname,password=pword,iocharset=utf8,file_mode=0777,dir_mode=0777
;;
stop)
echo -n "Unmounting GCCTFS1..."
umount /media/engineer
;;
*)
echo "Usage: $0 {start|stop}"
exit 1
esac
exit 0

```
I can run this from the command line and it works just fine and mounts and unmounts the share appropriately.
```
./mnt_gcctfs1.sh start|stop
```
I ran the update-rc.d utility:
```
root@gcnpd:/etc/init.d#  update-rc.d mnt_gcctfs1.sh start 99 2 3 4 5 . stop 01 0 1 6 .
 Adding system startup for /etc/init.d/mnt_gcctfs1.sh ...
   /etc/rc0.d/K01mnt_gcctfs1.sh -> ../init.d/mnt_gcctfs1.sh
   /etc/rc1.d/K01mnt_gcctfs1.sh -> ../init.d/mnt_gcctfs1.sh
   /etc/rc6.d/K01mnt_gcctfs1.sh -> ../init.d/mnt_gcctfs1.sh
   /etc/rc2.d/S99mnt_gcctfs1.sh -> ../init.d/mnt_gcctfs1.sh
   /etc/rc3.d/S99mnt_gcctfs1.sh -> ../init.d/mnt_gcctfs1.sh
   /etc/rc4.d/S99mnt_gcctfs1.sh -> ../init.d/mnt_gcctfs1.sh
   /etc/rc5.d/S99mnt_gcctfs1.sh -> ../init.d/mnt_gcctfs1.sh
```
I rebooted expecting to find the share mounted and it is not.
I can again run the script manually from the command line, but it does not work during the boot process.

Any thoughts?

Chris

---

### Post by cmfarley19 on 2008-06-30
Still looking for some help on this.

Anyone? Anyone?

Chris

---

