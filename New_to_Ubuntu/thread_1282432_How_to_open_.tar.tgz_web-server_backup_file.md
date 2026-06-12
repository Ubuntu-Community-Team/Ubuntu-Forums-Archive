---
title: "How to open .tar.tgz web-server backup file"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by greentrees on 2009-10-04
Hello all,

I am trying to extract from a .tar.tgz file.

I've taken a backup from a web-server which has created domain.com-20091004_100908.tar.tgz and I'd like to extract it's content.  I've extracted it to the desktop which has created a .tar file but can't seem to get much further one of the error messages I've seen is this...

tar: dev/null: Cannot mknod: Operation not permitted
tar: dev/ptmx: Cannot mknod: Operation not permitted
tar: dev/random: Cannot mknod: Operation not permitted
tar: dev/tty: Cannot mknod: Operation not permitted
tar: dev/urandom: Cannot mknod: Operation not permitted

gzip: stdin: decompression OK, trailing garbage ignored
tar: Child returned status 2
tar: Error exit delayed from previous errors

What am  I missing please someone ?

Thanks -GT

---

### Post by llamabr on 2009-10-04
What command are you using?  Post the entire command and it's output right in here.  Also, do a:

```
file thefile.tar
```

---

### Post by grturner on 2009-10-04
it's trying to overwrite your devices. It sounds like you've simply backed up your whole hard drive. If that is the case it may be easier to open it in gui and manually getting the files you need and reconfigure how you're backing things to only backing up your web data.

---

### Post by slakkie on 2009-10-04
Please do tar tvf archive.tar

---

### Post by greentrees on 2009-10-04
Ok I was hoping to do with this with the gui but never mind I can do command line...

terry@Hp-Linux:~/Desktop$ file domain.tar
domain.tar: directory
terry@Hp-Linux:~/Desktop$ 

##### BREAK ####

I still have the problem but it seems the Extract Here which I used initially also fails....

Ah, I've just spotted a problem with stage 1 where I have domain.tar.tgz on the Desktop and then I right click it and select Extract Here which produces "An error occured while extracting files." Clicking Command Line Output gives the exact same message that I quoted above.

It shouldn't be an "entire hd" file as it came from selecting the backup facility on a shared Linux web-server.

The last few lines of the result from tar tvf domain.tar.tgz look like this...

drwxr-xr-x user/group     4096 2009-01-19 03:48 var/www/squirrelmail/po/
drwxr-xr-x user/group     4096 2009-01-19 03:48 var/www/squirrelmail/src/
drwxr-xr-x user/group     4096 2009-01-19 03:48 var/www/squirrelmail/themes/
drwxr-xr-x user/group     4096 2009-01-19 03:48 var/www/squirrelmail/themes/css/
-rw-r--r-- user/group       65 2009-08-13 23:51 var/www/webdav.pwd
drwxr-xr-x user/group     4096 2008-02-21 11:30 var/yp/
tar: Child returned status 2
tar: Error exit delayed from previous errors

Oh, and thanks for the replies so far !

---

### Post by greentrees on 2009-10-04
Bump

---

### Post by tom66 on 2009-10-04
Open it in Archive Manager, and take out the files you need (not /dev, /var, /lib, /usr as these are system files).

---

### Post by greentrees on 2009-10-05
Thanks Tom,

Opening it in Archive Manager was the 1st thing I tried, then much googling before I came here.  Archive Manager just comes up with "An error occurred while loading the Arhive" Then Command Line output gives "tar: Skipping to next header
tar: Skipping to next header

gzip: stdin: decompression OK, trailing garbage ignored
tar: Child returned status 2
tar: Error exit delayed from previous errors"

And it doesn't show any files, I have two of these files taken at different times they both behave the same.

---

### Post by tom66 on 2009-10-05
Try "sudo file-roller NAME_OF_ARCHIVE"... 

But don't, whatever you do, extract the files into your '/' directory because you will screw your system up and turn it into a web server. (unlikely, you'll just hose it up)

---

### Post by greentrees on 2009-10-05
Hi Tom,
 
I tried that, got the same error !  SO frustrating !!!  It seems to be pointing to the possibility that (ignoring the system devices issue) both files could be corrupt.  Kindof odd that they should both have the same problem though.  I can't post them anywhere as it's not my site, someone else's oscommerce shop that got hacked.
 
-Terry

---

