---
title: "totally stuck tried all for cairo dock"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by hollowtd on 2009-07-28
I"ve got cairo dock now on my macbook using jaunty. I've done all sorts of research and even typed in the terminal to get the plugins. Even all the mispellings. I've got now the cairodock plugins 2.0.8 tar.bz2 box on my desktop. There is no readme file in it once extracted. Anyone know how to get this box to work? Or, how do I get the cairo dock plugins using terminal (I've tried sudo apt-get install cairo-dock-plugins) and all variations. 

Cheers again

---

### Post by hollowtd on 2009-07-28
really I just don't know how to run the tar.bz2 package.

---

### Post by Shazaam on 2009-07-28
Depending on what is in the tar file you usually have to compile it.
1. Open terminal.
2. cd (change directory) to where you have the tar extracted to. I extract mine to the desktop so we will use that as a location.
```
cd /home/yourusername/Desktop
```
or...
```
cd ~/Desktop
```
The capital D is important.
3. Make sure your file is there...
```
ls
```
This will list things on your desktop.
4. If the extracted folder is there cd into it...
```
cd /nameoffolder
```
5. Some apps need to be configured first, run these commands one at a time...
```
./configure
make
sudo make install
```
That should be all that you need.
A good link...
[https://help.ubuntu.com/8.10/add-applications/C/install-file.html](https://help.ubuntu.com/8.10/add-applications/C/install-file.html)

---

### Post by hollowtd on 2009-07-28
Wow, thanks for putting so much work into getting me that. After ls comes up, it opens up in red letters but there is no list. I'll check into that tomorrow but thanks for helping me out so far. Cheers

---

### Post by fabounet on 2009-07-29
why bother with the sources when you have deb packages available on the same page ?

---

