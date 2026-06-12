---
title: "another feisty samba problem"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by TheWizzard on 2007-04-21
I just upgraded my computer from Dapper to Feisty. everything looks really great and i'm glad i've upgraded this time :KS 

there is, however one strange problem with samba. i use this machine as a client to log into a samba server called athlon. the server hasn't changed. 
i put the name of the server in /etc/hosts and 'ping athlon' works. 

if i try to mount samba with 
```
sudo mount -t cifs -o user=niels,password=iodshfkjnc,noperm //athlon/home /mnt/athlon
```
i receive an error message and 'dmesg | tail' returns:
CIFS VFS: cifs_mount failed w/return code = -22

however, if i use the command: 
```
sudo mount -t cifs -o user=wizzard,password=iodshfkjnc,noperm //192.168.1.102/home /mnt/athlon

```

it mounts perfectly :confused: :confused: 

is there anyone who understands what's going on here?

---

### Post by spin2cool on 2007-04-21
has your machine reloaded the hosts file since you updated it?  If not, try doing
```
sudo /etc/init.d/networking restart
```
and see if that helps.

---

### Post by TheWizzard on 2007-04-21
> **spin2cool said:**
> has your machine reloaded the hosts file since you updated it?  If not, try doing
```
sudo /etc/init.d/networking restart
```
and see if that helps.

i did reboot after editing the hosts file. unfortunately this doesn't work.

---

### Post by Mike-Bell on 2007-04-22
Same problem here

---

