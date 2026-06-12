---
title: "Mounting SMB share works in Console but not Fstab"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by Burning_Ranger on 2006-11-14
Hello.

I am using the following in fstab:

mount -t smbfs -o username=administrator,password=********,lfs //192.168.1.64/E$ /smb/e_drive

It doesn't work when I reboot. However If I run this same command in a console it works fine. What have I done wrong?

---

### Post by stashj on 2006-11-21
I had the same problem and had to refer to smb rather than smbfs in the fstab. I think the fstab line should read something like;

//192.168.1.64/E$ /smb/e_drive smb username=administrator,password=****,lfs

---

### Post by KayoPs on 2006-11-22
Ok this is how i did to make it work on fstab.
First of all if you want a little more security avoid to put the username and password in plain text in fstab. Instead of doing that u rather create a file named for instance .smbpasswd in the /root/ directory, with those entries:

At a comand line do:

```
sudo echo username=yourusername > /root/.smbpasswd
sudo echo password=yourpassword >> /root/.smbpasswd
```
don't forget then to change the permissions, by doing :
```
sudo chmod 600 /root/.smbpasswd
```
after that has been done, you can add this to the fstab:
```
//yourserver/yourshare /yourpath/to/mount smbfs credentials=/root/.smbpasswd,dmask=0777,fmask=0777 0 0
```
add a line similar to this for each mount you'd like.

---

