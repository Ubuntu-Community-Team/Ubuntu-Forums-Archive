---
title: "put a program in startup applications"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by LittleGyko on 2011-04-24
I wrote a code in C which will warn me when power is low by issuing the command notify-send using system(). Now I want this program to automatically run as soon as I login. So I added the executable in  
System>Preferences>Startup Applications. 

Now when I login and in the console give the command "ps -x" the program does show up. However, it is not being executed. Could someone help. 

Thanks in advance.

EDIT: The executable file sits in the directory /home/Programs. It contains a line system("acpi >> file"); Now when I try to execute this from /home I get the error "file" cannot be created : permission denied

---

### Post by mynameisnotbob on 2011-04-24
It is in wine, right?

---

### Post by LittleGyko on 2011-04-24
No

---

### Post by mynameisnotbob on 2011-04-24
Change the command to: wine [yourfilepath] (no brackets).

---

### Post by LittleGyko on 2011-04-24
Sorry. I made some mistakes in my code.

---

### Post by grahammechanical on 2011-04-24
I think that your use of the word executable is causing confusion. Let us assume that this is a binary (bin) file and not a Windows exe file. Perhaps it is a script file created in Linux for Linux. I am not an expert in this kind of thing but I ask, does this file/script have the property or permission "Allow executing file as a program?" I am also guessing that the script produces a file. Does this file have read and write permissions set?

Just some thoughts that might help but then again might be completely stupid. What do I know?

Regards.

---

