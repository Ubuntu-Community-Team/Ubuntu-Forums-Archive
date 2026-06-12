---
title: "Problems accessing shares on Win 2K3 Server"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by Catsworth on 2007-06-13
Hi Guys,

I am running Ubuntu 6.10 on my laptop, and have a number of shares on a Win 2k3 server that I need to access.

I can mount the shares using the following at the command line:

```
mount -t cifs -o user=<username>,password=<password> //192.168.1.51/<sharename> /mnt/share/
```

However, when I do this I can create/delete files in the mounted directory but I'm not able to edit them (they are 'owned' by root.  Also, these shares are no longer mounted when I restart the laptop.

I would like the share to automount when I boot the laptop, I would also like to have full control over the files/folders within it.

Please  could somebody assist me in doing this?

Thanks.

---

### Post by moffa on 2007-06-13
You'll need to install smbfs first:

```
 sudo apt-get install smbfs 
```

Then, Edit your fstab
```
 sudo gedit /etc/fstab 
```

Append the following line

```

//192.168.1.51/<share name> /mnt/share smbfs username=<username>,password=<password> 0 0

```

---

### Post by Catsworth on 2007-06-13
> **moffa said:**
> You'll need to install smbfs first:

```
 sudo apt-get install smbfs 
```

Then, Edit your fstab
```
 sudo gedit /etc/fstab 
```

Append the following line

```

//192.168.1.51/<share name> /mnt/share smbfs username=<username>,password=<password> 0 0

```

Got it, thanks for that.

Is there any way now to stop the icons for those shares showing on the desktop?

---

### Post by Catsworth on 2007-06-13
It's ok, I got it sorted :)

---

### Post by Catsworth on 2007-06-13
In a slight departure from the original post, how would I go about creating a script that I can use to mount/unmount these drives?

I tried creating a desktop launcher with the command:

```
mount -t cifs -o user=<username>,password=<password> //192.168.1.51/<share> /mnt/<mount>/
```

.....but that didn't work.

I also tried it with sudo and gksu at the beginning, but neither of those helped either.

Anybody able to give me any pointers on this?  A desktop launcher, or a script I can double-click on would be great :)  Thanks.

---

