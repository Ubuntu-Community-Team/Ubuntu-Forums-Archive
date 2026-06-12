---
title: "couple of issues"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by techy_the_penguin on 2010-09-19
first i wanna say hi all.
im really excited about moving to ubuntu. i was on vista but wanted to move to something cleaner, more efiiecient, and stable. so far i love it but i have had a few problems.

im trying to figure out how to get to my files ie/ .mp3s, .jpgs, .txts, etc etc moved into linux or make a way i can get to them easily.

i tried using something called samba but didnt really know what i was doing and now i have my hard drive "mounted"(whatever that means) on my desktop. i still cant get into any of my files, but when i try to unmount it i get this message:

Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount /dev/sda2 from /media/PRESARIO_RP

also, i need to know how to make the ubuntu partition larger.


installed through wubi btw.




so........help?

thanks in advance!

---

### Post by techy_the_penguin on 2010-09-19
partially solved. figured out how to unmount the hd using a sudo command. still need help with making the partition larger and getting to my files though

and i didnt say it before, but im dual booting. i still have vista on this machine.

---

### Post by cariboo on 2010-09-19
Are the files you are trying to access on the same computer? Whether they are on a different partition or hard drive doesn't make a difference. You probably don't have permission to access the other partition/hard drive, so the easiest way would be to run the file-manager as root. To do this, press Alt-F2 and type:

```
gksu nautilus
```

Once the file-manager has opened, it's just a matter of navigating to the location of the files, and copy or move them.

Once you have moved the files to your Home directory, you still won't be able to access the files, so you will have to change the permissions and ownership. You can highlight all the files, then right-click and select properties, the rest is pretty self evident from there. This must be done while you are still running nautilus as root.

BTW Samba is only used to share file on a computer running Linux with Windows computers on the same network.

---

### Post by bcbc on 2010-09-21
Ubuntu installed using wubi can access files from the windows host under the host /host folder (Places, Computer, File system, host).

If you need more space, you're better off reinstalling. The wubi size is determined at install time and is set. (The virtual disk is root.disk). If you want to save room, you can also just access the files you want under /host rather than 'copy them over to ubuntu.'

---

### Post by mastablasta on 2010-09-21
> **techy_the_penguin said:**
>  
installed through wubi btw.
 
 
 
Also if this is true you are not dualbooting. Wubi is a virtualisation of some sort, so what you are actually doing is running Ubuntu within your Vista.
 
propper dual booting will make it all work much smoother (less erros and such) and also much faster.

---

### Post by bcbc on 2010-09-21
> **mastablasta said:**
> Also if this is true you are not dualbooting. Wubi is a virtualisation of some sort, so what you are actually doing is running Ubuntu within your Vista.
 
propper dual booting will make it all work much smoother (less erros and such) and also much faster.

No, this is a myth that is perpetuated by well-meaning community members. In fact the wubi-installed Ubuntu does not run within windows, and is not a virtual machine. It runs natively on your computer and it is true dual booting. Just it runs off a virtual disk (root.disk) that is stored on an ntfs or fat32 file system. 

It is still obviously better to run Ubuntu natively: it's faster and the virtual disk is prone to corruption - but some users like wubi because they can't or don't want to repartition their drives for a variety of reasons (or just want to try out Ubuntu and have the ability to uninstall easily if it doesn't work out). They also don't need to burn CDs or create USBs to run it - again not advisable - but that's how wubi was designed.

---

### Post by mastablasta on 2010-09-22
well either way it is still not propperly instaleld on it's own disk but rather runs as a programme on a virtual disk. waist isn't that some sort of virtualisation (not a virtual maschine though like Virtualbox)?

---

### Post by bcbc on 2010-09-22
> **mastablasta said:**
> well either way it is still not propperly instaleld on it's own disk but rather runs as a programme on a virtual disk. waist isn't that some sort of virtualisation (not a virtual maschine though like Virtualbox)?
Wubi installs Ubuntu to a virtual disk by design. Other things it is designed to do: easily install and uninstall Ubuntu from windows without the user having to repartition their disk. It is an awesome achievement. 

I think of it as the gateway drug to Ubuntu. If you want to see it in a negative light, well, fill your boots.

---

