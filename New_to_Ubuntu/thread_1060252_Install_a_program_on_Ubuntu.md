---
title: "Install a program on Ubuntu"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by dragonball on 2009-02-04
Hi
My company used to use Windows in thier computers and i am trying to convince them to use Ubuntu Linux :D

But we have one problem :
the  provider of the internet for us ( in our company) use a special program to do loginning and get access to the internet..
I tried to install the program on live verion of Ubuntu but i couldnot ... can you please tell me how to install it ( on live version ) ?

Note : I attached the file

Thank you

---

### Post by jimmy the saint on 2009-02-04
Here are instructions

[http://kb.cyberoam.com/default.asp?id=372&Lang=1&SID=](http://kb.cyberoam.com/default.asp?id=372&Lang=1&SID=)

---

### Post by dragonball on 2009-02-05
Thank you so much
But i have one problem :(
i extracted the file in F partion , But i dont know how to reach F partion through terminal !!
in MS-DOS i used to write F: and press enter
what is the  equivalent in Linux :KS ??

Thank Again

---

### Post by feelshift on 2009-02-05
```
sudo fdisk -l
```
Determine which partition is your F (you should recognize it by size). Then create an empty folder, and```
sudo mount -t ntfs-3g /dev/sdaX /where/you/created/the/folder 
``` If the partition is FAT32, replace ntfs-3g with vfav. Note that /dev/sdaX must be replaced with you F partition (example: /dev/sda5 or /dev/hda3).

---

### Post by Calmor on 2009-02-05
There is no "F partition" in linux - everything is a file, and you can mount a physical partition to almost anywhere in the file structure.  For example, I have my Vista partition mounted as /mnt/Vista, so I can cd /mnt/Vista and be at what Windows would call C:\.

What command or series of clicks did you perform to extract the .tar.gz file?

Also, not to be discouraging, but before trying to do something as complex as migrating even a small company from Windows to Linux, make sure you understand both Linux and the full scope of the company's computer usage.  If you're the one pushing for the transition, everyone will be coming to you when their computer doesn't work the way they think it should (being Windows users), or when they find out a program that they need to do their job every day doesn't have an open-source alternative.

---

### Post by dragonball on 2009-02-05
Thank you feelshift for the information :)
and by the way Metallica Ruleeeeeeee

> **Calmor said:**
> There is no "F partition" in linux - everything is a file, and you can mount a physical partition to almost anywhere in the file structure.  For example, I have my Vista partition mounted as /mnt/Vista, so I can cd /mnt/Vista and be at what Windows would call C:\.

What command or series of clicks did you perform to extract the .tar.gz file?

Also, not to be discouraging, but before trying to do something as complex as migrating even a small company from Windows to Linux, make sure you understand both Linux and the full scope of the company's computer usage.  If you're the one pushing for the transition, everyone will be coming to you when their computer doesn't work the way they think it should (being Windows users), or when they find out a program that they need to do their job every day doesn't have an open-source alternative.

Calmor thank you for the great tips ;)
so there is no partion in Linux every thing is a file , but still cannot imagine how to reach a file in F: partion !! 

and about how i extracted the .tar.gz file :
1- I get the file for the internet
2- I copy the file to F: partion ( using windows )
3- I lunched Linux Ubuntu using Live CD 
4- I extracted the file by right click and select extract ( from Linux )
5- and now i am trying to Lunch it ;)

By the way my partion works in FAT32

So how to mount my partion ? is there a website or something to learn me how to  do it ?

Thank you so much

---

### Post by feelshift on 2009-02-05
This command is for mounting partitions: ```
sudo mount -t ntfs-3g /dev/sdaX /where/you/created/the/folder
```

---

### Post by Flimm on 2009-02-05
Click on Places, Computer. Your "F:" partition should be there, although it won't be called 'F:'. Double-click on it to mount it.

---

