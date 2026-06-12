---
title: "VI Editor"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by joebipp on 2009-02-18
Hi everyone I am new to Xubuntu I tried doing my 1st shell script but cannot get it to run. I tried everything according to UNIX for dummies and I can see the file is there but do not know how to bring up the files. Also noticed that the keys for moving around in vi do not match the book. I really want to learn and will keep trying till I get it right. When the world finds the time can you please take a look and see what I am doing wrong?:
joeb@joeb-laptop:~$ ls
bin  Desktop  mymenu
joeb@joeb-laptop:~$ home/mymenu
bash: home/mymenu: No such file or directory

I created the file my mymenu it shows green so it must be there.
joeb@joeb-laptop:~$ mymenu
bash: mymenu: command not found
joeb@joeb-laptop:~$ 
I tried to make the file executable using: chmod 711 mymenu
I am lost but I know I can find they way with a little help

thanks Joeb

---

### Post by Nepherte on 2009-02-18
> **joebipp said:**
> 
joeb@joeb-laptop:~$ ls
bin  Desktop  mymenu
joeb@joeb-laptop:~$ home/mymenu
bash: home/mymenu: No such file or directory

if mymenu is a file and you want to execute it, you have to type:
```
./mymenu
```
That is only on the condition that mymenu is executable. To make something executable:
```
chmod +x mymenu
```

The keys to move your cursor (besides the arrow keys), are: h j k l.

---

### Post by kellemes on 2009-02-18
> **joebipp said:**
> Also noticed that the keys for moving around in vi do not match the book. I really want to learn and will keep trying till I get it right.

Hi there, welcome to the magical world of Linux.
In order to get rid of these arrow-keys not functioning you can use "vim" instead of "vi".
If "vim" is not installed yet you can install it from a terminal window..
```
sudo apt-get install vim-full
```
This will give you "vim" to start from a terminal window, "gvim" to get some pretty graphical version **and** you'll get "evim".. this is as easy as Windows Notepad.

Good Luck.

---

### Post by joebipp on 2009-02-18
Thanks,
I tried the execute:
joeb@joeb-laptop:~$ ls
bin  Desktop  mymenu
joeb@joeb-laptop:~$ ./mymenu
bash: ./mymenu: /bin/csh: bad interpreter: No such file or directory
joeb@joeb-laptop:~$ chmod +x mymenu
joeb@joeb-laptop:~$ ./mymenu
bash: ./mymenu: /bin/csh: bad interpreter: No such file or directory
joeb@joeb-laptop:~$ 

Still does not work?
I did up setup VIM full and now got it to work> 
now just got to get mymenu to work

Thanks Joeb

---

### Post by jerome1232 on 2009-02-18
looks like it uses csh as it's shell, just install that shell and it should work, you can click this apt link or install it from synaptic.

[apt://csh]("apt://csh")

---

### Post by joebipp on 2009-02-18
Thanks,
I the shell is suppose to be C shell I tried the link it does not work.

---

### Post by kellemes on 2009-02-18
```
sudo apt-get install csh
```
should do it..

---

### Post by joebipp on 2009-02-18
Thanks!
It works I am very grateful for everyones assistance 

The Telephone Book 
 
1. Display A Telephone Number 
2. Add A New Telephone Number 
 
Q Quit 
 
Enter your selection: 
joeb@joeb-laptop:~$

---

