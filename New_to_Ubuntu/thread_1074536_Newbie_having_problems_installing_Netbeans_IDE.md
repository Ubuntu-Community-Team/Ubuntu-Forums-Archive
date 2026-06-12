---
title: "Newbie having problems installing Netbeans IDE"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by prometheus1981 on 2009-02-19
Hello,
I have Ubuntu 8.04 installed on a PC at home. I wanted to install Netbeans IDE in this machine, but since my wireless card is fried I tried downloading it from my windows pc and then trying to install it locally. The file is a .sh, and when I try to install it in my computer it reads that it could not open the file. I have since tried to re-download the installer and try again (thinking that it was corrupt) but I keep getting the same result. I have tried to install it using the GUI. What is the command to use in terminal to get this going? I have the installer in a CD.

Thanks for your help world!

---

### Post by taurus on 2009-02-19
What is the exact command that you ran to install it?  Copy the file to your $HOME first and then run it with

```
chmod +x filename.sh
sudo ./filename.sh
```
Replace filename with the actual name of the file.

---

### Post by konqueror7 on 2009-02-19
also, try to temporary disable compiz when installing, sometimes it malfunctions (give you a blank frame)...

---

### Post by superprash2003 on 2009-02-19
do you have sun java already installed?

---

