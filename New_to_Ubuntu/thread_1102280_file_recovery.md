---
title: "file recovery"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by XSindy on 2009-03-21
deleted something important, with the nice shift+delete :cry:, but now I can't seem to find any recovery programs, sooo
help please :D

---

### Post by carml on 2009-03-21
You can try a SW called testdisk,which as also an utility called Photorecovery.I tried this when I was on Windows,but I don't know how to find it in Linux.:(
I found this on Google [http://ubuntuforums.org/showthread.php?t=387922,I](http://ubuntuforums.org/showthread.php?t=387922,I) hope it may help you.

---

### Post by blastus on 2009-03-21
If it's an ext3 file system and the files were recently deleted and you haven't used the file system much since you deleted the files, you can restore what you've deleted with ext3grep.

I've used ext3grep to restore deleted ext3 files and it works great. However, it's difficult to understand how to use the program (the ext3grep website is extremely technically orientated) and what's involved in restoring deleted files (i.e. what are the *stage* files and how are they created etc...) You also have to compile the application--more ugliness. ext3grep is going to be included in the Jaunty repositories so you won't have to download/compile the application with Jaunty.

[HOWTO recover deleted files on an ext3 file system](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)

The first step is to compile the application. The next step is to find the files that were deleted. To do that you should note the approximate date range when you deleted the files and then run something like this...

```
sudo ext3grep --after 1234881300 --before 1234881400 --histogram=dtime /dev/mapper/sda5_crypt

sudo ext3grep --after 1234879284 --before 1234883954 --dump-names /dev/mapper/sda5_crypt
```

Instead of /dev/mapper/sda5_crypt you would put in your device. Also, date/times are specified as Unix timestamps. To convert a date/time to a Unix timestamp you can use a calculator such as...

[Unix Time Conversion](http://www.onlineconversion.com/unix_time.htm)

So for example, the Unix timestamp 1234881300 is Tue, 17 Feb 2009 14:35:00 GMT. The --dump-names command above will list all the files that were deleted. I restored my files one-by-one with the following command...

```
sudo ext3grep --restore-file "xfree/untitled folder/temp/file.txt" /dev/mapper/sda5_crypt
```

...where the file I wanted to restore was "xfree/untitled folder/temp/file.txt"

---

### Post by mal_conductor on 2009-03-29
these are my notes on how to use testdisk and photorec to recover files.

[http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871](http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871)

---

