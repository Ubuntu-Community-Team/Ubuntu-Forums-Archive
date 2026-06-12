---
title: "Is printing files in Ubuntu possible????"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by suomalainen on 2011-06-01
Ubunteros,

In Microsoft Windows a user can right click on a file and print it. In Ubuntu a user needs to first open the file and then print.

Am I missing something??????

Thanks!

---

### Post by wolfen69 on 2011-06-01
Perhaps there is something in gconf-editor to add printing to right click menu, but not sure.

---

### Post by suomalainen on 2011-06-01
What's gconf-editor?

---

### Post by zipperback on 2011-06-01
> **suomalainen said:**
> What's gconf-editor?


It's the gnome configuration editor.

You can launch it by pressing alt-f2, and then entering gconf-editor.

It's basically the GUI version of the gnome configuration tools.


- zipperback
:popcorn:

---

### Post by zipperback on 2011-06-01
In regard to the original question regarding right click and print, you can possibly try the information on the following page.

[http://ubuntuforums.org/showthread.php?t=191020#2](http://ubuntuforums.org/showthread.php?t=191020#2)

It looks to be what you want.

- zipperback
:popcorn:

---

### Post by suomalainen on 2011-06-01
Thanks for explaining. I looked inside but didn't see anything that would add the "PRINT" functionality when right clicking on items.....

---

### Post by suomalainen on 2011-06-01
Close.... But no cigar.

---

### Post by HermanAB on 2011-06-01
Yes it is possible.  You can send any ASCII/PDF/PS file straight to the printer device and it will print it for you directly.

[http://www.aeronetworks.ca/howtos/print-howto.html](http://www.aeronetworks.ca/howtos/print-howto.html)

---

### Post by Mariane on 2011-06-01
It is not always possible. It depends upon the printer you have. I have an HP printer/scan/photocopier which does not yet have drivers for Linux. Epson printers have a much better compatibility in my experience. 

Mariane

---

### Post by suomalainen on 2011-06-01
I want to simply be able to right click on the file name and choose PRINT to print the document.

So far the advice offered doesn't allow for this.

---

### Post by I'mGeorge on 2011-06-01
What you want in linux depends on several factors.

First of all the name of the thread is kinda miss leading. You already know printing in linux it's more than possible you just wanna do it by right clicking on a text file, so the name should had been "is printing possible just by right clicking on a text file?"

For what you need it depends of the Desktop you're using and it's preinstalled apps, and most important what file browsers you're using. I've used several file browsers and none had this option, printing just by right clicking on a file, but you can check this following link for inspiration as it's something that can be easily implemented [http://www.frenssen.be/content/printing-file-right-click-context-menu-nautilus](http://www.frenssen.be/content/printing-file-right-click-context-menu-nautilus)

---

### Post by Paqman on 2011-06-01
There's no ready-made solution for this, but you can use the package [nautilus-actions](apt:) to create a custom entry in the right-click menu.

[See here for details]("http://ubuntuforums.org/showpost.php?p=10228151&postcount=6").

---

### Post by suomalainen on 2011-06-01
@ Paqman!

Thank you very much for this info. I just got it working and it works perfectly. Instructions are real easy to follow too!!!

I tried to also see if I could convert a .txt or .doc file to pdf using same format but it didn't work. Any ideas?

Thanks once again!!!!!

---

### Post by Mariane on 2011-06-01
You might also be interested in the printer desktop icon. This is again not what you asked for but I used to find it useful, in particular because you could drag and drop a whole folder on it and it would print every document in that folder. No need to do "print" for all documents one by one. 

Mariane

---

