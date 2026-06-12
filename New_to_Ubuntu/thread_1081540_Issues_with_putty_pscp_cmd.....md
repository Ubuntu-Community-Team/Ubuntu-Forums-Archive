---
title: "Issues with putty pscp cmd...."
date: 2009-02-26
forum: New to Ubuntu
---

### Post by Cyked on 2009-02-26
.... to copy files from the window machine I am on to remote Ubuntu box I am connected to in putty.

Do I just have the logic incorrect?  Here is what I am trying to do and the error I get:

pscp -P #### C:\files\pics\filename.jpg username@servername:/var/www/files/pics

C:filespicsfilename.jpg: No such file or directory



Why is it hanging up on the local file I am trying to transfer?

---

### Post by geirha on 2009-02-26
You need to run that pscp command in a command prompt in windows, not in the putty session. And you don't need to be connected with putty to use pscp.

---

### Post by kanikilu on 2009-02-26
This doesn't help you with pscp, but in case you hadn't tried it, I always use [WinSCP](http://winscp.net/) when doing transfers from Windows to my Ubuntu servers...never had a problem with it.

---

### Post by Cyked on 2009-02-26
> **kanikilu said:**
> This doesn't help you with pscp, but in case you hadn't tried it, I always use [WinSCP](http://winscp.net/) when doing transfers from Windows to my Ubuntu servers...never had a problem with it.

I'm toying with the permissions as well for the www folder and how i would want to set that while I look at cmd line options.

geirha, got it figured out.  I downloaded pcsc from chiark to use.  Thanks!

---

