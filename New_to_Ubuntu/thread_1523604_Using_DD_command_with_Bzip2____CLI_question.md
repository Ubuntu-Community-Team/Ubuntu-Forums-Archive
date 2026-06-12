---
title: "Using DD command with Bzip2?    CLI question"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by RichTJ99 on 2010-07-03
Hi,

I am looking to use DD to compress an entire disk (sda) to an image file on sdb.

A friend told me to mount sdb / partition 1, then as root, type the following command:

```
dd if=/dev/sda | bzip2 -9 >/media/sdb1/disk_image.img.bz2
```

This did not work.  I just get an error message:  

```
Invalid command line:  Not enough files given.  Aborting.../CODE]


I was also told to restore (assuming sda has the image & sdb is the destination), I could do the following:

[CODE]bzip2 -cd /media/sda1/disk_image.img.bz2 | dd of=/dev/sdb
```

Of course, since the first part didnt work, I couldnt test the second. 

Any ideas how to use DD to byte for byte image the entire drive & compress it (its mostly empty space).

Thanks,
Rich

---

### Post by HermanAB on 2010-07-04
Here are some ideas:
[http://www.aeronetworks.ca/netcat-howto.html](http://www.aeronetworks.ca/netcat-howto.html)

---

### Post by john newbuntu on 2010-07-04
Don't know why that happens.  Perhaps a bug with bzip2.  But as a workaround, use "gzip" instead of "bzip2 -9" and replace "bzip2 -cd" with "gzip -d"
I am assuming there is enough space in /media/sdb1 and that it is not FAT* formatted.

---

### Post by RichTJ99 on 2010-07-04
Hi,

I dont know if it matters, but the drive is formatted in NTFS.  

Thanks,
Rich

---

### Post by RichTJ99 on 2010-07-05
Hi,

You suggested using gzip instead of bzip2:

I did try that & it worked.  After the fact, I renamed the file from disk_image.img.bz2 to disk_image.tar.gz.

I then ran this command:

gzip -d /media/sda1/disk_image.img.bz2 | dd of=/dev/sdb

For some reason, it started to extract disk_image.tar into the root of sda1.  

I was hoping it would extract everything bit for bit onto sdb.

Any ideas what I missed?

Thanks,
Rich

---

