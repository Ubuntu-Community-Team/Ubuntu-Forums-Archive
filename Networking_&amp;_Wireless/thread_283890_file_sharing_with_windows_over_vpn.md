---
title: "file sharing with windows over vpn"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by jordanau on 2006-10-24
I was able to get vpnc to work with the cisco vpn of the university that i attend. I am not able to figure out how to access the files on the fileshare server. I get the welcome banner, so i know it is properly connected. On a windows machine, to reach the files i go to start>run and type \\nameoffolder and am asked for my student identification and password. Is this a samba share? does anyone know what to do after i connect via vpn? If anyone needs help on getting vpn set up in a similar fashion let me know.

---

### Post by harisund on 2006-10-25
Typically you could do the following: 

mount -t smbfs //path_to_machine/nameoffolder /path_where_you_want_it_mounted -o username=Your_User_name

---

### Post by jordanau on 2006-10-25
thank you for the response, when i try that i get the following (i placed "username" where my username goes (in other words i had my college username there. I also tried it without cadcit before the username and got the same error. I don't think it matters though, the error is occuring with smbfs i think. 

```
jordan@jordan-desktop:~$ sudo mount -t smbfs //cadcfiles/students /mnt/cadcfiles -o username=cadcit\username
mount: wrong fs type, bad option, bad superblock on //cadcfiles/students,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

jordan@jordan-desktop:~$ dmesg | tail
[17465559.980000] Buffer I/O error on device sda2, logical block 29222234
[17465560.272000] Buffer I/O error on device sda2, logical block 29222232
[17465560.272000] Buffer I/O error on device sda2, logical block 29222233
[17465561.092000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17485304.972000] tun: Universal TUN/TAP device driver, 1.6
[17485304.972000] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[17485436.688000] smbfs: mount_data version 1919251317 is not supported
[17485491.292000] smbfs: mount_data version 1919251317 is not supported
[17485548.156000] smbfs: mount_data version 1919251317 is not supported
[17485568.004000] smbfs: mount_data version 1919251317 is not supported
jordan@jordan-desktop:~$ 
```

thanks

---

### Post by jordanau on 2006-10-25
okay i fixed that problem, i had to obtain smbfs from repos now i have the following error...

```
Password: 
32507: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

```

I assume it is probably me typing the wrong foldername or something

if you can figure anything out let me know

---

### Post by harisund on 2006-10-25
Since it says Access Denied, maybe you shouldn't be entering your user name that way? Try just username instead of domainname/username

---

### Post by jordanau on 2006-10-25
that doesn't seem to make a difference. The good thing at least is it sees the folders, i just have to figure out how to connect.

---

