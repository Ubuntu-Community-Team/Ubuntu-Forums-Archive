---
title: "Download help"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by dashkowitz on 2009-05-03
[SIZE=2]Hello, I just switched from Windows to Ubuntu (YEAH!!) I' still getting accustomed to it and I'm having trouble opening downloads with archive manager. When I try to open a download I get the message - 

gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

I've tried several different files and receive the same type of error. What am I doing wrong. As I said before, I'm new to this OS so please try to keep it simple. Thanks for the help. I'm running this on a Compag Presario with the following-
[/SIZE][SIZE=2]**Microprocessor**[/SIZE]                                          [SIZE=2]1.6GHz AMD Mobile Sempron™ Processor 2800+ with PowerNow!™ Technology  [/SIZE]                                                                                    [SIZE=2]**Microprocessor Cache**[/SIZE]                                          [SIZE=2]256KB L2 Cache [/SIZE]                                                                                    [SIZE=2]**Memory**[/SIZE]                                          [SIZE=2]256MB 333MHz DDR System Memory (1 Dimm) [/SIZE][SIZE=2]
 


[/SIZE]

---

### Post by lisati on 2009-05-03
It could be anything from a "download gone bad" to a "bad file downloaded".
What were you trying to open?

---

### Post by michy99 on 2009-05-03
Sometimes this error is caused if you only have the first part of a multi-part archive.

---

### Post by dashkowitz on 2009-05-03
It was a program for observing the stars it''s called stellarium-0.10.2.tar.gz I tried downloading it three time and receive the same error. Thanks for the quick reply.

---

### Post by Volt9000 on 2009-05-03
An unexpected end-of-file error usually means the archive is corrupt, i.e. missing data.

If you can post a link to the file, we can try to open it, to see if it really is a problem with your setup, or the file itself really is corrupted.

---

### Post by cariboo on 2009-05-03
Stellarium is in the repositories, Go to System-->Administration-->Synaptic Package Manager, click the search button, enter stellarium in the search box, once the program shows up, right-click and mark it for installation. Next click apply, and wait for it to install.

---

### Post by cerealtx on 2009-05-03
```
sudo apt-get install stellarium
``` in terminal will have the same results

---

