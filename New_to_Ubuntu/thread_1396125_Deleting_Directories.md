---
title: "Deleting Directories?"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by Howard Roark on 2010-02-01
I was doing a viral scan and came across a possible infection *virus scanner* told me that it had to be removed manually. I went in to terminal typed in the files' name and was told that it is a Directory. I know that the *rm* command is very useful for files but not so effective against directories. Any suggestions as to weather or not I want to remove the whole Directory and how to do it.
Thanks

---

### Post by howefield on 2010-02-01
> **Howard Roark said:**
> Any suggestions as to weather or not I want to remove the whole Directory and how to do it.
Thanks

Without you telling us what folder it is, or anything else :)

Post a screenshot of the warning ?

---

### Post by chaanakya_chiraag on 2010-02-01
If you want to remove the directory, use
```
rm -r
```, not ```
rm
```

---

### Post by dondiego2 on 2010-02-01
> **Howard Roark said:**
> I was doing a viral scan and came across a possible infection *virus scanner* told me that it had to be removed manually. I went in to terminal typed in the files' name and was told that it is a Directory. I know that the *rm* command is very useful for files but not so effective against directories. Any suggestions as to weather or not I want to remove the whole Directory and how to do it.
Thanks


rm -r 

will remove directories but like the previous poster said, I would be very careful before I did this.

---

### Post by Howard Roark on 2010-02-01
Sorry, /home/linda/.mozilla/firefox/15zf8ris.default/Cache/

---

### Post by pararoly on 2010-02-01
```


man man


```

and

```

man rm

```

are your friends :-)

Best wishes
roly

---

### Post by howefield on 2010-02-01
> **Howard Roark said:**
> Sorry, /home/linda/.mozilla/firefox/15zf8ris.default/Cache/

Firefox stores bits of the webpages that you visit in there, to speed up subsequent visits to that page. It is in your home folder, so you should be able to open file manager and navigate to that folder and delete the contents.

Go to Places > Home folder, and press the ctrl + H keys together, this will show the hidden files/folders, (signified with the period in front of the file/folder name. Navigate to the folder and delete as required., you shouldn't need to delete the folder itself.

---

### Post by blur xc on 2010-02-01
```
rm -r
```will removed the directory, and any directories and/or files that are in the directory.  It's dangerous.  

```
rm -rf
```is even more dangerous, as the f option forces removal of all files, w/ no warnings.

```
rmdir
```only removed empty directories.  If the directory contains anything, it will throw an error.

The safe (but slow-ish) way would be to ```
rm *
``` the contents of the directory, then ```
rmdir
``` the directory.

Imagine your are trying to remove the directory ~/somedir/dumbdir/garbage (just the subdirectory garbage and it's contents), and you get as far as "rm -rf ~/" and you accidentally press enter.

You would be hosed.

I've read suggestions from some places that it's better to enter the command 
```
rm <dirname> -rf
```(Just tested it, and it works, must make it a habit)

At least that way if you accidentally hit enter part way through entering your path, nothing would happen, and rm can't remove a directory w/o the -r flag.

BM

---

### Post by wojox on 2010-02-01
You could also download bleachbit which will purge these and other files for you as well.

```
sudo apt-get upgrade && sudo apt-get install bleachbit
```

---

### Post by sandkernel on 2010-02-01
If you want to remove the /home/linda/.mozilla/firefox/15zf8ris.default/Cache/ directory and all of its contents then:

cd /home/linda/.mozilla/firefox/15zf8ris.default
rm -Rf ./Cache

---

