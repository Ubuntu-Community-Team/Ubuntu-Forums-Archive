---
title: "mount.nfs fails in Ubuntu / Works on Red Hat!!!"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by kristo5747 on 2010-08-13
Gurus,

I want log in locally to my Lucid (10.04) workstation and have my code saved over the network on my samba account

At work, all developers have samba user ids and when we were running Red Hat, we went thru the following procedure to get setup. 

[LIST]
[*]open a shell session to NFS server and execute the &#8220;id&#8221; command to get my samba user information.
[/LIST]
```
$> ssh &#8211;l alberto our_nfs_server
$> id
uid=7090(alberto) gid=100(users) groups=100(users)
```
[LIST]
[*]Create locally a login on my Linux workstation with the same login and uid.
[/LIST]
```
$>sudo useradd &#8211;u 7090 &#8211;g 100 &#8211;d /home/alberto &#8211;s /bin/bash alberto
```
[LIST]
[*]Define a password for my created login. ```
$> sudo passwd alberto
```
[*]Change permissions on the /home/alberto directory. Example:```
$>sudo chown alberto:100 /home/alberto
```
[*]Place this line at end of fstab:```

our_nfs_server:/d0/homedirs/alberto /home/alberto nfs defaults 0 0
```
[*]Mount the local directory ```
$> sudo mount -a
```
[/LIST]
```
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mount.nfs: access denied by server while mounting our_nfs_server:/d0/homedirs/alberto
```It does not work at all!!?? However, the same procedure on a RedHat workstation works fine. No errors.

We want to move all of our workstations/servers to Ubuntu so any help is welcome. 

Thank you!!!

Al.

---

### Post by jtarin on 2010-08-13
I was receiving the same error recently after my webmaster had to rebuild the server. Turns out the settings for the user account was limiting the number of connections to the share. As soon as he bumped that limit up, I was able to restore my mount.

---

