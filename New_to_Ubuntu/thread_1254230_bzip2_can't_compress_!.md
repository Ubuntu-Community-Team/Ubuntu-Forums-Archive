---
title: "bzip2 can't compress !"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by colau on 2009-08-31
***file-in*** is with 36 bytes.
```

bzip2 file-in

```
After this ***file-in.bz2*** is with 56 bytes.
ls -l
```

-rwxrwxr-x 1 user1 user1  38 2009-08-31 14:48 file2-in
-rwxrwxr-x 1 user1 user1  56 2009-08-19 17:02 file-in.bz2

```

---

### Post by sahabcse on 2009-08-31
check you file name, you have done bzip2 on file-in, not file2-in

---

### Post by colau on 2009-08-31
> **sahabcse said:**
> check you file name, you have done bzip2 on file-in, not file2-in
Forgot to mention, did this first to save.
```

cp file-in file2-in

```
If i extract the file-in.bz2 , i get the **file-in** with 36 bytes.

---

### Post by sahabcse on 2009-08-31
I have done a test, bzip2 is working fine. Update your system and try.

sahab@sahab-desktop:~/Desktop$ vim test
sahab@sahab-desktop:~/Desktop$ ls -al
-rw-r--r--  1 sahab sahab  156 2009-08-31 13:00 test
sahab@sahab-desktop:~/Desktop$ bzip2 test
sahab@sahab-desktop:~/Desktop$ ls -al
-rw-r--r--  1 sahab sahab  137 2009-08-31 13:00 test.bz2

---

### Post by The Cog on 2009-08-31
If the file looks like random data then it can't really be compressed. I don't know the bzip2 format, but it might actually require more space for the flags saying "this part is not compressed..." followed by the data than the original data required. And of course, there need to be some kind of header added, which assorted bzip2 metadata.

It would never occur to me to try and compress a 36 byte file. Try with larger file sized where the compression algorithms have a better chance of finding compressible patterns in the data.

---

### Post by Liolikas on 2009-08-31
Here more explanations:
[http://www.howstuffworks.com/file-compression.htm](http://www.howstuffworks.com/file-compression.htm)

---

### Post by lisati on 2009-08-31
If you try to compress an already small file, the output file can be bigger because most compression & archiver programs include extra information in the file that lets the decompression software restore to the correct file name and with the correct file attributes & permissions.

---

### Post by HavocXphere on 2009-08-31
The file is too small to compress.

The Cog is right. Compression programs use a header which contains odds&ends that the app needs to know when decompressing, so the end result will be bigger if
```
Header + compressed(Data) > Data
```

Nothing you can do about it.:|

---

### Post by colau on 2009-08-31
Thank you all for you replies.

---

