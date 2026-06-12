---
title: "sis mirage 3 771 driver error"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by Delta_X on 2010-02-18
hey I have downloaded over 20 sis 771 drivers but all give me an error

Wrong architecture 'i386'

can somebody please help??](*,)

---

### Post by gordintoronto on 2010-02-18
Did you try Administration/Hardware drivers?

I assume you are running Ubuntu 9.10 64-bit?

---

### Post by MichealH on 2010-02-18
I have the 64 bit driver Just have to find it

---

### Post by MichealH on 2010-02-18
Right here it is :D

Copy sis671_drv.la and sis671_drv.so to /usr/lib/xorg/modules/drivers/

Then copy the xorg.conf to /etc/X11

If it wont let you copy anything run in a terminal: 

```
gksu nautilus
```


Download: [https://dl-web.dropbox.com/get/sis671.tar.gz?w=287d8961&dl=1](https://dl-web.dropbox.com/get/sis671.tar.gz?w=287d8961&dl=1)

NOTE: You can only go up to 1200x800

---

### Post by Delta_X on 2010-02-19
yes i am running the 64-bit edition and i have tried the hardware updates but still no luck...
[MichealH]("http://ubuntuforums.org/member.php?u=883491") i cannot download the driver from dropbox it gives me a 403 error

---

### Post by 3rdalbum on 2010-02-19
I thought SiS graphics drivers were included in a default Ubuntu install? Not that SiS is very good anyway.

---

### Post by MichealH on 2010-02-19
> **Delta_X said:**
> yes i am running the 64-bit edition and i have tried the hardware updates but still no luck...
[MichealH]("http://ubuntuforums.org/member.php?u=883491") i cannot download the driver from dropbox it gives me a 403 error

oh well I will attach the file when back on pc

---

### Post by MichealH on 2010-02-19
Here you lot go:
[http://jump.fm/GSQXU](http://jump.fm/GSQXU)                                                         -sis671.tar.gz
[URL="http://www.2shared.com/file/11507049/eb8d5df5/flash.html"]
http://www.2shared.com/file/11507051/fc4de486/sis671install.html[/URL]   -sis671installer (Run in terminal)

You may have problems with flash so here is a script

[http://www.2shared.com/file/11507049/eb8d5df5/flash.html](http://www.2shared.com/file/11507049/eb8d5df5/flash.html) -flash install (Run in Terminal)

*NOTE* To run in terminal Double click and Click Run in terminal

***NOTE2** To install the sis drivers you must put the installer in the directory you extracted the files in.

---

### Post by Delta_X on 2010-03-01
The drivers don't work they give me a "no devices found" error can anybody help I think its the xorg.conf file that i need

---

