---
title: "Is there a alternative for Archive manager"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by sadaruwan12 on 2009-04-28
Hi,

I like to know if there a good program that could replace archive manager in ubuntu. B'cos archive manager doesn't handle some archive formats like RAR very well can any one tell me of a good replacement for that thx in advance.

---

### Post by Elfy on 2009-04-28
If you install unrar it will add rar support to file roller.

[https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

You can also install p7zip if you want

p7zip - 7zr file archiver with high compression ratio
p7zip-full - 7z and 7za file archivers with high compression ratio
p7zip-rar - non-free rar module for p7zip

---

### Post by gandaran on 2009-04-28
> **sadaruwan12 said:**
> Hi,

I like to know if there a good program that could replace archive manager in ubuntu. B'cos archive manager doesn't handle some archive formats like RAR very well can any one tell me of a good replacement for that thx in advance.
there is but I think archive manager is still the best, which rar  package have you installed for archive manager?
rar
unrar
unrar-free
if rar is installed you should have no problem with any rar file!

---

### Post by Praxicoide on 2009-04-28
Just make sure to install all the appropriate packages in order for file manager to use as a backend.

For rar, you can install unrar:

sudo apt-get install unrar

..And for .7z, you can install p7zip

sudo apt-get install p7zip-rar

(this will install rar support too)

File-roller should have the option to compress and unpack these formats.

---

### Post by sadaruwan12 on 2009-04-28
Yo HI PIXIE Thank you, I found another from linuxappfinder.com called peaszip don't whether to use it or not.:confused:

---

### Post by gandaran on 2009-04-28
> **sadaruwan12 said:**
> Yo HI PIXIE Thank you, I found another from linuxappfinder.com called peaszip don't whether to use it or not.:confused:
peazip is good but doesn't support rar files, you still are better off installing rar not unrar
```
sudo apt-get install rar
```

---

### Post by Giorgio tani on 2009-04-29
PeaZip and p7zip supports extraction of .rar archives.
Also UnRar (from RarLabs, authors and owners of intellectual property of .rar format) supports extraction of .rar, but this one is free but not Open Source.

For creation of .rar, unfortunately there is no free solution.
Rar For Linux (from RarLabs) is still commercial software.
In license.txt of the package it is stated "The RAR archiver is distributed as try before you buy" and "Following this test period of 40 days or less, if you wish to continue to use RAR, you must purchase a license", pretty much the same as for the Windows version.
Moreover, no Open Source replacement for RarLabs rar binary is possible, since it is explicitely disallowed in the license that rar/unrar descriptions, specifications, and binaries may be reverse-enginereed to build a working rar compressor from third parts.

---

### Post by sadaruwan12 on 2009-04-29
I actually want to extract .rar archives and I also like to know which compression format is best in linux or in Ubuntu.

---

### Post by hatalar205 on 2009-04-29
> **sadaruwan12 said:**
> Hi,

I like to know if there a good program that could replace archive manager in ubuntu. B'cos archive manager doesn't handle some archive formats like RAR very well can any one tell me of a good replacement for that thx in advance.

I have been using p7zip full in windows and ubuntu for more than 3 years. Up to know I haven't seen anyfile which I can not handle. I made a research on archieve programs and then I saw that there is nothing better than 7zip. It is wonderful and it is one of the initial programs I install after installing any windows and ubuntu.
I strongly advise you 7zip (but full version - in Synaptic you can find full version)

---

### Post by SuperSonic4 on 2009-04-29
> **sadaruwan12 said:**
> I actually want to extract .rar archives and I also like to know which compression format is best in linux or in Ubuntu.

Installing rar and unrar would be the easiest way to go about it.

For compressing files tarballs are usually the best - either .tar.gz , .tar.bz2 for example

---

### Post by Praxicoide on 2009-04-29
P7zip-rar has p7zip-full as a dependency, so I recommend installing this one.

---

### Post by frenchn00b on 2009-05-02
> **forestpixie said:**
> If you install unrar it will add rar support to file roller.

[https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

You can also install p7zip if you want

p7zip - 7zr file archiver with high compression ratio
p7zip-full - 7z and 7za file archivers with high compression ratio
p7zip-rar - non-free rar module for p7zip

he he 
*********  HOWTO ******* **
 
 
**1/ How to make a rar extractable for windows?**

so 
get those on megaupload 
5a74b0c8e3d35fe498d580e08e90650c *default.sfx
76ab410e2826456a9ca9a006ffea6766 *wincon.sfx
5a74b0c8e3d35fe498d580e08e90650c *windows.sfx
eeb322f1978b711140ec076fa735cb50 *zip.sfx
f53dce3ad1e2f73ccf5aa577519f1c92 *freebsd.sfx
6887d39229d11a8b063d8c9c03b0a732 *linux.sfx
4be71f85fc808ed14355ae5e2e69e9e7 *macos_x.sfx
8a70b6be524d625d17291c6d5766cced *7z.sfx
fbec918cd09e5bd955411c474d440f27 *7zCon.sfx
put that 
under /home/username/.sfx

2/ 
go to the folder where owns the file:
so type:
cp /home/username/.sfx/windows.sfx .
```
rar a -sfxdefault.sfx myexeforwindows.exe myfiledocument.doc
```

Enjoy, 

**Say thanks please !! cuz it is no where on LINUX Boards !!**


** SOLVED !!**

--
DN1NVFP0

---

