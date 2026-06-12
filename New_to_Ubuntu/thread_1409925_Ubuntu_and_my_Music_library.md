---
title: "Ubuntu and my Music library"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by skawars on 2010-02-18
First of all a bit background. I had Windows 7 installed, shrunk the DH and installed the latest Ubuntu 32bit on the 17gig or so I free'd up.

It seemed I had solved accessing all my music (which is on the windows partition, almost everything else is external), using NTFS config tool or something along them lines, I just had to enter my admin password to mount it? (this is all pretty new to me as you can probably tell)

It seems I'm having problems using my music collection day in day out. I'm pretty happy with Rhythmbox, and it managed to import the collection pretty easily, but with other software (Amarok/Songbird) it seemed impossible to find my music as it wasn't on the root drive.

Also when I was first setting up Ubuntu I dragged my old Documents, Videos, Pictures and Music into the my places sections, and it seemed to be worked perfectly, but it seems this goes back to how it was with each restart. As I some of the folders are on my external, and the music on the windows partition.

Is there any way I can get Ubuntu to remember to mount my windows drive each time, or is this impossible without creating another impartial Fat32 partition?

Cheers
dan

---

### Post by coalitians on 2010-02-18
There is a file called fstab is /etc which is used to mount ntfs,fat or any type into ur linux filesystem (i.e) it mount's automatically during startup.

```
sudo gedit /etc/fstab
```

now add the line

```
/dev/sda3 /home/mountpoint ntfs user,rw 0
```

and restart 

Note: you have to modify /dev/sda3 into the drive you want to mount 
i.e somefolks will have /dev/hda4 etc. 
/home/mountpoint can be modified into the folder you want to mount the filesystem 
ntfs can be set into fat etc. based ou your filesystem you are trying to mount

---

### Post by skawars on 2010-02-18
Hi, cheers for the advice. I think I've got this sorted through a combination of your own advice and some messing on with NTFS configuration tool.

Dan

---

