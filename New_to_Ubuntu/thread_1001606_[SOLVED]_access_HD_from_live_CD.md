---
title: "[SOLVED] access HD from live CD?"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by minsf on 2008-12-04
hi,
how do i access my files on the HD when booting from live CD?
i can see that the HD is mounted at /dev/sda1 (using a df command in the CLI for instance) but when i try to cd to this location (or use nautilus) i get an error ("cannot access /dev/sda: not a directory").
sorry if this is basic- i'm a newbie
thanks for your advice :)

---

### Post by Michael.Godawski on 2008-12-04
> Launch the live CD. Then, type this in a terminal
     ```
sudo fdisk -l 
```
 It'll show you what your partitions are called and what type they are. Let's assume, for the sake of argument, that your /home folder lives on /dev/hda3. 
     ```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/hda3 /ubuntu 
```
 Now there will be a "directory" in /ubuntu that will have your old installation and /home folder in it.taken from
[http://ubuntuforums.org/showthread.php?t=79284](http://ubuntuforums.org/showthread.php?t=79284)

---

### Post by minsf on 2008-12-04
thanks!
this makes sense. however, i was not sure where to find the types in the output of the fdisk command. hence i am not sure what to write in the mount command after the "-t".
anyways, it seems that it is indeed in /dev/sda1/ (according to fdisk -l) and i noticed that it has been mounted (automatically) at /media/disk/
so i am able to access it from there.
new problem: after i change to /media/disk/home/username i can no longer change to this user's Document folder (the permissions are 750). i tried 
"sudo cd Documents" returns an error ("sudo: cd: command not found").
what is the correct way to invoke root permissions when changing directories?
thanks a lot!

---

### Post by minsf on 2008-12-04
ok 
i solved the permission problem with 
sudo chmod 777 Documents
then changed to it etc.
problem solved, thanks
(though, how do i see the types of the drives in the fdisk command?)

---

### Post by Michael.Godawski on 2008-12-04
> (though, how do i see the types of the drives in the fdisk command?)

Glad to hear everything is working.

What do you mean by types? Perhaps the command:
```

cat /etc/fstab
```

Will give you the information you need.

---

### Post by minsf on 2008-12-04
i guess the type is just the file system: ext3 in most cases.
the second time i booted from the live cd, the HD was not automatically mounted, so as you suggested above 
"sudo mount -t ext3 /dev/sdda1 newfolder" 
worked very nicely- thanks a lot!
i think that the type can also be found using the "sudo lshw|less" command
but like i said- ext3 worked fine
thanks for ur help

---

