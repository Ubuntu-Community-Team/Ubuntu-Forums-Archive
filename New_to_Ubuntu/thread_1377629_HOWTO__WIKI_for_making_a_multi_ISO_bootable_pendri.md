---
title: "HOWTO / WIKI: for making a multi ISO bootable pendrive with LINUX?"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-01-10
Hello 

You would like to boot any iso with your pendrive ?  Wanna boot DSL, or live ubuntu, or ubuntu installer iso?

OK, here I made a linux version for bootmyiso:

1) format the pendrive with gparted, preferably fat16 if you have compatibilities issues (eventually). Otherwise fat32 is standard. 
For console fans: 
```
cfdisk /dev/sdX
mkfs.vfat /dev/sdX1
```

2) download : [http://yellowprotoss.ye.funpic.org/website/debian_squeeze_2.4kernel/bootmyiso-linux.tar.gz](http://yellowprotoss.ye.funpic.org/website/debian_squeeze_2.4kernel/bootmyiso-linux.tar.gz) 

3) then 
 Unpack the files of  bootmyiso-linux.tar.gz  on the pendrive

```
/mnt/pendrive
mount -t vfat  /dev/sdX1  /mnt/pendrive
tar -xjvpf bootmyiso-linux.tar.gz -C /mnt/pendrive
umount /mnt/pendrive
syslinux -s  /dev/sdX1
syslinux  /dev/sdX1 
```

4) Boot and select the ISO you would like to boot from your just made bootable pendrive: 
or modify the menu on the pendrive




Example of menu.lst:
```
find --set-root /memtest86+-4.00.iso
map --mem /memtest86+-4.00.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)

# title Parted Magic 4.5 ISO Boot
# find --set-root /pmagic-4.5.iso
# map /pmagic-4.5.iso (hd32)
# map --hook
# root (hd32)
# chainloader (hd32)

# title Test ISO
# find --set-root /testname.iso
# map /testname.iso (hd32)
# map --hook
# root (hd32)
```


-
you can get inspired with this [page]("http://yellowprotoss.ye.funpic.org/website/debian_squeeze_2.4kernel/install_debian.html")

---

### Post by cariboo on 2010-01-10
Your links are broken.

---

### Post by frenchn00b on 2010-01-10
> **cariboo907 said:**
> Your links are broken.

thanks cariboo 
Oh yes, what not reliable is my ftp provider, because it says often:
```
No suitable nodes are available to serve your request.
```

I made a mirror of bootmyiso-linux.tar.gz: [here]("http://depositfiles.com/files/7gslfpkjg")
[here2]("http://rapidshare.com/files/333400218/bootmyiso-linux.tar.gz.html")
MD5: D2AD161FB6983E03E568DA88CE5DEF25 

Oh man, I should find a good ftp with php provider website (free), any good advice?

---

