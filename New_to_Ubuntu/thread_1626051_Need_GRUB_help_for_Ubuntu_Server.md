---
title: "Need GRUB help for Ubuntu Server"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by sseelbinder on 2010-11-19
I had a working copy of XP, added Ubuntu Server, but the install did not recognize my XP install during GRUB install.  The install indicated it could be fixed later.  I am attempting to locate the fix.  Here is what my drive looks like:

  	 	 	 	p { margin-bottom: 0.08in; }  Disk /dev/sda: 250.0 GB, 250000000000 bytes  
 255 heads, 63 sectors/track, 30394 cylinders  
 Units = cylinders of 16065 * 512 = 8225280 bytes  
 Sector size (logical/physical): 512 bytes / 512 bytes  
 I/O size (minimum/optimal): 512 bytes / 512 bytes  
 Disk identifier: 0xe686f016  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1   *           1       10199    81923436    7  HPFS/NTFS  
 /dev/sda2           10200       19926    78124033    5  Extended  
 /dev/sda5           10200       19926    78124032   83  Linux

---

### Post by sandyd on 2010-11-19
> **sseelbinder said:**
> I had a working copy of XP, added Ubuntu Server, but the install did not recognize my XP install during GRUB install.  The install indicated it could be fixed later.  I am attempting to locate the fix.  Here is what my drive looks like:

  	 	 	 	p { margin-bottom: 0.08in; }  Disk /dev/sda: 250.0 GB, 250000000000 bytes  
 255 heads, 63 sectors/track, 30394 cylinders  
 Units = cylinders of 16065 * 512 = 8225280 bytes  
 Sector size (logical/physical): 512 bytes / 512 bytes  
 I/O size (minimum/optimal): 512 bytes / 512 bytes  
 Disk identifier: 0xe686f016  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1   *           1       10199    81923436    7  HPFS/NTFS  
 /dev/sda2           10200       19926    78124033    5  Extended  
 /dev/sda5           10200       19926    78124032   83  Linux

post output of
```

sudo update-grub2
```

---

### Post by sseelbinder on 2010-11-19
Found linux image: /boot/vmlinuz-2.6.35-22-server
Found initrd image: /boot/initrd.img-2.6.35-22-server
Found memtest86+ image: /boot/memtest86+.bin

---

### Post by drs305 on 2010-11-19
I don't know why it's not picking it up, but until it's figured out you could try putting the following in the /etc/grub.d/40_custom menu. Just add it below the existing lines and check to make sure it's executable. Change the areas in **[COLOR="DarkRed"]dark red[/COLOR]** to match your setup.


> menuentry "Windows" {
	insmod ntfs
	set root='(**[COLOR="DarkRed"]hd0,1[/COLOR]**)'
	search --no-floppy --fs-uuid --set **[COLOR="DarkRed"]ceecff9eecff7f51[/COLOR]**
	drivemap -s (hd0) ${root}
	chainloader +1
}


```
gksu gedit /etc/grub.d/40_custom &
sudo chmod +x /etc/grub.d/40_custom
sudo update-grub
```

---

