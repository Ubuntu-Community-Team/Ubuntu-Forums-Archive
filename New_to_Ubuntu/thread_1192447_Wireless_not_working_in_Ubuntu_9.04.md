---
title: "Wireless not working in Ubuntu 9.04"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by robbiechad on 2009-06-20
how do I Hi, Can anyone help me? I'm having problems getting Ubuntu to see my wireless card (Atheros) I have down loaded the madwifi files and unpacked them but what commands do I put into the terminal to compile the package to allow me to install it.  I tried to follow a blog instruction from a previous post but it seems to me part of the commands are missing because it just said 'make' then a blank space and the terminal didn't  know what to make of it. I'm stumped!!

---

### Post by 3rdalbum on 2009-06-20
The usual set of commands to compile is:

```
./configure
make
sudo make install
```

So, "make" on its own is a valid command. Don't put any blank spaces after it.

---

### Post by robbiechad on 2009-06-20
Hi Again, I do not know what I have done but my wireless connection is now working!!! Yahoo, all I know I have done was to go into hardware drivers and the Atheros Madwifi driver appeared, I clicked on it to apply it and  Ubuntu immediately saw my wireless connection and asked for the password... Bingo .. connected. So thanks for your help.. Lets see how I get on from now on.  My printer is working also my Scanner although it does seem a might complicated using Xsane software.:lolflag:

---

