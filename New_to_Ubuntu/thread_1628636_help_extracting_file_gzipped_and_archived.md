---
title: "help extracting file gzipped and archived"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by mrpervie on 2010-11-22
Im trying to apply this theme transformation pack but archiver spits out 
"tar: This does not look like a tar archive
tar: Skipping to next header
tar: Exiting with failure status due to previous errors"


ive been googling for a while but nothing seems to help....
its not corrupt i downloaded it a few times to be sure....

i tried mounting and extracting but that was going to take ...seriously hours.....timer kept going up....any ideas?

---

### Post by yankysunny on 2010-11-22
Tar is broken I think
Redownload may help

---

### Post by mrpervie on 2010-11-22
.......i said i downloaded it a few times to be sure it wasn't corrupt

---

### Post by bananas4370 on 2010-11-22
What extension does the archive file have? Are you using the correct switches for the tar command - eg.

tar -zxvf file.tar.gz

tar -xjvf file.tar.bz2
Cheers
Patrick

---

### Post by yankysunny on 2010-11-22
[http://ubuntuforums.org/showthread.php?t=60452](http://ubuntuforums.org/showthread.php?t=60452)
Try this

---

### Post by mrpervie on 2010-11-22
oops i thought i posted the filename



Win2-7Pack_v6.1_Multilang_Aero_MD5_cfaed04cddef8bf24d73873464f2b37f.tar.lzma.tar


ok i found that in google earlier wasnt sure if it applied to me ill try it just a sec

---

### Post by bananas4370 on 2010-11-22
> **mrpervie said:**
> oops i thought i posted the filename

Win2-7Pack_v6.1_Multilang_Aero_MD5_cfaed04cddef8bf24d73873464f2b37f.tar.lzma.tar

```
sudo apt-get install lzma

unlzma file.tar.lzma
```

Cheers
Patrick

---

### Post by mrpervie on 2010-11-22
thanks fellas....although im not sure if its extracting or not....terminal inst prompting so its doing something...i think i have to tar -d file 
then lzma -d file.....


but it is still taking forever...guess there is no way around it...lzma wont extract it as it is.


any idea how to check status so i know its not just stuck?....is there a gui program i could use?

---

### Post by bananas4370 on 2010-11-22
> **mrpervie said:**
> ....is there a gui program i could use?

I believe that 7zip can extract lzma.

Cheers
Patrick

---

