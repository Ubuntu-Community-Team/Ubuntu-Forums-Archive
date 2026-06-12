---
title: "how to use boot partition after Ubuntu installation?"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by anon0 on 2009-01-26
When I installed Ubuntu I did not use a boot partition to boot from. I've created a small partition in GParted for this purpose and marked it with the boot flag. What do I do next in order to boot from it?

---

### Post by bodhi.zazen on 2009-01-26
copy everything in your current /boot to the new partition.

Now edit fstab adding an entry to mount the new partition at /boot

Last edit /boot/grub/menu.lst to point to the new boot partition.

Which part of those general instructions do you need help with ?

---

### Post by anon0 on 2009-01-27
do you have to mount the new partition somewhere first in order to copy the current /boot to it? What I did was copying the old /boot contents to a temporary folder, mounted the new partition as /boot, then copied the temporary folder to it.

how do you edit menu.lst to point to the new boot partition? Thanks

---

### Post by bodhi.zazen on 2009-01-27
yes you have to mount the new boot partition to copy the files.

Yes, you have to update the root(hdx,y) in several places, including in the configuration sections.

---

### Post by anon0 on 2009-01-27
thanks. The bootloader doesn't recognize my new boot partition yet.

My pre-existing menu.lst entry that works is: 
```

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid	        9d94c065-4f52-4d83-84fc-fcb7f7b40ffd
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9d94c065-4f52-4d83-84fc-fcb7f7b40ffd ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

```

Since my boot partition is at sdb4, I tried this new entry:
```

title		Ubuntu 8.10, kernel 2.6.27-7-generic [root=(hd1,3)]
root            (hd1,3)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9d94c065-4f52-4d83-84fc-fcb7f7b40ffd ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

```

I didn't change the root=UUID=9d... part in kernel, because my / location has not changed.

But I get an error 22: "no such partition" upon boot up. What am I missing?

---

### Post by anon0 on 2009-01-27
- if I use the new partition's UUID, grub translates it as (hd0,3) and returns a "Error 15: File not found"
- if I use (hd1,3) which is what I think sdb4 should be, grub takes (hd1,3) and returns a "Error 22: No such partition"
- if I use the original uuid of / (sdb1), grub sees (hd0,0) which works.

I wonder if grub is treating sdb4 as (hd0,3) as opposed to (hd1,3) due to the BIOS being set to boot off IDE1 first rather than IDE0.

Also found this in the manual: "If you install GRUB into a partition or a drive other than the first one, you must chain-load GRUB from another boot loader. Refer to the manual for the boot loader to know how to chain-load GRUB."
[http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively)

---

### Post by caljohnsmith on 2009-01-27
Anon0, in order for us to get an idea of the current state of your Ubuntu installation, how about booting your Live CD, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

