---
title: "Installing savage2 .bin file"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by dsg158 on 2009-05-15
I just downloaded Savage 2 but i have no clue how to install it. I tried downloading a program to convert .bin to .iso files for wine, but it didn't work. is there an easier way to install this? 
thanks in advance.

---

### Post by marshall.robert on 2009-05-15
Unfortunately, with .bin files you have to break out the terminal.

.bin files for Linux are not like the .bin and .cue files you commonly see in Windows, it is more like an .msi file.

To install a .bin file in Linux try this in terminal.

```
cd /path/to/file.bin
chmod a+x file.bin
./file.bin
```where file.bin is the file name for the Savage 2 download.

Hope this helps.

---

### Post by dsg158 on 2009-05-15
I tried that but it says that there's no such directory. I'm really new to this. I never really messed with the terminal at all. 

Here's the file name:
  	 	 	 	 	 	  Savage2Install-1.5.0-i686.bin
Could you set it up so i can just copy and paste it? and do i input all three lines at the same time or one at a time?
thanks

---

### Post by steve101101 on 2009-05-15
is the file on your desktop. 

if it is you need to change the directory in the terminal.

cd /home/<USERNAME>/Desktop/

then run previous commands

---

### Post by dsg158 on 2009-05-15
EDIT:

i got it now. 

Thanks!!

---

