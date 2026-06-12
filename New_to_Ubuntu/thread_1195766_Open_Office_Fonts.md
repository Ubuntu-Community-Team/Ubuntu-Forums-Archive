---
title: "Open Office Fonts"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by dave collin on 2009-06-24
Hi,
New to ubuntu (jaunty) (last weekend) after years of MS.
I've got two issues with Open Office and from these and OO forums, I think one is ubuntu.
This is the missing fonts in drop down box.
Can someone explain very simply to a newbie how I can get them back, or to show and be assessable to Open Office.
I can find fonts in USR and have 3 folders: truetpe, type 1 and X11. 
I really have no idea what I'm doing (as yet!).
I've put this on OO forum as well - not sure if ubuntu or OO problem.
Thanks
Dave

---

### Post by lockettpots on 2009-06-24
Hi

Have a look at
[http://www.arsgeek.com/2007/07/19/how-to-install-truetype-fonts-on-your-ubuntu-computer/](http://www.arsgeek.com/2007/07/19/how-to-install-truetype-fonts-on-your-ubuntu-computer/)

or 

[http://www.wikihow.com/Install-True-Type-Fonts-on-Ubuntu](http://www.wikihow.com/Install-True-Type-Fonts-on-Ubuntu)

They worked for me

John

---

### Post by rushikesh988 on 2009-06-24
go to your home folder create the folder named as " .fonts  "   copy all fonts to it and also copy  all fonts to 

/usr/share/fonts/truetype




hope that will help you

---

### Post by Nautilus112 on 2009-06-24
If you want to add windows fonts as well, go to a windows computer and in C:/ there will be a folder named windows and then in it will be fonts, copy everything in that folder.  In Ubuntu, make a new folder called .fonts in your home folder, paste the windows fonts in there.  Install Fontmatrix through synaptic choose import, add the .fonts folder and then activate it.  You will see these fonts everywhere not just in openoffice.

---

### Post by jmszr on 2009-06-24
dave collin,

In the terminal - Applications > Accessories > Terminal, type (or copy & paste)```
sudo apt-get install msttcorefonts
``` If it asks for your password type it in (it will not be visible-Security) and press enter.
You should install the ubuntu-restricted-extras package which includes  msttcorefonts as well as codecs, flash and java.

---

### Post by dave collin on 2009-06-26
Thanks all,
I jumped the gun a bit with this post.
I figured it all out by reading stuff on forums.
Dave
:D

---

### Post by dave collin on 2009-06-26
By the way - how do I mark a thread as "closed" or "solved" (this one)

---

### Post by Scunnered on 2009-06-27
**dave collin**

You can do this by editing your original post.  Click edit to open it and then again to let you work with the header.

Previously there was a facility to do so and it displayed (SOLVED) before the header.

Hope this assists

---

