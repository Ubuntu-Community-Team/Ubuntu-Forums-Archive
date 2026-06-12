---
title: "Help installing TrueType fonts?"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by Xjjulix on 2009-06-22
So.
I did the whole thing with the terminal, (gksudo nautilus) Got to the truetype fonts folder, made a new folder in that, tried to drag my font file in and...

You don't have the right permissions to extract archives in the folder "file:///usr/share/fonts/truetype/myfonts"

.....I got that error message. I also tried just dragging the file.:confused: help please?

Do I have to enable something? If so, what?
Or alternative ways of installing fonts?

---

### Post by Mornedhel on 2009-06-22
Copy-pasting between instances of Nautilus is usually cumbersome when not both instances have been started with administrative rights and you need the permissions. I recommended using the terminal to copy the files.

In the case of fonts, you should be able to install them in your own user directory. Create a folder called ".fonts" (with the leading dot) in your home directory : the full path should be "/home/yourusername/.fonts". Just drag and drop the .ttf files in there. They won't be available to every user in the system, but they will be available to you, which may or may not be good enough for your purposes.

If you are using Nautilus, you will later have to press Ctrl+H to display hidden files and folders. The leading dot is a convention to identify them.

---

### Post by jmszr on 2009-06-22
Xjjulix,

In the terminal Applications > Accessories > Terminal, type (or copy and paste)```
sudo apt-get install msttcorefonts
```
If it asks for your password, type it in (it won't show up - Security) and then click enter.

---

### Post by Xjjulix on 2009-06-22
> **jmszr said:**
> Xjjulix,

In the terminal Applications > Accessories > Terminal, type (or copy and paste)```
sudo apt-get install msttcorefonts
```
If it asks for your password, type it in (it won't show up - Security) and then click enter.

And what will that do?

---

### Post by jmszr on 2009-06-22
Xjjulix,

That will install the Microsoft True Type Fonts, msttcorefonts is also a part of the 
ubuntu-restricted-extras package - which if you haven't installed already is highly recommended.

---

### Post by Xjjulix on 2009-06-22
> **jmszr said:**
> Xjjulix,

That will install the Microsoft True Type Fonts, msttcorefonts is also a part of the 
ubuntu-restricted-extras package - which if you haven't installed already is highly recommended.

What about other downloaded fonts; like the kind of things you see on dafont.com?

---

### Post by jmszr on 2009-06-22
Xjjulix,

Here is one resouce:[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts) . Also 
#5 here has some more fonts: [http://theindexer.wordpress.com/2009/04/24/to-do-list-after-installing-ubuntu-904-aka-jaunty-jackalope/](http://theindexer.wordpress.com/2009/04/24/to-do-list-after-installing-ubuntu-904-aka-jaunty-jackalope/) and so does: [http://ubuntulook.com/tag/ubuntu-fonts-install/](http://ubuntulook.com/tag/ubuntu-fonts-install/)

---

### Post by oldos2er on 2009-06-22
[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

 Oops--someone beat me to it.

---

### Post by Xjjulix on 2009-06-22
:) I'm not sure what happend, I think the installing msttfonts did something, but now it works just fine. Thanks!

lol. Now to figure out how to get the thing on gimp...

-EDIT-
Nevermind. I restarted it, and the font appeared.
-thanks more-

---

### Post by Orion8 on 2009-06-22
Xjjulix --

I am glad you got your problem working, but I wanted to comment on your original problem.  You said you had a nautilus window open with "gksudo nautilus"...  The problem is, both nautilus windows needed to be in sudo mode.  Say your font files were on the desktop -- open a sudo nautilus, then on the window you opened do file -> new window.  Navigate the second window to ~/Desktop and the first to wherever you are stashing the fonts (eg /usr/share/fonts/truetype/myfonts ).  Now you can drag between the two as each window has the correct permissions.

---

