---
title: "Master Boot Record"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Rrasyrogenees on 2009-01-15
hey... i am still a nOOb as my signature suggests... and my head is still spinning trying to learn everything in here... i missed the basics training and even when i do try to read about the "basics" it seems to be more confusing to me...  and i do things backwards anyway and learn advanced lessons before the basics...

Ubuntu 8.10, Kernel 2.6.27-9 generic
Ubuntu 8.10, Kernel 2.6.27-9 generic (recovery mode)
Ubuntu 8.10, Kernel 2.6.27-7 generic
Ubuntu 8.10, Kernel 2.6.27-7 generic (recovery mode)
Ubuntu 8.10 Memtest86+
Other Operating Systems
Ubuntu 8.10, Kernel 2.6.27-9 generic (on /dev/sda1)
Ubuntu 8.10, Kernel 2.6.27-9 generic (recovery mode) (on /dev/sda1)
Ubuntu 8.10, Kernel 2.6.27-7 generic (on /dev/sda1)
Ubuntu 8.10, Kernel 2.6.27-7 generic(recovery mode) (on /dev/sda1)
Ubuntu 8.10 Memtest86+ (on /dev/sda1)
Ubuntu 8.10, Kernel 2.6.27-9 generic (on /dev/sdb6)
Ubuntu 8.10, Kernel 2.6.27-9 generic (recovery mode) (on /dev/sdb6)
Ubuntu 8.10, Kernel 2.6.27-7 generic (on /dev/sdb6)
Ubuntu 8.10, Kernel 2.6.27-7 generic (recovery mode) (on /dev/sdb6)
Ubuntu 8.10 Memtest86+ (on /dev/sdb6) 
Ubuntu 8.10, Kernel 2.6.27-9 generic (on /dev/sdb1)
Ubuntu 8.10, Kernel 2.6.27-9 generic (recovery mode) (on /dev/sdb1)
Ubuntu 8.10, Kernel 2.6.27-7 generic (on /dev/sdb1)
Ubuntu 8.10, Kernel 2.6.27-7 generic (recovery mode) (on /dev/sdb1)
Ubuntu 8.10 Memtest86+ (on /dev/sdb1)

is what i have and i want sdb1 to be my main boot... it is ubuntu... (kubuntu, xubuntu, and ubuntu studio are my other three)... how do i do the MBR to get me where i want to be?

and is there an answer to why people want to have dual boot with any windows os?  the closest i have now is wine...world of warcraft calls to me

---

### Post by iaculallad on 2009-01-15
If you're having a tripple boot as of the moment, you should edit your /boot/grub/menu.lst file and change the boot order from there.

Follow the guide below:

Open /boot/grub/menu.lst for editing (Terminal):

```
gksudo gedit /boot/grub/menu.lst
```

Find this line and change the default value to point to the value of your desired kernel.

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**[COLOR="DarkRed"]default         0[/COLOR]**
```

Sample values using my current menu.lst file will be:

```
## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-15-generic		**[COLOR="Blue"]<----- 0[/COLOR]**
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)		**[COLOR="Blue"]<----- 1[/COLOR]**
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro single
initrd          /boot/initrd.img-2.6.22-15-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic		[COLOR="Blue"]**<----- 2**[/COLOR]
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)		**[COLOR="Blue"]<----- 3[/COLOR]**
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+		**[COLOR="Blue"]<----- 4[/COLOR]**
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

If I want to boot on "Ubuntu 7.10, kernel 2.6.22-14-generic" as default, I would change the value of default to 2 instead of 0.

> # You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**[COLOR="DarkRed"]default         2[/COLOR]**

After you had changed it, Save and close. And while on your terminal, reboot.

```
sudo shutdown -r now
```

---

### Post by Vantrax on 2009-01-15
iaculallad that is one of the best responses I have seen so far.

Well done.

---

### Post by Rrasyrogenees on 2009-01-18
first i want to say that it was very well written (iaculallad)... and i agree that is better than i have seen so far.

that being said... i am not sure that it is explaining my situation (at least for me to understand)... i have four OSes and it does not list it in the way that is shown (as i see it and please understand too that my nOObness is showing through here)... 

the OS i want is on sdb1 as i have installed the four on sda1, sda6, sdb6, sdb1 (as in the order i showed and it shows them under "other operating systems").  

how do i get it to boot to the 2nd hd (listed as sdb1)?  i know it is not the same as a dual boot in the sense that i have a quad boot but to make only one the default boot to start up on when i start my computer... i can live with having to watch for the grub to change it at boot-up but i know you understand my desire here too.

and to say upfront... i am never unhappy with any of the explanations just unhappy with my lack of understanding what i am being told. once it finally clicks in my head i will do great... just need a crowbar to get my brain working sometimes... lol

---

