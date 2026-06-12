---
title: "cannot access hard drive data from live cd"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by guv999 on 2009-12-23
Hi
I have had a bit of a disaster tonight and the end result is that GRUB2 only lauches in resuce mode and more importantly I cannot access my hard drive.
I am using a live CD to connect and want to access my hard drive data, but it will not allow me to access it at all.
To summarise what happened:
I wanted to reformat an external HDD which I did, however it had errors and for whatever reason I ran the fsck command in the terminal reada  forum post for a similar problem).
First error was that I ran the command on my internal hard drive
Second error I killed the terminal before it completed running
When I rebooted the PC I received a grub error 'out of partition'
I then used a live CD and could not mount my internal HD at all
I did run the fsck again and it completed successfully
I am now able to mount my hard drive, however I cannot access it.  In Nautilus it only displays a 'lost and found' folder that can only be accessed by root.   
How can I do this?  
I really appreciate any help, there a few photos in the folder that would be difficult to replace.   I am not concerned about the grub error unless fixing it is the only way to access the data - I'll happily reinstall

---

### Post by taurus on 2009-12-23
You can run nautilus with root privilege and see if you can access your harddrive.

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

### Post by mapes12 on 2009-12-24
Hi

I found this thread about how to restore Grub from a LiveCD. It may help you out:

[http://ubuntuforums.org/showthread.php?t=224351&highlight=backup](http://ubuntuforums.org/showthread.php?t=224351&highlight=backup)

---

### Post by guv999 on 2009-12-25
Thanks for your help.   I did mange to retrieve the photos that were not already backed up

---

