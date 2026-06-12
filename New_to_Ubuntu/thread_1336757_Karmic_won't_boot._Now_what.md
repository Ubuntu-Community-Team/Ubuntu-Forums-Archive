---
title: "Karmic won't boot. Now what?"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by Nikkiru on 2009-11-24
I just installed Karmic on an old hard drive which previously had Windows on it, as the sole OS on that disk. After clicking the GRUB option to load ubuntu 9.10,  this error message came up:

> error: no such device:  d26c351b-b601-4cb3-83f2-1d208a6a877f

[indent]Failed to boot default entries[/indent]

Press any key to continue ...

Any ideas?

---

### Post by rexh on 2009-11-24
try booting again as the computer is booting hit the shift key and that should take you to the grub2 menu.  Once there press "e" to do a temp. edit of the grub menu.  Find the line in the boot menu that starts with the word "search" go to the end of that line and use the backspace key to delete it.  Press CNTL X to boot.
That should let you boot, but it is a one time fix.  If it works there is a more perm.fix that is a lot more involved.

---

### Post by doas777 on 2009-11-24
it's saying that it can't find the partition that it is looking for (the one that has a uuid equal to the long hex string in your error message).
I would probably boot from a live cd, open a terminal, and run
```

ls -l /dev/disk/by-uuid

``` 
to see if the uuid is listed there. if it isn't, but you show the right number of devices, then you need to find out which id is your current os disk.

---

### Post by Nikkiru on 2009-11-24
> **doas777 said:**
> it's saying that it can't find the partition that it is looking for (the one that has a uuid equal to the long hex string in your error message).
I would probably boot from a live cd, open a terminal, and run
```

ls -l /dev/disk/by-uuid

``` 
to see if the uuid is listed there. if it isn't, but you show the right number of devices, then you need to find out which id is your current os disk.

I booted by the method rexh suggested. Here's what came up in the terminal:

> nikkiru@nikkiru-laptop:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2005-08-04 04:41 9e44140d-857a-493a-befe-05386e070928 -> ../../sda5
lrwxrwxrwx 1 root root 10 2005-08-04 04:41 d26c351b-b601-4cb3-83f2-1d208a6a877f -> ../../sda1
nikkiru@nikkiru-laptop:~$ 


Does that tell you anything?

---

### Post by doas777 on 2009-11-24
> **Nikkiru said:**
> I booted by the method rexh suggested. Here's what came up in the terminal:



Does that tell you anything?

well, it tells me that the hdd grub couldn't find is there and visible to the livecd. not sure where that leaves you,but i'm glad you didn't lose any data.

---

### Post by rexh on 2009-11-25
Here is a more "permanent" temporary solution, It was sent to me by drs305. If you do this you can boot your computer until you update Grub2, then you have to do it again. drs305 sent me some other options as well but I have not found the time to try them yet. I am and a newbie and have no real knowledge of the Grub code. Anyway here is the code, open a terminal:
 
sudo chmod +w /boot/grub/grub.cfg # makes writable
sudo cp /boot/grub/grub.cfg /boot/grub/grub.cfg.old
gksu gedit /boot/grub/grub.cfg
 
Place a comment in front of the "search" lines.
 
Save the file

---

### Post by Nikkiru on 2009-11-25
> **rexh said:**
> Here is a more "permanent" temporary solution, It was sent to me by drs305. If you do this you can boot your computer until you update Grub2, then you have to do it again. drs305 sent me some other options as well but I have not found the time to try them yet. I am and a newbie and have no real knowledge of the Grub code. Anyway here is the code, open a terminal:
 
sudo chmod +w /boot/grub/grub.cfg # makes writable
sudo cp /boot/grub/grub.cfg /boot/grub/grub.cfg.old
gksu gedit /boot/grub/grub.cfg
 

I'm pretty sure I'm more of a newb than you are. ;)

I find the above  understandable enough, but this part has me scratching my head:

> Place a comment in front of the "search" lines.
 
Save the file

How do you do this?  What does this "comment" consist of, and how do you save it as a file?

---

### Post by doas777 on 2009-11-25
a comment char is '#'
#this is a commented line
this is an uncommented line

just open your file, add a # to the beginning of the line you wish to comment out, and then save.


with grub2, the procedure has changed a little. 
instead of editing /boot/grub/grub.cfg, you want to modify
```
/etc/default/grub
```then after your changes are made, run
```
update-grub
```, and it will move your configuration into the /boot location.
then reboot.

---

### Post by Nikkiru on 2009-11-25
Thanks. When I get home, I'll try it out and report back. :)

---

### Post by rexh on 2009-11-25
The best solution I have found is post number 66 of the following thread:


[http://ubuntuforums.org/showthread.php?t=1321712](http://ubuntuforums.org/showthread.php?t=1321712)



It should work even if you update Grub2.

---

