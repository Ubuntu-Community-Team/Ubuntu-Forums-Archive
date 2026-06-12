---
title: "Is there any way I can mount a file to the cd drive without having to burn it"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by coneill659 on 2011-06-10
I have downloaded a dot iso file that needs to be burnt to a disk and then run on the cd drive. Is there any way I can mount this file to the cd drive without having to burn it to a disk? Similar to the mount'n'drive manger in daemon tools for windows.

---

### Post by dmacg on 2011-06-10
hell why sure there is. Hello there. look at free app called universal usb installer. easilly found by a google search, a few perfunctionaries and soon thereafter bob is your crossdressed aunty. an iso has to be read before being mounted any way you go about it. i learnt this the boring by attempting every other way. remember to prefix all searches with linux.

---

### Post by shad0w_walker on 2011-06-10
Open up terminal (Applications > Accessories > Terminal)
Then run this

```

sudo mount -o loop /path/to/iso /media/cdrom

```

You may need to run

```
sudo mkdir /media/cdrom 
``` 

If it tells you there isn't a /media/cdrom directory.

The commands will ask you for your password to run (They can alter the system so need admin rights)
When you type it, it won't show anything, but it is there.

Edit:
To unmount it when you're done, same process but use:

```

unmount /media/cdrom

```
Also, there are some programs in the applications manager that should do the same trick. Can't remember them off the top of my head though. Search for something like 'ISO mount' should do it.

---

### Post by comput99 on 2011-06-10
how's tht for infraction?

---

### Post by shafin on 2011-06-10
This feature is built-in in ubuntu. In nautilus, double clicking any iso file should mount that file, and the drive will become visible in the left pane.

---

### Post by jtarin on 2011-06-10
> **shad0w_walker said:**
> 
Also, there are some programs in the applications manager that should do the same trick. Can't remember them off the top of my head though. Search for something like 'ISO mount' should do it.One is Gmount-iso
and you will find its menu entry under "System Tools" after installation.

---

### Post by aeronutt on 2011-06-10
> **shafin said:**
> This feature is built-in in ubuntu. In nautilus, double clicking any iso file should mount that file, and the drive will become visible in the left pane.

For me, right clicking, selecting "open with Archive Mounter" works.

---

