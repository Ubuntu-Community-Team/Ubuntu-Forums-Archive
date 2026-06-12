---
title: "bchunk strange file extension"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by hugstari on 2009-07-23
Hello

I just convert a bin/cue image i had to a iso image using the command bchunk filename.bin filename.cue filename
Everything seemed to be going ok except that the file extension for every file ends with a ;1 now. I am trying to get the setup working but it keeps giving me errors telling my it cant find this and that file.

[[IMG]http://img13.imageshack.us/img13/7654/ult.th.png[/IMG]](http://img13.imageshack.us/i/ult.png/)

Any ideas on what i can do?

---

### Post by hugstari on 2009-07-23
I could rename all the files one at a time but that isn't my optimal solution, there must be a simpler way.

I would also very much like to prevent something like this happening again.

---

### Post by unutbu on 2009-07-23
How are you mounting the iso image?

I know at least with CD/DVDs written in iso9660 format, if you mount the CD/DVD with the command
```

sudo mount -t udf /dev/sr0 /media/DVD # gives long filenames
```

you get long filenames. But if you mount it with the command
```

sudo mount -t iso9660 /dev/sr0 /media/DVD # gives short filenames

```
you may get short filenames. Short filenames have stuff like ";1" appended to the end of the name.

---

### Post by hugstari on 2009-07-23
Thanks your answer turned me onto the right path. I don't think i followed your advise to the point and kept getting errors because of it.I got this error,
```
sudo mount -o udf /home/user/Desktop/Ultima/ultcol/ultcol01.iso /media/cdrom0 
mount: /home/user/Desktop/Ultima/ultcol/ultcol01.iso is not a block device (maybe try `-o loop'?)

```

But then i tried some other commands that worked. I am still trying get the basics of ubuntu and all the help i can get here is great so thanks :)

---

