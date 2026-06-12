---
title: "Virtualbox shared files"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by trevorc on 2009-11-13
I have Virtualbox and Windows Vista as a guest on Ubuntu 9.1 
I need to share files between the two OS or get usb support between the two
I have read some of the answers to similar questions and tried them but to no avail. Can someone guide a complete beginner OAP with an easy to understand solution please

---

### Post by Soul-Sing on 2009-11-13
you have to install guestadditions: devices: Install Guest Additions”

terminal:
```
cd /media/cdrom0
```

```
sudo bash ./VBoxLinuxAdditions-x86.run 
```

devices: shared folders: machines folders: add/share window:
path to your shared folder

mount shared map:
```
cd /mnt
```

```
sudo mkdir share
```
```

sudo mount -t vboxsf Sharedmap /mnt/share
```

---

### Post by trevorc on 2009-11-13
Thanks for your reply, I have guest additions already installed and then I get baffled, to me the rest of it seems too technical, could you break it down into more explained detail so that I could print the page and follow step by step guides to get this working please

---

### Post by howefield on 2009-11-13
> **trevorc said:**
> ...could you break it down into more explained detail

Why don't you watch the videos on the virtualbox website, which explain how to do this ?

This will most likely answer your queries, then if you have any questions after that, post them.

[http://www.virtualbox.org/wiki/VirtualBoxTV](http://www.virtualbox.org/wiki/VirtualBoxTV)

The third video down the page takes care of it, but the others may be worth watching as well, each one is only about 10 minutes long.

---

### Post by konqueror7 on 2009-11-13
go to your VMs settings, then *Shared Folders*, add a new folder by exploring the directory. then in your Vista, go to *Run* and type,

```
net use **x:**\\vboxsvr\**sharedfolder**
```

'x:' is where you want to mount it on Vista, and
'sharedfolder' is the same as what you named your shared folder in *Shared Folders*

you may also want to adding the shared folder by using the 'Mount Network Drive' in *My Computer* and explore the folder in '\\vboxsvr\'.

---

