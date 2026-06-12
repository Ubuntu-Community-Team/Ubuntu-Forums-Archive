---
title: "Generate a list of MD5 from a disc and modified date ? Is it possilbe?"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by ubfu on 2009-07-07
Is there a way to generate a list of MD5 from a disc , name of files and folder and modified date ?

Using Brasero burn application , it'll automatically create a md5sum text file to verify the data burn into the disc.Is it possible to create a md5sum from a disc again ?
I had a few dvd data disc which I wanted retrieve the md5sum , name of files /folder and date ? It had about 300 files and folder in it.

Hope someone can give step doing it.Thank you

---

### Post by ubfu on 2009-07-08
Possible to do that on a dvd disc ?

---

### Post by ubfu on 2009-07-18
Please , anyone know how to generate md5 or a program that can read every file and generate a text list to

```
File-      Size     Date created     Date Modified     Type     MD5

Form1.doc   4kb      16-Jul-2009       17-Jul-2009   Document   r28290574
Form2.doc   10kb     12-Jul-2009       14-Jul-2009   Document   ddt98093d
```

and list goes on

Any program can do this ?

Thank you :)

---

### Post by LewRockwell on 2009-07-18
[http://ubuntuguide.org/wiki/Ubuntu:Feisty/CDDVDBurning#General_Notes](http://ubuntuguide.org/wiki/Ubuntu:Feisty/CDDVDBurning#General_Notes)

.

---

### Post by jerome1232 on 2009-07-18
oops replied to wrong thread.

---

### Post by eyads on 2009-07-19
Okay, this is a tricky one, however, I'll try to patch together all my knowledge.

I will assume that our current working directory is "/media/cdrom/" and that YOUR user name is "ubfu".

1) In terminal type:

```
find >/home/ubfu/Desktop/md5checker.sh
```

then ..

```
gedit /home/ubfu/Desktop/md5checker.sh
```

Should look something like this:
```

.
./Ada_Programming_Operators.pdf
./gnat_download-2009-07-16.tar
./adadistilled.pdf
./OOP ada95.pdf
./Ada_Programming_Keywords.pdf
./A#
```

2) In gedit, delete the first "." if exists and add "#!/bin/sh". should then look like this:
```

#!/bin/sh
./Ada_Programming_Operators.pdf
./gnat_download-2009-07-16.tar
./adadistilled.pdf
./OOP ada95.pdf
./Ada_Programming_Keywords.pdf
./A#
```

3)In gedit search for: "./" replace with: "md5sum ./" , should the look like:
```

#!/bin/sh
md5sum ./Ada_Programming_Operators.pdf
md5sum ./gnat_download-2009-07-16.tar
md5sum ./adadistilled.pdf
md5sum ./OOP ada95.pdf
md5sum ./Ada_Programming_Keywords.pdf
md5sum ./A#
```

4) Save, close and in nautilus change permissions to "Allow execution as a program"

In terminal:
```
md5checker.sh >mymd5list.txt
```

5)to check files:
```
md5sum -c mymd5list.txt
```

:-k I admit, this is a ugly solution, but unless you or someone knows how's to write a complex script, this is the closest and most effortless solution I can present.

---

