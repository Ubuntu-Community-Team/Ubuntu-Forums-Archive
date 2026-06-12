---
title: "mapping drives from a windows 2003 server"
date: 2005-04-17
forum: Networking &amp; Wireless
---

### Post by loom001 on 2005-04-17
I am trying to figure out how to map a couple of drives from my windows 2003 server on my linux (ubuntu Hoary) laptop. 

I can use under [places] the network server browser to browse all the drives on the 2003 server.  I just can't figure out how to map the drives. 

I did try to right click on the directory and do make link but I get this error: 
[B]
Error "Unsupported operation" while creating a link to then the server link.[/B]

Thanks for any help in advance...

 ](*,)

---

### Post by localzuk on 2005-04-20
The easiest way would be to use the mount comman. Something like:
```

mkdir /media/required-name
mount -t smbfs //server-address-or-ip/path/to/required/share/folder /media/required-name

```
This will mount the share in /mnt/required-foldername

When you have the command right, alter your /etc/fstab as root and include
```

//server-address-or-ip/path/ /media/required-name smbfs username=username,password=password,uid=500,gid=100,dmask=0007,fmask=0007 0 0

```
That should then load the link at start time.

---

### Post by tonym on 2005-04-20
As an alternative you could look at autofs.  This would then cope if the 2003 server wasn't up when you booted Ubuntu.

---

### Post by loom001 on 2005-04-24
Thanks for the info that did the trick!

 \\:D/

---

### Post by Abhi Kalyan on 2006-10-20
Hi, I have not even started yet.
Am not able to connect to a domain=zen.local, running on a winddows server 2003
Am not able to get to the shares
Am peeling my faace skin and pulling out my hair trying to figure out how???

---

