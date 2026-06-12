---
title: "Question on installing"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by danielgrosvenor on 2010-10-11
Hi guys

I'm really enjoying Ubuntu so far, and am impressed by how user-friendly a great deal of it is.

One thing I am having trouble with, however, is installing things that I've downloaded from the web.  For example, [this Compiz-Indicator from Gnome-Look]("http://www.omgubuntu.co.uk/2010/09/compiz-indicator-applet-gives-you-compositing-control-in-a-click/").  I downloaded and extracted it to my desktop, but am not sure what to do next.  The guide says to type 
```
chmod +x install.sh
./install.sh
```
into Terminal which, as I had kinda guessed, doesn't work on its own as presumably I need to specify the file's location first.

My question is, er, how do I do that??  (And is there not a way to simply double-click on the install.sh or whatever file, after setting its permissions to Extractable, and avoid the Terminal all together?  This was my first approach, but again nothing happened.)

---

### Post by ibizatunes on 2010-10-11
```
cd ~/Downloads
```

cd = change directory    ~ =home      / =location

so it means cd to home in folder Downloads

then try your chmod etc

---

### Post by danielgrosvenor on 2010-10-11
So I should type **cd ~/Desktop/(containing folder)** into Terminal before any other commands?

---

### Post by Bölvaður on 2010-10-11
> **danielgrosvenor said:**
> is there not a way to simply double-click on the install.sh or whatever file, after setting its permissions to Extractable, and avoid the Terminal all together?
Right click on the file, click Properties and then Permissions, mark the "Allow execut.. as a program", click ok. Double click.


also you could have just claimed the whole path for the file
chmod +x ~/Desktop/install.sh

---

### Post by danielgrosvenor on 2010-10-11
> **Bölvaður said:**
> also you could have just claimed the whole path for the file
chmod +x ~/Desktop/install.sh

I have multiple install.sh files (in different folders) on the desktop.  Will typing that install them all at once, or just risk creating problems/confusion?

---

### Post by sandyd on 2010-10-11
> **danielgrosvenor said:**
> I have multiple install.sh files (in different folders) on the desktop.  Will typing that install them all at once, or just risk creating problems/confusion?
no, that just makes the script executable. You must do that for each of the install scripts

So, if the folder on the desktop is called "1", then
```

chmod -x ~/Desktop/**1**/install.sh
```
you will have to browse to the folder (inside of it) before you can run the install script.
```

/bin/bash ~/Desktop/**1**/install.sh
```

---

### Post by oldos2er on 2010-10-11
> **danielgrosvenor said:**
> I have multiple install.sh files (in different folders) on the desktop.

Can you post the output of **ls ~/Desktop** ?

---

