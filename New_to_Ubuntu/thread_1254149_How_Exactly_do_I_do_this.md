---
title: "How Exactly do I do this?"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by Ronchap on 2009-08-31
Im following a guide on how to install WoW on linux.

"Now we need to, as root, make a file with a text editor in /etc called ld.so.conf, that contains a single line specifying a directory: /usr/local/lib
Now run the command 'sudo ldconfig'. This is necessary due to the special way Ubuntu handles dynamic linking (I think), while Wine expects the more standard method."

I'm in root, just dunno what to do from there.

---

### Post by SoftwareExplorer on 2009-08-31
Do ALT+F2 and put ```
gksudo gedit
``` in and hit run. It will ask your password and then it will open a text editor that is allowed to make changes to files in the /etc directory.

---

### Post by dearingj on 2009-08-31
In a terminal, type
```
sudo gedit /etc/ld.so.conf
```
The sudo may not be necessary, since you say you've already got root access.

In gedit, add the following line to whatever (if anything) is already there:
```
/usr/local/lib
```

Then close gedit, making sure to save the file, and run this command in the terminal:
```
sudo ldconfig
```

---

### Post by Ronchap on 2009-08-31
> **dearingj said:**
> In a terminal, type
```
sudo gedit /etc/ld.so.conf
```The sudo may not be necessary, since you say you've already got root access.

In gedit, add the following line to whatever (if anything) is already there:
```
/usr/local/lib
```Then close gedit, making sure to save the file, and run this command in the terminal:
```
sudo ldconfig
```

I do the gedit /etc/ld.so.conf but then get this message
"(gedit:5411): Gtk-WARNING **: cannot open display: 
root@rchap-desktop:~# " 
What's this mean? :(


And with the gksudo command, the (gedit:5415) now.

---

### Post by OutOfReach on 2009-08-31
> **Ronchap said:**
> I do the gedit /etc/ld.so.conf but then get this message
"(gedit:5411): Gtk-WARNING **: cannot open display: 
root@rchap-desktop:~# " 
What's this mean? :(


And with the gksudo command, the (gedit:5415) now.

Hmm, did you press Ctrl+Alt+F2 instead of Alt+F2?

---

### Post by SoftwareExplorer on 2009-08-31
When it gives you an error like that it usually means that it can't open a graphical application. If you have just the command line and it says root@computername then you can run just 'nano /etc/ld.so.conf' and if it says yourusername@yourcomputername then run 'sudo nano /etc/ld.so.conf'.

---

