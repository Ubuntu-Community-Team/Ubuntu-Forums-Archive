---
title: "dual boot issues"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by dfnwpofb on 2009-01-21
Hi

absolute beginner here...

I have installed ubuntu, and only ubuntu appears in grub. can anyone help with this.

my drives are partitioned:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfda9943c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2            8027        9729    13679347+   5  Extended
/dev/sda3            5036        7389    18903040    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4            7389        8026     5116781   a5  FreeBSD
/dev/sda5            8027        9606    12691318+  83  Linux
/dev/sda6            9607        9729      987966   82  Linux swap / Solaris

Partition table entries are not in disk order

***

yeah as you can see i have freebsd, ubuntu and vista installed. 

are my partitions wrong or do i need to edit the grub menu.lst?



title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f4ad284f-658b-4df0-9733-e3235bd46f31
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f4ad284f-658b-4df0-9733-e3235bd46f31 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f4ad284f-658b-4df0-9733-e3235bd46f31
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f4ad284f-658b-4df0-9733-e3235bd46f31 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f4ad284f-658b-4df0-9733-e3235bd46f31
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST


this is all that appears in grub list, i was told to add


title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

to this list but although it now gives option to load windows it doesnt work (bootmgr missing)


as you can see i am very new but if i could get these three os's working from grub at least i could have a play around and maybe learn something :)


please help

---

### Post by Titan8990 on 2009-01-21
Change this for booting Windows:


root(hd0,0)

to:

root (hd0,2)

---

### Post by dfnwpofb on 2009-01-21
hey thanks

correct disc now but...

> **Titan8990 said:**
> Change this for booting Windows:


root(hd0,0)

to:

root (hd0,2)

aborted, 'BOOTMGR is missing'.

?

---

### Post by northern lights on 2009-01-21
> **Titan8990 said:**
> Change this for booting Windows:


root(hd0,0)

to:

root (hd0,2)

I'd agree that it appears as if your Windows was installed on the third partition (sda3), which in GRUB syntax would be (hd0,2).

However, it is most likely not as simple as altering just the *root* parameter. Windows bootloaders have a tendency to only work off the first primary partition. You will most likely also have to add the *map* command to make ntldr/vistaloader believe it's on the first partition:

```
title Windows Vista/Longhorn (loader)
map (hd0,0) (hd0,2)
map (hd0,2) (hd0,0)
rootnoverify (hd0,2)
savedefault
makeactive
chainloader +1
```

Unfortunately your Windows partition isn't even primary but a logical one - never tried that with Vista. Good luck.

---

### Post by dfnwpofb on 2009-01-21
> **northern lights said:**
> 
Unfortunately your Windows partition isn't even primary but a logical one - never tried that with Vista. Good luck.

oh dear, yeah I'll actually start over with windows on a primary partition.

thanks!

---

### Post by handydan918 on 2009-01-21
Might as well put it at hd0,0 while yer at it...

---

### Post by northern lights on 2009-01-21
> **dfnwpofb said:**
> oh dear, yeah I'll actually start over with windows on a primary partition.

thanks!
If you choose to do so, install it on the first primary partition. Even if that might mean installing another OS also.

It appears though, as if all three are installed on logical ones, as your Ubuntu (see *fdisk -l* output) can't detect the filesystem for sda1.

---

### Post by caljohnsmith on 2009-01-21
> **northern lights said:**
> 
However, it is most likely not as simple as altering just the *root* parameter. Windows bootloaders have a tendency to only work off the first primary partition. You will most likely also have to add the *map* command to make ntldr/vistaloader believe it's on the first partition:

```
title Windows Vista/Longhorn (loader)
map (hd0,0) (hd0,2)
map (hd0,2) (hd0,0)
rootnoverify (hd0,2)
savedefault
makeactive
chainloader +1
```

Unfortunately your Windows partition isn't even primary but a logical one - never tried that with Vista. Good luck.
Partition sda3 is not a logical partition, it is a primary partition. Also, you can easily boot Windows from any primary partition--Windows does not have to have to be the first primary partition. Using the above mapping syntax will not work, because the map commands remap drives, not partitions. Also, it is unnecessary to use the mapping commands when booting Windows from the first boot drive or (hd0), which is the drive Windows is currently on. 

**Amists10**, if you haven't all ready started reinstalling or changing your partitions, we should be able to get your Windows booting from Grub without having to resort to a reinstall, assuming your Windows is OK. In order to do that we'll need more info about your setup, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Windows booting problem might be.

---

### Post by northern lights on 2009-01-21
Should have watched out for blocks, missed partition table entries not being in order.

---

