---
title: "no space in root folder"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by Zombir on 2010-01-24
Yesterday I tried to update Ubuntu and ran into few errors and when looking around finally found out that the root folder has run out of space. I haven't got GParted in my computer and it doesn't let me to uninstall any programs at all. At the moment I feel like the greatest idiot of all, not giving enough space to the root. But  what can I do now? What can I delete to get some space?

---

### Post by jamesbannon on 2010-01-24
Try running

```
sudo apt-get clean
```

That will clean the cache and perhaps get you sufficient space back. Also try cleaning everything in /tmp, /var/tmp and /var/spool. 

This might allow you to install gparted to resize the root partition. Failing that, backup and rebuild.

---

### Post by nmccrina on 2010-01-24
You can run GParted from your LiveCD...If there's no empty space after your root partition on the disk, though, you probably would want to go into Windows and resize its partition (assuming your dual booting), then install Ubuntu again, this time using the increased space. ;) Anytime you're dealing with resizing/removing partitions, remember to backup if possible!

---

### Post by 311005901 on 2010-01-24
You also might want to run
```
sudo apt-get autoremove
sudo apt-get autoclean
```

---

### Post by CoryThompson on 2010-01-24
Ubuntu comes with a nice disk usage utility.

Go Applications -> Accessories ->  Disk Usage Analyzer
or type:
```
 baobab 
```

---

### Post by Zombir on 2010-01-25
Thanks for everybody interested. When I tried to boot Ubuntu last time I couldn't even see the graphics of it. It gave the error message 'bla bla bla possibly due to out of space'  in a shell environment and prompted me to enter the username and password. I'm not quite used to shells and was forced to chose the method of booting from the live CD and using the partition editor. This solved the problem I think. But still the effects of the previous errors in updating remain.
                       Now GRUB shows two Ubuntu OSes! (I have a dual boot system) and both loads the same OS but their names different. I opened the menu.lst file and this is what it reads:

 title        Ubuntu 8.10, kernel 2.6.27-16-generic
uuid        80f9f2d4-bb5b-49e8-ba97-03ae1a3c300d
kernel        /boot/vmlinuz-2.6.27-16-generic root=UUID=80f9f2d4-bb5b-49e8-ba97-03ae1a3c300d ro quiet splash 
initrd        /boot/initrd.img-2.6.27-16-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-16-generic (recovery mode)
uuid        80f9f2d4-bb5b-49e8-ba97-03ae1a3c300d
kernel        /boot/vmlinuz-2.6.27-16-generic root=UUID=80f9f2d4-bb5b-49e8-ba97-03ae1a3c300d ro  single
initrd        /boot/initrd.img-2.6.27-16-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        80f9f2d4-bb5b-49e8-ba97-03ae1a3c300d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=80f9f2d4-bb5b-49e8-ba97-03ae1a3c300d ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        80f9f2d4-bb5b-49e8-ba97-03ae1a3c300d
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=80f9f2d4-bb5b-49e8-ba97-03ae1a3c300d ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        80f9f2d4-bb5b-49e8-ba97-03ae1a3c300d
kernel        /boot/memtest86+.bin
quiet

note that in the 'kernal' line  the UUID part is the same for both but the number given in /boot/vmlizuz-... is different. 
Is it a good idea to erase on of them?
On the other hand when I try to open the Synaptic Package manager, it gives this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. 

and closes.
when I try to run 'sudo dpkg --configure -a' in the terminal I get the error message:

dpkg: parse error, in file `/var/lib/dpkg/updates/0105' near line 1:
 newline in field name `#padding'

Now I cannot run the package manager because it closses as above. What should I do?
Thanks

---

### Post by Paqman on 2010-01-25
> **Zombir said:**
> 
note that in the 'kernal' line  the UUID part is the same for both but the number given in /boot/vmlizuz-... is different. 
Is it a good idea to erase on of them?


Yes, it is, and it'll free up about 100MB. These are updated kernels. You'll get a new kernel occasionally in your normal updates. Just use the newest one. Assuming it works fine (and it will) you can uninstall the old ones.

---

### Post by t0p on 2010-01-25
Don't know what to suggest about your *dpkg* problems.  But as for the "2 Ubuntus" in the grub menu: that isn't 2 operating systems; grub is giving you the option to boot from the latest kernel installed or the previous one.  Don't delete one.  It's a good idea to keep a copy of the previous kernel as backup, in case the new kernel gives you problems.

In the future, once you've amassed a few kernels, you might decide to remove some.  In which case, remove them with Synaptic, as explained [here]("http://ubuntuforums.org/archive/index.php/t-459901.html"). (The thread's a little old, but still relevant.)

---

