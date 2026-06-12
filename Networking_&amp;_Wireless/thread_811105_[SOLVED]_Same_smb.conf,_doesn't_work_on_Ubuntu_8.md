---
title: "[SOLVED] Same smb.conf, doesn't work on Ubuntu 8"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by DoritosBR on 2008-05-28
Here's a dump of my smb.conf
It's the same I used on Ubuntu 7.10.

But on 8.04, it doesn't work.

The problem is:
WHen I try to access the "shared" share on Windows, it asks for a Guest Password.
When I try to access it from another linux, it just says "Failed to mount Windows share"

The correct is that anyone (inside the IP range 192.168.1.x) can access and write on this share without being annoyed, this means, no passwords, no authentication of any kind.

Any Help?

[global]
	workgroup = SHADALOO
	server string = %h server (Blanka)
	security = SHARE
	obey pam restrictions = Yes
	passdb backend = tdbsam
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	printcap name = cups
	dns proxy = No
	wins support = Yes
	panic action = /usr/share/samba/panic-action %d
	invalid users = root
	hosts allow = 127.0.0.1, 192.168.1.0/24

[printers]
	comment = All Printers
	path = /tmp
	create mask = 0700
	guest ok = Yes
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[shared]
	path = /mnt/sfat/shared
	available = yes
	browsable = yes
	public = yes
	writable = yes

---

### Post by jetsam on 2008-05-28
Two things to check.  First, verify that samba is running:
```
pgrep mbd -l
```
Should output something like this (with different numbers) if it is:
```
8219 nmbd
8221 smbd
8225 smbd

```

Second, double check that nothing has changed about the directory of your disk mount since the upgrade:
```
ls -al /mnt/sfat/shared
```

---

### Post by DoritosBR on 2008-05-28
> **jetsam said:**
> Two things to check.  First, verify that samba is running:
```
pgrep mdb -l
```
Should output something like this (with different numbers) if it is:
```
8219 nmbd
8221 smbd
8225 smbd

```

Second, double check that nothing has changed about the directory of your disk mount since the upgrade:
```
ls -al /mnt/sfat/shared
```

this one should output anything?

```
sudo pgrep mdb -l
```
or
```
pgrep mdb -l
```

Because they return nothing

But the services are running (i think)

```
marcelo@Blanka:~$ sudo ps aux | grep -e nmbd -e smbd
root      7603  0.0  0.1  55112  1312 ?        Ss   21:56   0:00 /usr/sbin/nmbd -D
root      7605  0.0  0.2  75556  2408 ?        Ss   21:56   0:00 /usr/sbin/smbd -D
root      7608  0.0  0.0  75556   736 ?        S    21:56   0:00 /usr/sbin/smbd -D
marcelo   9114  0.0  0.0   5164   836 pts/0    R+   22:05   0:00 grep -e nmbd -e smbd

```

I backed up a lot of configs from ubuntu 7, including the fstab

```
marcelo@Blanka:~$ ls -al /mnt/sfat/shared
total 53824
drwxrwx---  7 root plugdev    65536 2008-05-28 20:12 .
drwxrwx---  9 root plugdev    65536 1969-12-31 21:00 ..
drwxrwx---  3 root plugdev    65536 2008-05-28 20:12 Mozilla

-rwxrwx---  1 root plugdev 27505824 2008-04-27 18:28 Nokia_PC_Suite_rel_6_85_14_1_eng_us_web.exe

```

But I can't understant why with the same smb.conf that I backed up, it doesn't work.

BTW, I found out that the Gnome saying "Failed to mount Windows Share" IS a gnome bug

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/206439](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/206439)

It should ask password as well
When I try
```
smbclient \\\\192.168.1.50\\shared
```

It asks a password, like the Windows machine

---

### Post by jetsam on 2008-05-28
> this one should output anything?
No.  My mistake.  I meant **pgrep mbd -l** not _mdb_ (corrected in post above.)

Your smb.conf works ok for me in Hardy if I change the workgroup and subnet in **hosts allow** to appropriate values for my network and make an accessible directory at the right place.

> marcelo@Blanka:~$ ls -al /mnt/sfat/shared
total 53824
drwxrwx---  7 root plugdev    65536 2008-05-28 20:12 .
drwxrwx---  9 root plugdev    65536 1969-12-31 21:00 ..


...If I'm reading that right, the share directory is owned by root and group plugdev with no read permissions for other.  I think this would cause your trouble.  

Can you post the line from your fstab where the drive is mounted?  The plugdev group I think is usually for removable media...

---

### Post by DoritosBR on 2008-05-28
> **jetsam said:**
> The plugdev group I think is usually for removable media...


BINGO!

Thanks a lot.

I changed my fstab to:

```
UUID=1898-F536  /mnt/sfat       vfat    auto,user,rw,exec,utf8,umask=000 0 0

/dev/sdb1 /mnt/intfs      ntfs    defaults,umask=007,gid=46 0       1

/dev/sdb2 /mnt/irfs       reiserfs defaults        0       2

```

I don't remember how it was, but I saw it wasn't right and changed it to the backup I have.

Thanks, now It's working.

And now this post shall be the solution for anyone who has the same problem :)

---

### Post by jetsam on 2008-05-28
Excellent.  Glad you got it working!

:)

---

### Post by Iowan on 2008-05-28
> **jetsam said:**
> ... I meant **pgrep mbd -l**... That's _much_ easier than ```
ps ax |grep mbd
```... Always good to learn something new.  (Where's that thumbs-up smiley???)

---

