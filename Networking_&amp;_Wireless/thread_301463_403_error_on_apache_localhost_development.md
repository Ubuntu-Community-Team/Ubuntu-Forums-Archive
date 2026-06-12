---
title: "403 error on apache localhost development"
date: 2006-11-17
forum: Networking &amp; Wireless
---

### Post by martal on 2006-11-17
Using Apache2, my document root (defined in a sites-available file) is in a vfat partition (shared with XP). This is the fstab line:

# /dev/hda5
UUID=44D4-6C75 /media/data vfat defaults,utf8,umask=007,gid=46 0 1

I can write, create folders etc, working fine.

But I get a 403 error, access forbidden, when I try and open my virtual host name.

This is the sites-available file:
<VirtualHost *>
	DocumentRoot /media/data/webpages/plockton
	ServerName plockton
	DirectoryIndex index.shtml
	
	<Directory /media/data/webpages/plockton>
		Options Indexes FollowSymLinks MultiViews +Includes
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
	
	ErrorLog /media/data/webpages/plockton/logs/error.log

</VirtualHost>

Is my syntax correct?

NameVirtualHost * is in a conf.d file.

A similar setup has worked well for me in previous Ubuntus.

The owner of all my webpages is root, group is plugdev. As a vfat partition, I can't experiment with permissions, only from the fstab. Is this where the problem is, or somewhere else?

Any ideas?

---

### Post by Ensnared on 2006-11-17
Seems to me that the umask or user/group is the problem. Umask 007 sets the permissions to "rwxrwx---" on all files and directories on the VFAT partition, meaning only user and group have any access to it. The webserver runs as the user "apache" if I remember correctly, which is why you get access denied.

In order to let Apache serve the pages, it needs execute-permissions on all parent directories leading up to the site directory, and it needs read- and execute-access on the directory where the files are located.

A quick fix would be to change the umask in your fstab to 000 (or 002 to disable write-access), or alternatively specify the user or group apache's uid or gid in fstab, and then remount the disk (sudo mount -o remount  /media/data)
I may be wrong on the username, I'm at work now so I can't check to make sure - it might be user "nobody" instead, but I'm _fairly_ sure it's "apache" ;)

---

### Post by martal on 2006-11-17
Thanks, Ensnared, that worked.

fstab is now: defaults,utf8,umask=000

Maybe a little bit open, but could make life easier when I work on the family user accounts.

How would you specify the group for apache? There is no apache group in Users and Groups. And not a nobody or a plugdev.

---

### Post by Ensnared on 2006-11-17
Not sure where you're looking for these users, but if you check your /etc/passwd and /etc/group you'll see all system users and groups there (if you're using a graphical tool, many of the system users are probably hidden).

I don't remember which user apache runs as (no Ubuntu, and a very cranky firewall here at work), but you could probably find out by doing this:```
ps aux | grep apache
```...which will list all apache processes running on the system, and will show the user they run as in one of the columns. The main process may run as root, but the child processes (you'll probably have 10 of those) are the actual ones handling requests, and they run as something else.

---

### Post by martal on 2006-11-17
Well, here's the result of the grep:

root      4731  0.0  0.4   8012  2452 ?        Ss   13:48   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  4732  0.0  0.3   7804  1756 ?        S    13:48   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  4733  0.0  0.5 229884  3068 ?        Sl   13:48   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  4735  0.0  0.5 229616  2812 ?        Sl   13:48   0:00 /usr/sbin/apache2 -k start -DSSL
martin    7160  0.0  0.1   2796   752 pts/0    R+   14:46   0:00 grep apache

Not sure what to do with that!

---

### Post by Ensnared on 2006-11-20
Apparently the apache user is www-data, so your fstab-line could look like this:```
UUID=44D4-6C75 /media/data vfat defaults,utf8,umask=007,user=www-data,gid=46 0 1
```

Alternatively, you can do this:```
cat /etc/passwd | grep www-data
``` which will show you the UID and GID for the user www-data - the line would show something like this: ```
www-data:x:UID:GID:andsomemorestuff
```
You can then change the "gid=46" to "gid=XXX" in your fstab-line (XXX being the actual GID, obviously).

---

