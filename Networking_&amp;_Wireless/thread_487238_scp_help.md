---
title: "scp help"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by eman245 on 2007-06-28
I'm trying to transfer some files with scp. Here is the code i'm using:

scp file.txt [email]bob@xxx.xxx.xxx.xx[/email]:/home/bob

so i'm trying to send bob the file file.txt. And this works fine with file.txt, It also works fine if I replace file.txt with folder/*   .This transfers all the files within the folder. But how would I do it if I wanted to send the actual folder itself, and all its contents? I have tried to use just the folder name (folder) instead of file.txt, but i get the message:          folder: not a regular file

What i'm trying to accomplish is to move about 8gb worth of data from one machine to another. And I NEED the folder hierarchy to remain intact. How can I accomplish this with scp, or by some other method.

I have tried just sharing the folder, but have had no success...

I'm kind of a noob to linux / ubuntu so I dont really know what i'm doing. 
I'm using Ubuntu 7.04 on both machines...

-Thanks

---

### Post by milton1 on 2007-06-28
I think scp might have a -r (recursive) flag. I have used it to copy entire folders.

---

### Post by milton1 on 2007-06-28
try ```
man scp 
``` to get details on options.

---

### Post by milton1 on 2007-06-28
> **eman245 said:**
> 

scp file.txt [email]bob@xxx.xxx.xxx.xx[/email]:/home/bob



this seems redundant. using just the following:

```
bob@xxx.xxx.xxx.xx:. 
``` should put it in your home directory.

---

### Post by tagra123 on 2007-06-28
For a GUI use gftp  _(gftp can connect via ssh _-- very easy )

to install it

**sudo apt-get install gftp**


[http://packages.ubuntu.com/dapper/net/gftp-gtk](http://packages.ubuntu.com/dapper/net/gftp-gtk)

Use the* -r* switch to recurse through directories.

From a terminal

**man scp**
 
This will describe usage and all options.

---

