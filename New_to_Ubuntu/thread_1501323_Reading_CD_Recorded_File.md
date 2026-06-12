---
title: "Reading CD Recorded File"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by colintivy on 2010-06-04
Hi Folks.

I have a CD recorded on a Win Machine with an Access file which I wish to transfer to my Linux laptop and use with OOo Database/Spreadsheet. When I try to open it it says the file belongs to root, all the boxes are greyed out and I cannot see how I can change the permission to allow me to read it. The books are full of help with changing permissions to read/write to/from a HD but do not mention files. Any clues where to go?

Thanks in anticipation of help with this.

colintivy :confused:

---

### Post by kevinatkins on 2010-06-04
Where does the file currently reside? Have you moved it onto your hard drive?

---

### Post by echo.whoami on 2010-06-04
open a terminal and write

```
cd /media/cdrom0
```

then again with the cd (change directory) try to find where is the access file. when you find it write 

```
sudo cp <<thefilename>> ~/Desktop/
```

it will prompt you for a password. type the password and then 

```
cd ~/Desktop
sudo chown <<youruseraccountname>> <<thefilename>> 
```

---

### Post by colintivy on 2010-06-04
@kevin,

It is on the CDRW in my CDrom drive in laptop.

@echo.whoami,

That was quick, I will have a go later when time permits. I thought that the route was likely to be a bit involved. Tx.

colintivy :)

---

### Post by echo.whoami on 2010-06-04
i'm not sure about the /media/cdrom0 however. 

i think that you should at first type on a terminal
```
cd /media
ls 
```

then insert your disk and again 
```
ls
```

and the filename that was not there before will be your disk. type
```
cd <<filename>>
```

and it will get you in the cd.

I'm just a newbie in linux and i don't know everything so a hope that what i wrote is right. please write if something didn't work... :)

---

### Post by ajgreeny on 2010-06-04
Normally a CD will automount whan it is put in the drive.  You should then be able to simply drag the file or files to your home folder and open them.  As they have come from a CD, they may be read only, but you can change that by right clicking on the file in nautilus and in the Properties -Permissions tab, change the entry in User to **Read and Write**.

---

