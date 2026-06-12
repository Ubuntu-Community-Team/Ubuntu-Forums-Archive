---
title: "run updates manually"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by keyfeather on 2009-04-01
Hi,

I need to run the updates manually- I have seen the codes posted but I don't know where to type them- sounds dumb,forgive me, but I would really appreciate help. 

I went to applications, then accessories, and the to terminal but there wasn't place to type a password or the code.

---

### Post by lindsay7 on 2009-04-01
When you go to the terminal there is a blinking curser. That is where you type the code and you password when asked.

Download this and use it as a guide. It will answer a lot of you questions.

[http://www.ubuntupocketguide.com/download3.html](http://www.ubuntupocketguide.com/download3.html)

---

### Post by Kevbert on 2009-04-01
Go to Applications-Accessories-Terminal and type in
```
sudo apt-get update
sudo apt-get upgrade
```
You'll be prompted for your login password. The first command gets the update list and the second downloads and installs the updates.  You may get the icon in the top right-hand corner of your desktop say there's loads of new updates to install after the first command, ignore this when manually updating and just use the commands (otherwise you'll get an error).

---

### Post by clive littlewood on 2009-04-01
Hi

Just in addition to the above note that when you type in your password nothing shows (this is for security) just type as normal and enter.

Clive         :p

---

