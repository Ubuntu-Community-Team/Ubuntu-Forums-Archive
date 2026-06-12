---
title: "cannot execue ./program"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by piolinve11 on 2010-03-26
Hello, I am new using Ubuntu. I have installed a program that runs using ./program
I have used this program before under Suse and Fedora successfully (now I am trying Ubuntu for the first time). The program is usually installed as superuser using  tar -zxvf  program.tar.tgz -P, and then run using ./program from a terminal window. I typed sudo ar -zxvf  program.tar.tgz -P. The required files were written to the right directories and the exceutable is now placed on my desktop. I verified the permissions were OK to execute and by typing: sudo chmod 755 program. Then I typed the: sudo ./program and I keep getting the message: 
sudo: unable to execute ./program NO such file or directory. (I was running the terminal window from the desktop, and If I do ls the file IS there)
If I type ./program  I get: bash:./program No such file or directory
Double clicking directly on the file wont run.
Please help

Piolin

---

### Post by juancarlospaco on 2010-03-26
Open a Terminal and do sudo su

Drag and Drop the file on the Terminal, and press ENTER

*Is easier if you search the .deb of that Program*

---

### Post by Drenriza on 2010-03-26
try
#1
```
sudo su - root
``` 
#2
```
/home/username/Desktop
```
#3
```
./program
```

---

### Post by coffeecat on 2010-03-26
Is ./program a script? Have you made it executable? You may need to...

```
sudo chmod +x ~/Desktop/program
```

---

### Post by joe.beard on 2010-03-26
what is ./program, it could be that it is a script requiring a shell that is not locateable on you system and the error is coming from the shell not from your execution of it, try 

```
head -1 program
```

and see what you get, if it is a script you will have a line to execute the required shell. Check that this is actually in existence on your system.

---

