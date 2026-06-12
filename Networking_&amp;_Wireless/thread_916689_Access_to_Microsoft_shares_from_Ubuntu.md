---
title: "Access to Microsoft shares from Ubuntu"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by frisket on 2008-09-11
A Microsoft-using colleague has send me a link to some documents he wants people to read, which is in the format:

\\somename\dir\dir\dir\dir\

How do I create a link on my desktop which will open this in a browser (eg FF)?

If I click on Places in my menubar and select Connect to Server, and then pick Windows Share, how do I find out what the name of the server (is that the \\somename?) and the share (is it the first directory name in the address quoted?)

---

### Post by arunvir on 2008-09-11
make it into zip and host it in some file hosting server and post the link here


or try posting it as an attachment in here


I believe that you are trying to post that document here

---

### Post by sv1cdn on 2008-09-11
Hello!
I use File browser and then type something like:

smb://10.0.0.196/lexis/

which show the IP address of a windows server (LAN) and the name of the shared directory. Ubuntu makes me a mounted folder at the desktop.
You must have samba install, u get this easily done by sharing one of ubuntu folders.

---

### Post by arunvir on 2008-09-11
:(:(:(
sorry

I though of this as something else
:lolflag::lolflag::lolflag:
I think connect to server must do the trick though

Does it work then??

---

### Post by frisket on 2008-09-11
> **arunvir said:**
> make it into zip and host it in some file hosting server and post the link here
or try posting it as an attachment in here
I believe that you are trying to post that document here

Huh? Did you even bother to read my question?

---

### Post by frisket on 2008-09-11
> **sv1cdn said:**
> Hello!
I use File browser and then type something like:

smb://10.0.0.196/lexis/

But there isn't an address bar in File Browser where I can type this.

[edit] Ah, yes there is...have to click on the paper'n'pencil icon. Duuh. No wonder Ubuntu gets criticised for poor usability.

Yay. That worked, many thanks. Pity XSMbrowser doesn't have this ability.

---

