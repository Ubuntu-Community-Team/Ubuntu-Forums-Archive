---
title: "need help with xmms ./configure"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by AlphaWhelp on 2009-12-07
it says GLIB version 1.2.2 is not found and I should install it first, but I have already installed GLIB 2.14.6!  What is wrong?  Is XMMS not compatible with a later version of Glib?

---

### Post by LuisGMarine on 2009-12-07
post the exact error message, this way we have some actual errors to try and look over.

---

### Post by lloyd_b on 2009-12-07
> **AlphaWhelp said:**
> it says GLIB version 1.2.2 is not found and I should install it first, but I have already installed GLIB 2.14.6!  What is wrong?  Is XMMS not compatible with a later version of Glib?

No, it isn't.  XMMS is a GTK 1 application (which uses Glib 1), and will not build with GTK/Glib 2.

If you look in Synaptic, you'll see packages for GTK1/Glib1 as well as GTK2/Glib2.  You can safely have both versions installed on the same system.

(Note: Be sure to install the "...-dev" packages for them if you want to compile against them).

Lloyd B.

---

### Post by mc4man on 2009-12-08
If your looking for libgtk1.2 in karmic it's been removed. A couple of choices, you can dl and install the needed libs from jaunty or use a repo.

To dl, maybe better for you to dl and install individually.
Location and install order of *1.2 packages needed to build

[http://packages.ubuntu.com/en/jaunty/libglib1.2ldbl](http://packages.ubuntu.com/en/jaunty/libglib1.2ldbl)

[http://packages.ubuntu.com/en/jaunty/libgtk1.2-common](http://packages.ubuntu.com/en/jaunty/libgtk1.2-common)

[http://packages.ubuntu.com/jaunty/libglib1.2-dev](http://packages.ubuntu.com/jaunty/libglib1.2-dev)

[http://packages.ubuntu.com/jaunty/libgtk1.2](http://packages.ubuntu.com/jaunty/libgtk1.2)

[http://packages.ubuntu.com/jaunty/libgtk1.2-dev](http://packages.ubuntu.com/jaunty/libgtk1.2-dev)

...................................................................................

What would be easier is to add this xmms repo which has all of the above libs and also includes a prebuilt xmms for karmic 

[http://www.pvv.ntnu.no/~knuta/xmms/](http://www.pvv.ntnu.no/~knuta/xmms/)

To add repo just open System -> Software Sources -> third Party -> click on add, copy and paste 1st. karmic source line from link. ( you don't really need the deb-src line unlees you wish to build his xxms source) screen 1

If you wish the deb-src then add that line
After adding line(s) then click close and reload, after should look like screen 2 

If you wish to install the prebuilt xmms package then 
```
sudo apt-get install xmms
```

If you wish to install libgtk1.2 and deps for either building xmms or some of the plugins then 
```
sudo apt-get install libgtk1.2-dev
```

After that you'll probably want to track down and or build some extra plugins

---

### Post by lloyd_b on 2009-12-08
> If your looking for libgtk1.2 in karmic it's been removed. A couple of choices, you can dl and install the needed libs from jaunty or use a repo.

Oops.  I hadn't realized that they dropped Gtk/Glib 1.2 in Karmic.

Lloyd B.

---

### Post by ornovscot on 2010-05-19
I use a Dell inspiron 530, with Ubuntu.




When I tried to install the XMMS some months ago, I found these type of messages:


bash: ./sc_trans: Permission Denied


I tried typing in sudo_(My designated password)


Also, I typed in  apt-get update into the terminal window, after I typed in the above.


I received this response:

E: Could not open lock file/var/lib/apt/lists/lock - open(13 Permission denied)

E: Unable to lock the list directory




As it was some months ago, I can't remember what I did next.  But when I looked at the computer yesterday, for the first time in months, I found Amorok under Application->Sound & Video

Probably I installed Amorok.


When I tried to add MP3 files, I found the message "cannot support MP3", or words to that effect.  On the desktop is a folder of some of the MP3 files I wanted to add either to XXMS or to Amorok.


I made the necessary selections, but the problem didn't resolve.
I allowed packages to be added at the Synaptic Package Manager, but I couldn't resolve the problems I described.


Is there anything else I could do get the MP3 audio part of the Ubuntu working?


Thank you in advance.

---

