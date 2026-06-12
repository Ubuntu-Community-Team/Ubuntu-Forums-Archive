---
title: "Cant update until I can 'mount(?)' iso"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by tzarcasm on 2010-02-23
So the machine tells me that it wants to update but then I get prompted to insert the Ubuntu cd but since my netbook doesnt *have* a cdrom drive that is quite impossible. Also I dont want to buy an external cd-drive if theres a way around this.

I do have the iso on my desktop and have tried (with the proper iso name of course) this:

**sudo mount -o loop /home/hfs/desktop/ubuntu_netbook.iso /media/cdrom0**

To which I get: *"cant find"*

I do have the 'furious iso mount' software but dont know if thats the answer and dont know how to use it.

Thanks in advance.

EDIT:I'll add that I do have the bootable iso on USB stick as well.

---

### Post by sandyd on 2010-02-23
use acetone iso to mount the iso.
It should be mounted in /home/*username*/virtual-drives/1/

check if it is.
```

gksudo gedit /etc/apt/sources.list
```add this to the bottom.

```
deb /path/to/mounted/iso/ karmic main restricted

```save.
```

sudo apt-get update
```done.

---

### Post by 3rdalbum on 2010-02-23
Go to System > Administration > Software Sources and uncheck the CD. It will no longer ask for the CD.

---

### Post by tzarcasm on 2010-02-24
Thanks Carlee. I get 'malformed line in 58' when I try that. But I'll try acetone.

---

### Post by tzarcasm on 2010-02-24
Tried to install 'acetoneiso' and get 'error404' when I follow instructions on the web. I'll just uncheck the cd as 3rd album says. 

Then I'll chalk it up to *another* thing I cant be bothered with rather than spend **days** trying to figure out.

Thanks again for your help.

---

