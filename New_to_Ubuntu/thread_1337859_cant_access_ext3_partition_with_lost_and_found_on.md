---
title: "cant access ext3 partition with lost and found on"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by gridd on 2009-11-25
hi I have a formatted  ext 3 partition that want to use as home but the file on there says lost + found and denies me access. I've searched  a few times for an answer, but no luck. I'm  using Jaunty.please advise.

---

### Post by whoop on 2009-11-25
The lost and found dir is supposed to be there, you can access it with elevated privileges (for example):

```

sudo bash
cd /lost+found/
ls

```

---

### Post by drs305 on 2009-11-25
You can open Nautilus in admin and do what you want with it:
```

gksu nautilus 

```
That *lost+found* folder is generated when fsck is run. fsck stores "lost" bits of data there for inspection by the user if he/she chooses to do so. Deleting it will cause the folder to disappear until the next fsck is run, then it will be recreated.

You can delete if for now after checking to make sure there isn't anything in it you want - use SHIFT-DEL so it doesn't go into the root Trash bin.

---

### Post by gridd on 2009-11-25
> **whoop said:**
> The lost and found dir is supposed to be there, you can access it with elevated privileges (for example):

```

sudo bash
cd /lost+found/
ls

```
 

mike@mike-desktop:~$ sudo bash
[sudo] password for mike: 
root@mike-desktop:~# sudo bash
root@mike-desktop:~# cd /lost+found/
root@mike-desktop:/lost+found# ls

hi where do I go from there Im hopeless with terminal.

would using gparted to convert it to /home work or is there a simpler way in terminal?
I have three other os on by the way.

---

### Post by whoop on 2009-11-25
> **gridd said:**
> mike@mike-desktop:~$ sudo bash
[sudo] password for mike: 
root@mike-desktop:~# sudo bash
root@mike-desktop:~# cd /lost+found/
root@mike-desktop:/lost+found# ls

hi where do I go from there Im hopeless with terminal.

would using gparted to convert it to /home work or is there a simpler way in terminal?
I have three other os on by the way.

Creating a separate home partition is a different procedure altogether. You need to add the partition as /home in /etc/fstab.
Look here for more info:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by gridd on 2009-11-25
> **drs305 said:**
> You can open Nautilus in admin and do what you want with it:
```

gksu nautilus 

```
That *lost+found* file is generated when fsck is run. fsck stores "lost" bits of data there for inspection by the user if he/she chooses to do so. Deleting it will cause the folder to disappear until the next fsck is run, then it will be recreated.

You can delete if for now after checking to make sure there isn't anything in it you want - use SHIFT-DEL so it doesn't go into the root Trash bin.
  


thanks  that works but this came up in terminal should I ignore it

mike@mike-desktop:~$ gksu nautilus
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

I can now access the folder but how do I make it a home partition.

do I have to sort out the user share issue first?

---

### Post by drs305 on 2009-11-25
> **gridd said:**
> thanks  that works but this came up in terminal should I ignore it

do I have to sort out the user share issue first?

No, you can disregard those messages. 

The link for making a new home is in whoop's post.

Basically, you create a partition for your /home, copy your files over to it, rename the old home, and make an entry in /etc/fstab. You don't just make a folder. You make a partition, then mount the /home folder on it.

---

### Post by whoop on 2009-11-25
> **gridd said:**
> 
I can now access the folder but how do I make it a home partition.

do I have to sort out the user share issue first?

Leave this folder as it is, as it is supposed to be there.
Look here:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
on how to create a separate home partition.

---

### Post by gridd on 2009-11-25
> **whoop said:**
> Creating a separate home partition is a different procedure altogether. You need to add the partition as /home in /etc/fstab.
Look here for more info:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

thanks I knew I had seen that link  somewhere, should I be concerned about the sharing issue  or should can I ignore it sorry drs 305 was too quick for me.

---

### Post by gridd on 2009-11-25
Many thanks to you both. I shall put this as provisionally solved.

Thanks again.

---

### Post by whoop on 2009-11-25
> **gridd said:**
> should I be concerned about the sharing issue  or should can I ignore it.


If you are talking about lost+found, again: the directory is supposed to be there, its permissions are set correctly. Leave it as is and ignore it (until in the future when you might need it sometime)...

---

