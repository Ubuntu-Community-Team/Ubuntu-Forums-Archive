---
title: "Have new kernel but no grub entry"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by sunwatcher on 2010-06-07
I recently updated my machine which gave me a new kernel.  Unfortunately, grub (grub2?) menu still has older kernel, but not the newer one.  Can I add the new kernel to the grub menu?  I'm pretty much a newbie running 9.04.

---

### Post by mbzn on 2010-06-07
try:

sudo update-grub

---

### Post by LowSky on 2010-06-07
how did you install the new kernel?

you could try to run this from terminal

sudo update-grub

---

### Post by sunwatcher on 2010-06-07
I installed the new kernel via update manager.  Using sudo update-grub in terminal gave this:
[INDENT]Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-19-generic
Found kernel: /boot/vmlinuz-2.6.28-18-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done[/INDENT]

Then checking /boot/grub/menu.lst gives this:
[INDENT]title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 9.04, kernel 2.6.28-18-generic
uuid		df799ad9-c5f8-4b2f-947a-a494a55672b3
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=df799ad9-c5f8-4b2f-947a-a494a55672b3 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid		df799ad9-c5f8-4b2f-947a-a494a55672b3
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=df799ad9-c5f8-4b2f-947a-a494a55672b3 ro  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		df799ad9-c5f8-4b2f-947a-a494a55672b3
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=df799ad9-c5f8-4b2f-947a-a494a55672b3 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		df799ad9-c5f8-4b2f-947a-a494a55672b3
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=df799ad9-c5f8-4b2f-947a-a494a55672b3 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, memtest86+
uuid		df799ad9-c5f8-4b2f-947a-a494a55672b3
kernel		/boot/memtest86+.bin
quiet
[/INDENT]

I am puzzled.

---

### Post by Irony on 2010-06-07
When you get to the grub screen press e for edit and replace 18 with 19 and see if it boots.

If it does delete kernel 13 and do;

```
sudo update-grub
```

---

### Post by sunwatcher on 2010-06-07
Sorry, really a newbie at this.  I pressed e which took me to another menu and then prompts expecting me to input something. I have no idea what to input.

---

### Post by oldos2er on 2010-06-07
You need to add a stanza to your menu.lst referencing the new kernel. Run ```
gksu gedit /boot/grub/menu.lst
```, and add 

title Ubuntu 9.04, kernel 2.6.28-19-generic
uuid df799ad9-c5f8-4b2f-947a-a494a55672b3
kernel /boot/vmlinuz-2.6.28-19-generic root=UUID=df799ad9-c5f8-4b2f-947a-a494a55672b3 ro quiet splash
initrd /boot/initrd.img-2.6.28-19-generic
quiet

Save and exit, reboot, and you should be able to boot from the new kernel.

---

### Post by Irony on 2010-06-07
> **sunwatcher said:**
> Sorry, really a newbie at this.  I pressed e which took me to another menu and then prompts expecting me to input something. I have no idea what to input.

When you get to the grub screen press e for edit and replace 18 with 19 and see if it boots. Use the arrow keys to move the cursor and replace 18 with 19.

---

### Post by Irony on 2010-06-07
> **oldos2er said:**
> You need to add a stanza to your menu.lst referencing the new kernel. Run gksu gedit /boot/grub/menu.lst
Grub 2 does not have a menu.lst any new entries can be added to gksudo gedit etc/grub.d/40_custom and then running sudo update-grub.

---

### Post by oldos2er on 2010-06-07
> **Irony said:**
> Grub 2 does not have a menu.lst 

Indeed; I've seen no evidence the OP is using grub2, but rather s/he's using grub legacy. Perhaps the OP could clarify.

---

### Post by Irony on 2010-06-08
> **oldos2er said:**
> Indeed; I've seen no evidence the OP is using grub2, but rather s/he's using grub legacy. Perhaps the OP could clarify.
Actually you were right in the first place it seems the OP is using grub1 because it says;

```
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
```

So adding the following entry like you said should solve the OP problem;
```

title Ubuntu 9.04, kernel 2.6.28-19-generic
uuid df799ad9-c5f8-4b2f-947a-a494a55672b3
kernel /boot/vmlinuz-2.6.28-19-generic root=UUID=df799ad9-c5f8-4b2f-947a-a494a55672b3 ro quiet splash
initrd /boot/initrd.img-2.6.28-19-generic
quiet
```

---

### Post by sunwatcher on 2010-06-10
Yes, I am using grub legacy.  I added the entry to menu.lst and all works fine now.  Problem solved.  Many thanks everyone.

---

