---
title: "[SOLVED] How do I edit the host file?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by mstruve on 2008-12-11
Hi, sorry I have a total beginners question. I have literally just installed Ubuntu for the first time and am not hugely techy anyway. I've done a bit of reading around but can't find the answer to this:

I'm trying to get the iPhone VLC remote working, and have been told i need to :

[I]VLC in the latest versions uses a file called '.hosts' to define which computers can access the VLC remote player. You need to open this file and edit it:

you will need to edit the hosts file:

the file is in /usr/share/vlc/http/.hosts (If you're using the old http interface, it's located in /usr/share/vlc/http/old/.hosts )[/I]

How do I do this? Where do i enter this code?

Thanks for your help.

Matt

---

### Post by jakev383 on 2008-12-11
Go to Applications -> Accessories -> Text Editor
then select the Open button and navigate to that directory you need.  You'll need to right click on the dir listing in the center menu and select Show Hidden Files to see the file you want (a period as the first char of a filename signifies that it's hidden).

---

### Post by halitech on 2008-12-11
you can either 

a. Press Alt-F2 and type in ```
gksu gedit /usr/share/vlc/http/.hosts
```
or
b. open a terminal and paste in the same command.
or
c. open a terminal and type ```
sudo nano /usr/share/vlc/http/.hosts
```

---

### Post by mstruve on 2008-12-11
Wow, thanks very much for your quick replies. Much appreciated.

---

### Post by halitech on 2008-12-11
> **jakev383 said:**
> Go to Applications -> Accessories -> Text Editor
then select the Open button and navigate to that directory you need.  You'll need to right click on the dir listing in the center menu and select Show Hidden Files to see the file you want (a period as the first char of a filename signifies that it's hidden).


the file is in /usr/share/vlc/ so they need to do it with sudo or they won't be able to save the file

---

### Post by mstruve on 2008-12-11
> **halitech said:**
> the file is in /usr/share/vlc/ so they need to do it with sudo or they won't be able to save the file

yeah i think this is right, its saying "You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again."

Will try the other way. Thanks.

---

### Post by mstruve on 2008-12-11
> **halitech said:**
> you can either 

a. Press Alt-F2 and type in ```
gksu gedit /usr/share/vlc/http/.hosts
```
or
b. open a terminal and paste in the same command.
or
c. open a terminal and type ```
sudo nano /usr/share/vlc/http/.hosts
```

Sorry one more stupid question - i've followed your instructions here, and seem to have edited the code, but how do i then 'save' the modified version?
Thanks

edit - sorry should also say i used option c in your list.
thanks

---

### Post by halitech on 2008-12-11
if I remember right, it should be CTRL-O to save the file and CTRL-X to exit but just look at the bottom of the window, it should have the commands there

---

### Post by mstruve on 2008-12-11
> **halitech said:**
> if I remember right, it should be CTRL-O to save the file and CTRL-X to exit but just look at the bottom of the window, it should have the commands there

Thanks again for all your help. VLC remote now working like a charm :)

---

### Post by halitech on 2008-12-11
glad to hear that :) please remember to mark the thread solved in case others are serching for the same issue

---

### Post by oldos2er on 2008-12-11
> **halitech said:**
> if I remember right, it should be CTRL-O to save the file and CTRL-X to exit but just look at the bottom of the window, it should have the commands there

 Ctrl-X will prompt the user to save the file if it has changed.

---

### Post by halitech on 2008-12-11
I just prefer to do the save first myself, just in case :)

---

