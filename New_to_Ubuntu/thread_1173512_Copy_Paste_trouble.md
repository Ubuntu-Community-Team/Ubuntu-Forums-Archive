---
title: "Copy Paste trouble"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by rvgsd on 2009-05-29
Hi, 

I am using Xubuntu 8.04 LTS, Kernel 2.6.24-19.
Everything works fine, except I am having trouble with copy paste.

If I copy some text from a document, close that document, open another one, and try to paste, it doesn't work. However, if the document from which I am copying is open at the time I paste into the other document, it works. 
Its exactly the same with copying files from one folder to another. 

Is it supposed to be this way?
Is there any way I can keep the text/file in the memory even when I close a document/folder.

Thanks for helping.

---

### Post by halitech on 2009-05-29
I'm not sure if it is supposed to work that way or not but same thing happens to me (using Debian with XFCE). If its a bug/"undocumented feature" then I would guess its in XFCE not ubuntu or debian. Not sure if there is a way around it or not as I've never looked all that hard.

---

### Post by Hospadar on 2009-05-29
Are you using the default xfce text editor (mousepad)?  You might try using a different text editor, like gedit/kate/scribes/etc.  It seems unlikely that the problem lies in the editor, but you never know.

---

### Post by Sef on 2009-05-30
1) What are you using to read the document from: Abiword, mousepad, or other?

---

### Post by theozzlives on 2009-05-30
I have the same problem with firefox, I just keep it open.

---

### Post by CatKiller on 2009-05-30
> **rvgsd said:**
> If I copy some text from a document, close that document, open another one, and try to paste, it doesn't work. However, if the document from which I am copying is open at the time I paste into the other document, it works. 
Its exactly the same with copying files from one folder to another.

That's right. There isn't currently a unified "clipboard" under Linux for copy and paste, so you need to keep the source application open for it to work.

I believe the freedesktop people are working on a specification for this.

---

### Post by Ms_Angel_D on 2009-05-30
for xfce (xubuntu) Search synaptic for a little panel plugin called clipman that should fix all your copy and paste woes ;)

for gnome (ubuntu) try glipper and for
for kde (kubuntu) try klipper

---

### Post by Zalbor on 2009-05-30
klipper in KDE is standard, no need to install it.
For Gnome I use Parcellite, it should probably work in xfce too.

---

### Post by halitech on 2009-05-30
> **Ms_Angel_D said:**
> for xfce (xubuntu) Search synaptic for a little panel plugin called clipman that should fix all your copy and paste woes ;)

for gnome (ubuntu) try glipper and for
for kde (kubuntu) try klipper

thanks for that, just added clipman to my panel and it works like a charm :) Although I don't think clipman is a separate program, I think its part of the xfce4-goodies package

---

### Post by bacardiandwatermelon on 2009-05-30
Thanks for the glipper app, it works a treat :-)

---

### Post by rvgsd on 2009-06-18
Clipman works great! 
Thanks!

rvgsd

---

