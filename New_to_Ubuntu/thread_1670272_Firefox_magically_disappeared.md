---
title: "Firefox magically disappeared?"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by Mindswap1 on 2011-01-18
I guys its really strange. I was using firefox today, and noticed that these past few days its kept on crashing a lot. However after crashing today it sorta dissapeared.. If I look into the global menu section, and then internet firefox is listed. However when I click on it a message that says

> Could Not launch Firefox Web Browser. 

Failed to execute child process

"firefox" (No such file of Directory). 

However if I look into the software center it says firefox is installed. Please help.

---

### Post by dFlyer on 2011-01-18
Try this from the command line. ps -A.
Find all entries of firefox and mozilla and kill them by:
kill PID #.
Than try and start ff again.

---

### Post by Mindswap1 on 2011-01-18
I tried it, and there were no Firefox or Mozilla entries active. :/

---

### Post by DMKryl on 2011-01-18
what happens when you try to run it from terminal
just type firefox and show us the terminal output

---

### Post by wojox on 2011-01-18
Look in Main Menu aka alacarte and go to Internet > Firefox > Edit and look at what path it's using.

---

### Post by Mindswap1 on 2011-01-18
After typing in firefox I got the following. 


> The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox

After That I typed in sudo apt-get firefox and got the following. 

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



---

### Post by DMKryl on 2011-01-18
copy your bookmarks ( ~/.mozilla/firefox/(profile)/bookmarks.html.)
sudo apt-get remove firefox
restart system
reinstall firefox

---

### Post by DMKryl on 2011-01-18
-

---

### Post by BobvanderPoel on 2011-01-18
A lost or deleted link? In my ubuntu install firefox is a link in /usr/bin:

bob$ ll /usr/bin/fire*
lrwxrwxrwx 1 root root 32 2010-12-10 09:20 /usr/bin/firefox -> ../lib/firefox-3.6.13/firefox.sh*

If you have the /lib/firefox-* stuff, then you can remake the link:

cd /usr/bin/
sudo ln -s ../lib/firefox-3*/firefox.sh

should do it :)

---

### Post by Mindswap1 on 2011-01-18
> **DMKryl said:**
> copy your bookmarks ( ~/.mozilla/firefox/(profile)/bookmarks.html.)
sudo apt-get remove firefox
restart system
reinstall firefox

Thanks!That solved it perfectly no more crashing also.

---

