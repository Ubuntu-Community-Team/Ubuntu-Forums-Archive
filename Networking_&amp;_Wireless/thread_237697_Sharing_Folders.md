---
title: "Sharing Folders"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by Isoss on 2006-08-16
I have two ubuntu machines: a laptop and a pc. I have tried SSH to connect and it worked but it is so slow and sometimes the PC freazes while transfering big files I doubt it's a hardware incompitability.

Anyway, untill I find out where seems to be the problem I need an alternative solution. Does samba work between 2 ubuntu machines? if yes, HOW? how about FTP? I tried GFTP but using SSH2 method but had the same problem!

I also have another problem! I can't samba from my laptop while I can from my PC which can view all the windows PCs on the network. When I go to Places -> Network Servers -> Windows Networks it pompts: 
**"smb:///" is not a valid location.**
Please check the spelling and try again.

Hope this is simple

Thanks

Isos

---

### Post by Isoss on 2006-08-17
Hello there! come on I don't think it's hard!

---

### Post by o2kewl on 2006-08-17
You are correct; it isn't hard.   Setup NFS on both computers.

```
apt-get install nfs-common
```

On the server you need to modify the /etc/exports, /etc/hosts.allow files.


You should modify your /etc/fstab to look something like this:
IN the form of:  
1.2.3.4:/remote/system/path /local/system/path <variables>
This is what mine looks like:

```
192.168.0.254:/home/files/music /home/rug/multimedia/music nfs rsize=8192,wsize=8192,hard
192.168.0.2:/multimedia/tv /home/rug/multimedia/tv nfs rsize=8192,wsize=8192,hard
192.168.0.2:/multimedia/movies /home/rug/multimedia/movies nfs rsize=8192,wsize=8192,hard

```

---

### Post by Isoss on 2006-08-17
Alright thanks. I installed nfs-common on both but I am not sure what to modify! I can't find /etc/export and dunno what to do with /etc/hosts.allow. 

I have a questions about the fstab! do I have to mount? and what are rsize, wsize and hard?

Thanks.

---

### Post by edafe on 2006-08-26
Step-by-step instructions on how to configure Samba as a file server:

[http://www.edafe.org/ubuntu/index.html#samba](http://www.edafe.org/ubuntu/index.html#samba)

Regards,
Edafe

---

