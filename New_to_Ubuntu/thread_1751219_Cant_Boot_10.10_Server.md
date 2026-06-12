---
title: "Cant Boot 10.10 Server"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by steez on 2011-05-06
Hello, 
I have used these forums many times to answer my newb ubuntu questions, however I have created a problem that I cannot seem to find the answer to.

I believe what has happened is I had an external HDD plugged in that contained Win7 boot images from Acronis, when my nix machine restarted it decided to try and boot from them and now my MBR is messed up.

I have just one 1TB HDD that was set up with Ubuntu server 10.10. a 30gb partition for ubuntu 1.7GB for SWAP.  

When the machine boots now I get 
```
error: unknown filesystem.
grub rescue>

```
and
```

ls 

```
here gives me
```

(hd0) (hd0,msdos5) (hd0,msdos1)

```


When I use a ubuntu boot cd I can get to CLI and
```
fdisk -l
``` 
shows
```
Disk /dev/sda: 1000.2 GB, ....

Device Boot Start End Blocks ID System
/dev/sda1 * 1 32 248832 83 Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2  32 121602 976510977 5 Extened
/dev/sda5  32 121602 976510976 8e Linux LVM

``` 

Please let me know if I can post more info.  Thanks in advance.

---

### Post by steez on 2011-05-06
I have tried this
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

And now i can get to GNU GRUB 1.98

its now
grub>
instead of 
grub rescue>

---

