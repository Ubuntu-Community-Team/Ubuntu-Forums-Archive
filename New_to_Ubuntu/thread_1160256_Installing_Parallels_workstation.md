---
title: "Installing Parallels workstation"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by Leshinsky on 2009-05-15
Hey,  i was told Parallels workstation is a good program to run a windows desktop in ubuntu.  I downloaded the program.  when i use the package installer to install it the program will install but not config.  then i cant find a icon anywhere for it.  so i looked up the pdf at [http://www.parallels.com/download/workstation/](http://www.parallels.com/download/workstation/) to figure out how they say to install it.  i followed their recmondations on page 8 of the linux manual and got this in my terminal window.  you can see what i did. 

matthew@ubuntu:~$ dpkg -i Parallels-2.2.xxxx-Lin.deb
dpkg: requested operation requires superuser privilege
matthew@ubuntu:~$ cd Desktop
matthew@ubuntu:~/Desktop$ dir
Parallels-2.2.2222-lin.deb
virtualbox-2.2_2.2.2-46594_Ubuntu_jaunty_i386.deb
xTuple-3.2.2-linux-installer(2).bin
xTuple-3.2.2-linux-installer.bin
matthew@ubuntu:~/Desktop$ dpkg -i Parallels-2.2.xxxx-Lin.deb
dpkg: requested operation requires superuser privilege
matthew@ubuntu:~/Desktop$ su
Password: 
root@ubuntu:/home/matthew/Desktop# dpkg -i Parallels-2.2.xxxx-Lin.deb
dpkg: error processing Parallels-2.2.xxxx-Lin.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 Parallels-2.2.xxxx-Lin.deb
root@ubuntu:/home/matthew/Desktop# 


What am i doing wrong.  can anyone help me or am i a lost puppy and i should just stick with windows.

---

### Post by kanikilu on 2009-05-15
Why are you using "xxxx" instead of the actual filename?

Use your regular account with sudo (not su) and try:

```
sudo dpkg -i Parallels-2.2.2222-lin.deb
```

Or for a graphical install, right-click on the deb file and choose "Open with Gdebi Package Installer", or run:

```
gdebi-gtk Parallels-2.2.2222.lin.deb
```

---

### Post by Leshinsky on 2009-05-15
Ok i tried that and got this error message.  i have cut and pasted it here from my terminal window

matthew@ubuntu:~$ sudo dpkg -i Parallels-2.2.2222-lin.deb
[sudo] password for matthew: 
dpkg: error processing Parallels-2.2.2222-lin.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 Parallels-2.2.2222-lin.deb
matthew@ubuntu:~$

---

### Post by Leshinsky on 2009-05-18
Any ideas i need a program that i can run my existing windows over ubuntu so i dont have to keep restarting my computer.  sadly enough i tried wine and it didnt work for all of the programs.  and this program does not seem to want to install (see last reply)

---

### Post by Dgurion on 2009-05-18
If you type in "dir" into the terminal window. Does it list the parallels.deb file?

If it does. Try ```
sudo dpkg -i Parallels*.deb
```

---

### Post by pspsampsp on 2009-05-18
couldn't you try something like virtualbox ( i think its what your looking for [http://www.virtualbox.org/](http://www.virtualbox.org/)) if you want to install it in ubuntu  just search it in add remove.

---

### Post by Leshinsky on 2009-05-18
matthew@ubuntu:~$ dir
Desktop    examples.desktop      LimeWire  Pictures  Templates
Documents  Firefox_wallpaper.png  Music     Public    Videos
matthew@ubuntu:~$ 



i downloaded it i dont know where it went

---

### Post by Dgurion on 2009-05-18
Its most likely on the desktop..

type in ```
cd Desktop
```

then try typing ```
dir
```

---

### Post by WhiskyChris on 2009-05-18
The error message you report

```
matthew@ubuntu:~$ sudo dpkg -i Parallels-2.2.2222-lin.deb
[sudo] password for matthew:
dpkg: error processing Parallels-2.2.2222-lin.deb (--install):
cannot access archive: No such file or directory
```

implies that pdkg can't find the file at all and doesn't even get started on installing it.

Originally, you changed to the desktop to try to install the file:

```
matthew@ubuntu:~$ cd Desktop
matthew@ubuntu:~/Desktop$ dir
Parallels-2.2.2222-lin.deb
virtualbox-2.2_2.2.2-46594_Ubuntu_jaunty_i386.deb
xTuple-3.2.2-linux-installer(2).bin
xTuple-3.2.2-linux-installer.bin
```

but then I believe it failed because you typed the filename incorrectly (as quoted above filename ends "...lin.deb"; you went on to try to install "...Lin.deb" with a capital L).

If this is the problem then the following steps should work, first open a terminal, then type the following commands:

```
cd Desktop
```
to move to your desktop directory

```
sudo dpkg -i Parallels-2.2.2222-lin.deb
```
as provided by kanikilu to do the business.

"sudo" will give you temporary superuser access in order to install the package

NOTE: if you type "sudo dpkg -i Par" and then simply press 'Tab', the filename should complete for you.

---

