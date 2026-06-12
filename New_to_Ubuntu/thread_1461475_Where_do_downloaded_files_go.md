---
title: "Where do downloaded files go"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by Vere nicolson on 2010-04-24
I am very new to Ubuntu and downloading a linux version of the Arduino IDE is not going well
 

 I have identified that I need;
 ppa:arduino-ubuntu-team/ppa  
 

 I have run the following in terminal
 

 1  
 sudo add-apt-repository ppa:arduino-ubuntu-team/ppa  
 2  
 sudo apt-get update  
 3  
 sudo apt-get install arduino  
 

 The end of the terminal message is;
 “”Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 arduino is already the newest version. 
 0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded. 
 ve@youre-laptop:~$ “”
 

 So that suggests the Arduino IDE files should be somewhere on my computer.
 I have re-run 1,2 &3 above several times
 

 But when I run;
  “”find ~/ -type f -iname arduino 
 /home/vere/.local/share/Trash/files/arduino-0017/arduino 
 /home/vere/.local/share/Trash/files/Arduino IDE/arduino-0018/arduino ””
 

 It shows the only similarly named files are in the trash.
 

 More frustrating, using nautilus I can't find the trash files.
 

 Please help me understand what I am doing wrong??

---

### Post by philinux on 2010-04-24
Update the locate database first.

```
sudo updatedb
```

then

```
locate filename
```

---

### Post by Vere nicolson on 2010-04-24
Thankyou Philinix,
That worked a treat,  Tomorrow I will try to figure out how but for now I am happy and grateful.

Cheers

Vere

---

### Post by sansor on 2010-04-24
You currently have arduino installed. If it is a regular application (I believe it is), it should be under a sub-menu under the Applications menu (On the top-left of your screen). Try looking at Applications->Accessories, Applications->Programming, ... 
If you find it, just right-click and select "Add this launcher to Desktop"

If you still can't find it, try the command 
$ arduino
from the terminal. It should start the program.

If this also doesn't work, pres Alt+F2, and write arduino. Then open the "Show list of known applications" box and see if it is there.

On the other hand, there are two tools recommended to you: find, locate. 

1) find: This tool searches through your files looking for a match. It finds a file which matches what you give to it. 

$ find "some_path" -iname "file_you_are_looking"

If you give "arduino" as "file_you_are_looking", it won't match arduino3.6 for example. In this case you can use "*" as: 
$ find / -iname *arduino*

This will match everything that has arduino anywhere in the file system. Since find starts from root directory "/", you need to type sudo before the command.

2) locate: This tool has indexes files on your computer and looks at the index to find the file you are looking for. You update the index database with 
$ sudo updatedb 
and then when you run 
$ locate "file"

it shows the where the file is. Although this tool is much faster compared to find, it's not as powerful because it doesn't support the "*" stuff. So the file name you give to it has to be the exact match.

---

