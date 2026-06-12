---
title: "I can't see windows' hard drive"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by mosquetero on 2009-05-11
Hi everyone!

I had Ubuntu and Windows Vista in my computer and everything worked ok. The problem was that Ubuntu hadn't a large memory so I booted it, "stole" some memory from windows and reinstall it again. Now everything is like before but I can't see the windows hard drive!!! Before enlarging the Ubuntu memory I could but now I can't. Does anyone know what can I do to be able to enter in the windows files using Ubuntu?

Thanks

---

### Post by mosquetero on 2009-05-11
By the way!! I had the Ubuntu version 8.04, but now I have the new 9.04 version

---

### Post by Wiebelhaus on 2009-05-11
Sounds like your using Virtual box?

---

### Post by mosquetero on 2009-05-11
Virtual box?? I don't know what is it, but I haven't done anything about that.

---

### Post by halitech on 2009-05-11
By "stole" some memory, do you mean you enlarged the partition that Ubuntu is installed on?

Can you still boot into windows?

---

### Post by mosquetero on 2009-05-11
Yes. I had 11 Gb for Ubuntu and 225 Gb for Windows. After what I did I have 35Gb for Ubuntu and 201 Gb for Windows. I tried Windows and it works perfectly.

THanks for your answers

---

### Post by Wiebelhaus on 2009-05-11
> **mosquetero said:**
> Yes. I had 11 Gb for Ubuntu and 225 Gb for Windows. After what I did I have 35Gb for Ubuntu and 201 Gb for Windows. I tried Windows and it works perfectly.

THanks for your answers


Ok , that confused the heck out of me. Calling it memory 

run these commands.

```
sudo apt-get install ntfs-3g ntfsprogs
```

That is the ntfs support your seeking , cheers.

---

### Post by mosquetero on 2009-05-11
Thanks sx66gns but it still doesn't work. A message appears in the screen when I log into my account that says:

Network Service discovery disabled.

Your current network has a .local domain which is not recommended and incompatible with the Avahi network service discovery. The service has been disabled.

Maybe it is related to what is happening to me.

---

### Post by mosquetero on 2009-05-11
I did one thing which may be the cause of my problems. When I made the partitions, I wrote /windows as the mount point for the windows partition. Do you think it can be related???

---

### Post by Wiebelhaus on 2009-05-11
> **mosquetero said:**
> I did one thing which may be the cause of my problems. When I made the partitions, I wrote /windows as the mount point for the windows partition. Do you think it can be related???

Check /mnt/windows

See if anything is there..

---

### Post by mosquetero on 2009-05-11
:( windows does not exist in that folder

---

### Post by halitech on 2009-05-11
> **mosquetero said:**
> Thanks sx66gns but it still doesn't work. A message appears in the screen when I log into my account that says:

Network Service discovery disabled.

Your current network has a .local domain which is not recommended and incompatible with the Avahi network service discovery. The service has been disabled.

Maybe it is related to what is happening to me.

Look in System/Administration/Network in the General tab and see if the Automatic Service Discovery box is unchecked.

as to the windows partition, post the output of
```
sudo fdisk -l
``` and ```
cat /etc/fstab
```

---

