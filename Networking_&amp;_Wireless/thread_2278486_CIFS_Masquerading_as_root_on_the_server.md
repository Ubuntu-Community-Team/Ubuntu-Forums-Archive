---
title: "CIFS: Masquerading as root on the server"
date: 2015-05-16
forum: Networking &amp; Wireless
---

### Post by PenguinLust on 2015-05-16
I have a file server that can't run NFS, so it runs SAMBA. It also only has 1 user: root (don't ask). I want to be able to connect from my client using a non-root user in CIFS, and have the server think it's root. Unfortunately, the client just seems to treat the remote file system as root only so the permissions I get are accordingly. How can I do this? I've tried all kinds of options in fstab, like "uid", "setuid", etc. but nothing works. I've also noticed that despite setting a ton of options in fstab, when I type "mount" and it lists all the mounts, the only option for my cifs mount is "rw". Why?

---

### Post by SeijiSensei on 2015-05-17
You can force Samba to use the root account when managing the share by adding "force user = root" and "force group = root" to the stanza in smb.conf that defines the share.  You might want to make the share "public" in Samba with 770 permissions on the actual shared directory.  If you try adding a user with smbpasswd it will want to find a corresponding Unix user.  With "public" anyone can connect to the share, but all file transactions will occur with root privileges.

You'd be much better off creating a Unix user account, but it sounds like that route isn't available to you.

I've never heard of a machine running a Unix variant that cannot run NFS.

---

### Post by PenguinLust on 2015-05-17
> **SeijiSensei said:**
> You can force Samba to use the root account when managing the share by adding "force user = root" and "force group = root" to the stanza in smb.conf that defines the share.
I tried this. I'm still able to mount the share and read files, but still get "permission denied" when I try to write a file from the client system.

> You might want to make the share "public" in Samba with 770 permissions on the actual shared directory.
Really? That doesn't sound public. It used to have global read and execute permission, but this chmod took that away.
> I've never heard of a machine running a Unix variant that cannot run NFS.
You could be forgiven for not having heard of [OpenELEC]("http://openelec.tv/"). 'Very *ad hoc*.
Here's the smb.conf mod:
```
[HDD]
  path = /var/media/sda1-ata-ST9320325AS_5VEA
  available = yes
  browsable = yes
  public = yes
  writeable = yes
  force user = root
  force group = root

```
And the fstab on the client:
```
//rpi/HDD       /home/PL/pi_fileserver       cifs    defaults,noauto,uid=0,gid=0,username=root,password=openelec,iocharset=utf8,file_mode=0777,dir_mode=0777 0       0

```
Other than that, the only mod I made was chmod 770 /var/media/sda1-ata-ST9320325AS_5VEA

---

### Post by SeijiSensei on 2015-05-17
It shouldn't need global permissions because the force user/group directives tell Samba to do everything as root.

Maybe you just need to create a Unix user that matches your Windows username, then add it to Samba with "smbpasswd".

I tried OpenELEC on a Raspberry Pi but quickly dropped it in favor of Raspbian.

---

### Post by PenguinLust on 2015-05-17
> **SeijiSensei said:**
> Maybe you just need to create a Unix user that matches your Windows username, then add it to Samba with "smbpasswd".

I tried OpenELEC on a Raspberry Pi but quickly dropped it in favor of Raspbian.

You mean I should create a new user on the server? I don't think that's possible. Even if it was, wouldn't I have to make all the files on the shared system belonging to that user? That wouldn't work either, since, at the very least, new files written to that system would be root.

I think Raspbian was the first one I tried. I quickly lost patience w/a system that couldn't even use a static IP address.

---

### Post by SeijiSensei on 2015-05-17
Raspbian is just Debian. Last I checked you could [set up a static IP in /etc/network/interfaces]("http://elinux.org/RPi_Setting_up_a_static_IP_in_Debian") there just as you can in Ubuntu.

If you open a shell in OpenELEC, is there no "adduser" or "useradd" command?  If not, you could manually edit /etc/passwd to add one.  Just copy the equivalent line for your username on some Ubuntu machine to the bottom of /etc/passwd.  It will look like this:
```
seiji:x:1000:1000:SeijiSensei:/home/seiji:/bin/bash
```
You'll need a parallel entry in /etc/group:
```
seiji:x:1000:
```
Finally, just create the home directory and make it owned by the new user
```

sudo mkdir -p /home/seiji
sudo chmod -R seiji:seiji /home/seiji

```
You probably don't need sudo if everything runs with root privileges. That fact alone would disqualify a distribution in my mind.

---

### Post by PenguinLust on 2015-05-17
I don't feel comfortable circumventing the single-user system that the developers have deliberately set up. There'd still be the problem about the root on the server creating new files. Is there no way to do this from the client-side?

---

