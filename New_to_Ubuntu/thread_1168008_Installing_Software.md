---
title: "Installing Software"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by moebob24 on 2009-05-23
Ok, I need some help installing software that does not come from the package manager. I Downloaded the .tar.gz archive and extracted the contents. Now what. The content of it was 1 file and it isn't an install file because when I double click it, nothing happens. By the way, the software is PowerISO.

---

### Post by taurus on 2009-05-23
Isn't PowerISO a windows program?  Try installing it with wine (even that is not a guarantee it would install).

---

### Post by Mornedhel on 2009-05-23
1. What is the name of the file in the archive ?

2. Why would you want to install PowerISO anyway ? If you want to mount ISO files, the mount command already does this. If you're looking to burn CDs and DVDs or rip them to ISOs, Brasero already does this.

---

### Post by moebob24 on 2009-05-23
> **taurus said:**
> Isn't PowerISO a windows program?  Try installing it with wine (even that is not a guarantee it would install).

There is a Linux version of it. At least I think it is. Besides, I don't have wine running and I seriously doubt my Linux box could handle it. It is an older PC I got as a gift, so I upgraded the RAM and threw Linux on it. It runs pretty fast (Ubuntu is awesome) for an older PC.

---

### Post by taurus on 2009-05-23
What is the exact name of that file?

---

### Post by moebob24 on 2009-05-23
> **Mornedhel said:**
> 1. What is the name of the file in the archive ?

2. Why would you want to install PowerISO anyway ? If you want to mount ISO files, the mount command already does this. If you're looking to burn CDs and DVDs or rip them to ISOs, Brasero already does this.

Whoa! Linux already has ISO mounting? Ok thats all I needed to know.

---

### Post by ALIENDUDE5300 on 2009-05-23
Hi, extract the archive to a folder, and paste a list of the files in the archive here inside CODE tags. After that, I'll try to help you.

EDIT: Nevermind, you said linux already has ISO mounting, and no longer need the program.

---

### Post by Mornedhel on 2009-05-23
(sudo mount -t iso9660 /path/to/image.iso /media/cdrom -o loop)
(do your thing)
(sudo umount /media/cdrom) (note: it's umount, not unmount)

I'm sure there are GUIs to do this as well.

---

### Post by gandaran on 2009-05-23
> **moebob24 said:**
> There is a Linux version of it. At least I think it is. Besides, I don't have wine running and I seriously doubt my Linux box could handle it. It is an older PC I got as a gift, so I upgraded the RAM and threw Linux on it. It runs pretty fast (Ubuntu is awesome) for an older PC.
tried that poweriso linux version, it doesn't work in jaunty, must be some missing dependencies I cont find out which ones.
try installing from synaptic isomaster, it does pretty much the same as poweriso.

---

### Post by taurus on 2009-05-23
> **Mornedhel said:**
> (sudo mount -t iso9660 /path/to/image.iso /media/cdrom)
(do your thing)
(sudo umount /media/cdrom) (note: it's umount, not unmount)

I'm sure there are GUIs to do this as well.

For an ISO image, you need to include -o loop option with your mount command though.

```
sudo mount -t iso9660 /path/to/image.iso /media/cdrom -o loop
```

---

### Post by moebob24 on 2009-05-23
> **Mornedhel said:**
> (sudo mount -t iso9660 /path/to/image.iso /media/cdrom)
(do your thing)
(sudo umount /media/cdrom) (note: it's umount, not unmount)

I'm sure there are GUIs to do this as well.

Honestly, I found that the terminal is alot faster than GUIs, and I come from a pure Windows background. I seriously love Linux!

---

### Post by Mornedhel on 2009-05-23
> **taurus said:**
> For an ISO image, you need to include -o loop option with your mount command though.

Yeah, I always forget that. mount does remind you that you need it, though.

---

### Post by moebob24 on 2009-05-23
> **Mornedhel said:**
> Yeah, I always forget that. mount does remind you that you need it, though.

```

sudo mount -t iso9660 /home/bill/Desktop /media/cdrom

```

This comes back as 
```

mount: /home/bill/Desktop is not a block device

```

Any ideas. Should I put in -o instead of -t?


EDIT:
Hold up, I gotta rerun the command. I realized I didn't name the ISO file.

---

### Post by ALIENDUDE5300 on 2009-05-23
> **moebob24 said:**
> ```

sudo mount -t iso9660 /home/bill/Desktop /media/cdrom

```

This comes back as 
```

mount: /home/bill/Desktop is not a block device

```

Any ideas. Should I put in -o instead of -t?

Try sudo mount -t iso9660 /home/bill/Desktop/isoname.iso /media/cdrom
Also, if you already have something mounted to /media/cdrom, it might not work right.

---

### Post by taurus on 2009-05-23
> **moebob24 said:**
> ```

sudo mount -t iso9660 **[COLOR="Red"]/home/bill/Desktop[/COLOR]** /media/cdrom

```

I don't see a name of the file (.iso) that you want to mount?

> This comes back as 
```

mount: /home/bill/Desktop is not a block device

```

Any ideas. Should I put in -o instead of -t?

Should look at my previous post, #10.

---

### Post by Mornedhel on 2009-05-23
Urm.

Maybe put the image instead of a folder ?

I doubt you'll be able to mount your desktop as an ISO image. :)

I edited my previous post to reflect other posters' corrections, so just in case here is an example again :

```
sudo mount -t iso9660 /home/<username>/Desktop/POD.iso /media/cdrom -o loop
```

Damn, Taurus beat me to it.

---

### Post by moebob24 on 2009-05-23
> **Mornedhel said:**
> Urm.

Maybe put the image instead of a folder ?

I doubt you'll be able to mount your desktop as an ISO image. :)

I edited my previous post to reflect other posters' corrections, so just in case here is an example again :

```
sudo mount -t iso9660 /home/<username>/Desktop/POD.iso /media/cdrom -o loop
```

Damn, Taurus beat me to it.

I was starting to think that.

---

### Post by moebob24 on 2009-05-23
I got it!!! 

Thanks for the help everyone! This is why I love the Linux community. Everyone here has helpful advice. I could never get that on an XP forum. 

Anyway, thanks alot. I'm sure I'll be back soon with more questions.:D

---

### Post by ajgreeny on 2009-05-23
In 9.04 all you need to do is double click (or perhaps right click and choose) and an iso file will be opened in archive manager; no need to bother with the command line any more.

---

### Post by Mornedhel on 2009-05-23
> **ajgreeny said:**
> In 9.04 all you need to do is double click (or perhaps right click and choose) and an iso file will be opened in archive manager; no need to bother with the command line any more.

Huhh. I never noticed that.

Right-click and "Archive Mounter". I was wondering when someone would get to implementing that.

---

### Post by moebob24 on 2009-05-23
> **Mornedhel said:**
> Huhh. I never noticed that.

Right-click and "Archive Mounter". I was wondering when someone would get to implementing that.


WOW this is fun. After all that all I had to do was right click. HAHAHA

---

