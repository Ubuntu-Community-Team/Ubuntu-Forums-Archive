---
title: "No CIFS VFS for Ubuntu ???"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by xp_newbie on 2006-11-02
Disappointed by Gnome's VFS, which **doesn't make its services available to legacy non-Gnome apps** (e.g. Emacs and all Linux command line programs), I started searching for a consistent solution to access Samba shares from my Ubuntu laptop/desktop.

At first, I thought of using **mount -t smbfs** in **/etc/fstab**, but then I discovered that it requires putting passwords in the /etc/fstab file, in clear text...

So I continued searching and then I found... [CIFS VFS]("http://linux-cifs.samba.org/"). Unlike some other network filesystems all key network function including authentication is provided in kernel (and changes to mount and/or a mount helper file are not required in order to enable the CIFS VFS).

I gladly went looking for it in the Synaptic repositories, but... I found no mention of it - despite enabling universe and multiverse repositories. :(

Any idea whether there is a apt-able CIFS VFS package for Ubuntu?

Or should I install it directly from the .tgz archive?

Thanks!
Alex

---

### Post by Leslie Viljoen on 2006-11-13
You would expect the guys on the samba mailing list would be a little more helpful, since the solution is only one line. Cifs is in Ubuntu already:

mount -t cifs -o username=blah //server/share mount_dir

---

### Post by xp_newbie on 2006-11-22
> **Leslie Viljoen said:**
> You would expect the guys on the samba mailing list would be a little more helpful, since the solution is only one line. Cifs is in Ubuntu already:

mount -t cifs -o username=blah //server/share mount_dir

Leslie, thank you for the tip.

However, I just tried what you said (on a freshly installed Ubuntu Dapper) and I get the following error:

```
/mnt> sudo mount -t cifs -o username=xpnewbie //smbserver/xpnewbi /mnt/smbserver_xpnewbie
mount: wrong fs type, bad option, bad superblock on //smbserver/dani,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
Any idea what could be wrong?

Also, if I want to automate this so that it mounts every time I boot, will have to place password in /etc/fstab? Or is there a better solution?

Thanks,
Alex

---

### Post by cptvitamin on 2006-11-29
> Also, if I want to automate this so that it mounts every time I boot, will have to place password in /etc/fstab? Or is there a better solution?
[LIST=1]
[*]create a file in your home dir called .smbcred or something
[*]Put the following in this file:
```

username = your_username
password = your_password

```
[*]in the options for your entry in /etc/fstab, include credentials=/home/user/.smbcred
[/LIST]
chown the .smbcred file to root for added security.
Make sure you put spaces before and after the equals signs and put a carriage return after the password.

---

### Post by briantipton on 2008-02-14
> **xp_newbie said:**
> Leslie, thank you for the tip.

However, I just tried what you said (on a freshly installed Ubuntu Dapper) and I get the following error:

```
/mnt> sudo mount -t cifs -o username=xpnewbie //smbserver/xpnewbi /mnt/smbserver_xpnewbie
mount: wrong fs type, bad option, bad superblock on //smbserver/dani,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
Any idea what could be wrong?


I ran into this today.  If you haven't found the solution, try installing the smbfs package.

```
sudo apt-get install smbfs
```

That fixed it for me.

Brian

---

### Post by dmizer on 2008-02-15
cifs is part of the smbfs package.  you must install the smbfs package in order to use cifs.

```
sudo aptitude install smbfs
```

see the second link in my sig for more details.

---

