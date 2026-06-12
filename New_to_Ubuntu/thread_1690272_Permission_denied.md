---
title: "Permission denied"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by JUOKAS on 2011-02-18
Hallo, 
I downloaded a linux wersion of braid, but the thing is I cant install it.
I got this :
> root@sviestainis:/media/275 GB/OS +/Braid# chmod +x braid-linux.run.bin
root@sviestainis:/media/275 GB/OS +/Braid# ./braid-linux.run.bin
bash: ./braid-linux.run.bin: Permission denied

Any suggestions?

---

### Post by Bucky Ball on 2011-02-18
Add 'sudo' to the beginning of your commands. ;)

---

### Post by JUOKAS on 2011-02-18
I tried, but the same ' Permission denied' . I doing everything as root its shouldn't give such thing...

---

### Post by nick_goodfate on 2011-02-18
Set the root password 
> sudo passwd root
and type "su", enter the above password and then run you .bin as usual

---

### Post by Grenage on 2011-02-18
Few people would recommend logging in as root for this kind of thing, a new (or experienced) user could easily wreck their install.

What permissions does the file have?

---

### Post by JUOKAS on 2011-02-18
the files have this permits 
> ls -al
total 117608
drwx------ 1 riestainis riestainis         0 2011-02-17 21:32 .
drwx------ 1 riestainis riestainis      4096 2011-02-18 16:08 ..
-rw------- 1 riestainis riestainis 119506187 2011-02-18 15:54 braid-linux.run.bin
 
riestainis have root privileges.

---

### Post by JKyleOKC on 2011-02-18
That listing shows that the program does not have execute privileges set. Do "chmod u+x braid-linux.run.bin" while in its directory, as root, and you should then be able to run it...

---

### Post by JUOKAS on 2011-02-18
I have same problm...

> root@sviestainis:/media/275 GB/OS +/Braid# chmod u+x braid-linux.run.bin
root@sviestainis:/media/275 GB/OS +/Braid# ./braid-linux.run.bin
bash: ./braid-linux.run.bin: Permission denied


---

### Post by gandaran on 2011-02-18
> **nick_goodfate said:**
> Set the root password 

and type "su", enter the above password and then run you .bin as usual
you don't need to use 'su' in ubuntu, on ubuntu you use 'sudo' which gives you the same temporally root privileges as 'su'

---

### Post by gandaran on 2011-02-18
> **JUOKAS said:**
> Hallo, 
I downloaded a linux wersion of braid, but the thing is I cant install it.
I got this :


Any suggestions?
yes.........! 
one easy way of running any .bin file or script sh file is install the nautilus script [app runner]("http://hacktolive.org/wiki/App_Runner")

---

### Post by JUOKAS on 2011-02-18
The problem was with my hdd permittes. I coped game to another hdd and everything works fine.  
**gandaran** thanx for the app.

---

