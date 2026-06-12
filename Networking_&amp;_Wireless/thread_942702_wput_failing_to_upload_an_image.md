---
title: "wput failing to upload an image"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by Pyro.699 on 2008-10-09
Hello,

I found a program in the depositories that resembled the wget application, wput. Ive read the documentation on it and tried to use it to upload a simple 186kb image.

> 
cody@Charmander:/var/www$ wput -nd [ftp://domain:password@domain.com](ftp://domain:password@domain.com) /var/www/background.jpg
--14:36:36-- `background.jpg'
    => [ftp://user:xxxxx@xx.xx.xxx.xxx:21/background.jpg](ftp://user:xxxxx@xx.xx.xxx.xxx:21/background.jpg)
Connecting to xx.xx.xxx.xxx:21... connected! encrypted!
Logging in as user ... Logged in!
Error: recv() timed out. No data received
Receive-Warning: read() timed out. Read '' so far.
even as i'm writing this thread the wput application is still running and *trying* to upload the file. Any ideas as to why the file is not uploading?

Thanks
~Cody Woolaver

---

### Post by yogensha on 2008-10-10
I'd try playing with passive mode with the -p option.

---

