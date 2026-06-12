---
title: "SMB still asking for password"
date: 2005-04-29
forum: Networking &amp; Wireless
---

### Post by bagohell on 2005-04-29
I want to connect to a share that is on a Windows box, in a windows Domain.
I used this path 

```
smb://DOMAIN;username:password@windowscomputername/share
```

I don't want to be prompted for the password, yet I am when ever I first try to connect to this share after a restart.

I've used this path before on other linux machines, and I don't get prompted for the password.  Is there something I'm missing with Ubuntu?

---

### Post by ifrflyer on 2005-04-29
Are you just connecting or trying to mount the share? 

I thought that the syntax for the latter was 

mount  -t filesystem something somewhere -o options

so something like 

```
mount -t smbfs //hostname/sharename /local/mount/point -o password=password,username=username,gid=gid,uid=uid
```

Or if you put it in your /etc/fstab then it would be (at least on mine it is):

```
#Samba Share
//hostname/public /home/user/samba smbfs  user,auto,rw,username=user,password=password,uid=user,gid=users,fmask=666,dmask=777 0 0
```

Try 

```
man mount
``` 

for more. 


Hope that helps!

---

### Post by gregorlowski on 2005-05-28
This is sort-of a shameless plug, but if you want a GUI tool to mount
samba shares, nfs, and other stuff, you can check out:

[http://gnetmount.sourceforge.net/](http://gnetmount.sourceforge.net/)
(shameless plug because I'm the developer)

If it requires a password for a share, it'll automatically bring up a username and password entry, and if no password is required then it will automatically mount as guest (if you don't enter a password it will try to mount as guest).

I wrote it for people at work because neither nautilus (at least the version in hoary) nor the gnome mount applet will let you mount a share if it requires a password. 

-Greg

---

### Post by [pl]ice on 2005-05-31
use guest account...
 in fstab : smbfs    ...rw,guest,user, ....

works for me, or there is option with

 mount -t smbfs -o guest //server/folder  /home.folder

works

(actually man smbmount...)

---

