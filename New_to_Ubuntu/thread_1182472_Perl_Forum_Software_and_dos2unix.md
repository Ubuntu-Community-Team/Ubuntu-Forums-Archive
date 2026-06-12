---
title: "Perl Forum Software and dos2unix"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by gschier on 2009-06-09
Hi, I am trying to put Perl forum software on my website but all the files are in dos and need to be converted to unix.  I know of dos2unix but it only takes file input and I have about 2000 files to convert.  Does anyone have any suggestions?  Or do you know of any other free open-source forum software in perl?

Thanks

~Greg

---

### Post by cybergalvez on 2009-06-09
should be simple enough to write a bash script to feed all your files to dos2unix so you don't have to do it by hand.  I'm not very good at bash, but a python scrip is also really easy to write to do the same thing, you should be able to even write a perl script to do it too

---

### Post by ibuclaw on 2009-06-09
```
find **/path/to/directory** -type f | xargs dos2unix
```

That should convert all files in the directory.

Regards
Iain

---

