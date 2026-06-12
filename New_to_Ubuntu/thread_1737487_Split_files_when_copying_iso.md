---
title: "Split files when copying iso?"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by cruisx on 2011-04-23
Hey guys, Iv got linux running on ps3 and im trying to copy the ISO disk to an external FAT32 drive. I was wondering is it possible to modify this command to split the file in 3.8gb chunks while its being copied? 

```
dd if=/dev/scd0 of=/media/disk/name.iso
```


THe name.iso will be copied to scd0( Or what ever my USB drive will be called correct?)

---

### Post by HermanAB on 2011-04-23
The program you are looking for is called... wait for it... drum roll... split

$ man split

will get you going.

---

### Post by cruisx on 2011-04-23
> **HermanAB said:**
> The program you are looking for is called... wait for it... drum roll... split

$ man split

will get you going.

Wait so would it be like

dd if=/dev/scd0 of=/media/disk/name.iso | split -b 3800m

Sorry first time using linux.

---

### Post by HermanAB on 2011-04-23
Hmmm, usually you need to add a dash to tell a program to read/write to/from standard input instead of to/from a file.

Something like this:

```
dd if=/dev/scd0 of=- | split -b 3800m -
```

You may have to faf around with that or google for a while to figure it out.

---

### Post by cruisx on 2011-04-23
Hmm Im just try to do some searching. 

> cd /the/directory/i/want/my/files/to/go/to
tar -cvj /full/path/to/mybigfile | split -b 650m

Going off of that. 

Could i do 

cd /dev/scd0 tar -cvj /media/disk/name.iso | split -b 3800m 

Ill experiment when i get back to linux PC.

---

