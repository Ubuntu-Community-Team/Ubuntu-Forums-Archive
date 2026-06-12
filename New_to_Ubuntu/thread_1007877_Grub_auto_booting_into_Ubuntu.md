---
title: "Grub auto booting into Ubuntu"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by s7alk3r91 on 2008-12-10
i just installed Ubuntu 8.10 and its not letting me boot to XP it auto loads Ubuntu on boot i think i have to edit something in my /boot/grub/ dir but i don't know what file to edit or what to put in it

---

### Post by adult swim on 2008-12-10
press alt+f2 and run ```
gksudo gedit /boot/grub/menu.lst
```
and then see if the section for timeout is set to 0, if it is youll want to change it to something else.  that number is the timer and it counts in seconds.  next youll want to look and make sure that hidden menu is not turned on.  if it is you can put a # in front of it to turn it off.  your sections would look something like this
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

```
EDIT: and for good measure lets make sure you didnt accidentally overwrite your xp install when you installed ubuntu.  what is the output of ```
sudo fdisk -lu
```

---

### Post by jimmy the saint on 2008-12-10
Please copy/paste the result of 
```
sudo parted /dev/sda print
```

---

### Post by bumanie on 2008-12-10
In terminal put in code > sudo fdisk -lu and > cat /boot/grub/menu.lst then cut and paste the output to the forum. The .lst is the letter L, not the numeral one.

---

### Post by s7alk3r91 on 2008-12-10
thanks alot it was the hidden menu i deleted that and im rebooting now i will get back to you if it worked

---

### Post by s7alk3r91 on 2008-12-10
ok i got the boot menu now but xp is not showing up 

>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   250324829   125162383+   7  HPFS/NTFS
/dev/sda2       250324830   293041664    21358417+   5  Extended
/dev/sda5       250324893   291178124    20426616   83  Linux
/dev/sda6       291178188   293041664      931738+  82  Linux swap / Solaris
paul@paul-desktop:~$ 


> Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  128GB  128GB   primary   ntfs         boot 
 2      128GB   150GB  21.9GB  extended                    
 5      128GB   149GB  20.9GB  logical   ext3              
 6      149GB   150GB  954MB   logical   linux-swap        


> ## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		b1469564-c48d-4b8d-a1b7-f639e501d05b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=b1469564-c48d-4b8d-a1b7-f639e501d05b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		b1469564-c48d-4b8d-a1b7-f639e501d05b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=b1469564-c48d-4b8d-a1b7-f639e501d05b ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		b1469564-c48d-4b8d-a1b7-f639e501d05b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b1469564-c48d-4b8d-a1b7-f639e501d05b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		b1469564-c48d-4b8d-a1b7-f639e501d05b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b1469564-c48d-4b8d-a1b7-f639e501d05b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		b1469564-c48d-4b8d-a1b7-f639e501d05b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


---

### Post by adult swim on 2008-12-10
youll need to add this to the bottom
```
title		XP
root		(hd0,0)
chainloader	+1
```

---

### Post by s7alk3r91 on 2008-12-10
ok i did that ill be back to let u know how it works

---

### Post by s7alk3r91 on 2008-12-10
ok that did the job, thanks alot, you know your stuff YOU REVIVED MY XP:lolflag: thanks alot appreciate it

---

