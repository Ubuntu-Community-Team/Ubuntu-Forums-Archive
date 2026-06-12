---
title: "error no space left on device"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by aint_no_einstein on 2009-12-07
I'm trying to install Ubuntu using this [https://help.ubuntu.com/community/Installation/FromUSBStick#Prepare%20the%20USB%20Drive](https://help.ubuntu.com/community/Installation/FromUSBStick#Prepare%20the%20USB%20Drive) and every thing goes fine till about an hour into it installing then it stops and I get this 

> an error occurred 
no space left on device 
for more information please see the log file:
C:\docume~1\owner\locals~1\temp\wubi-9.10ubuntu1-rev160.logI've tried both the full install and the dual boot several times and neither of them seem to work. I know I have the right download and I know there is more then enough room on the computer for it. 
Can somebody please tell me what I'm doing wrong?

---

### Post by Merk42 on 2009-12-07
What does the log file say?
 
Also given where the log is, it appears you're installing via WUBI, are you sure that's what you want to do?

---

### Post by bhaverkamp on 2009-12-07
You should attach the log file mentioned. Did this error happen during the USB image creation or during the install. Looks to me like the image creation failed given the windows path to the log file.

---

### Post by aint_no_einstein on 2009-12-07
I don't know what the log file said because I can't find it but I may not be doing it right I'm vary new to this kind of stuff and don't really have anyone to show me.

As for the other question it comes up the same if I'm using wubi or not.

---

### Post by aint_no_einstein on 2009-12-07
> Did this error happen during the USB image creation or during the install.during the install
and i redownloded it twice

---

### Post by Merk42 on 2009-12-07
How much space are you allocating for Ubuntu?

---

### Post by aint_no_einstein on 2009-12-07
I thing I had 32GB free

---

### Post by Merk42 on 2009-12-07
That is enough space. Did you try the option "test disk for errors"?

---

### Post by aint_no_einstein on 2009-12-07
yes nothing

---

### Post by Merk42 on 2009-12-07
Are you able to do the 'try ubuntu' option?

---

### Post by aint_no_einstein on 2009-12-07
no the same thing happens

---

### Post by aint_no_einstein on 2009-12-07
bump

---

### Post by Merk42 on 2009-12-07
I'm sorry I'm out of ideas

---

### Post by Sin@Sin-Sacrifice on 2009-12-07
I would say the same thing I tell everyone using Wubi... Partition the hard drive and install it by itself. Wubi is crap IMHO. If you want help doing it that way let me know and get a pen and paper. I will guide you.

---

