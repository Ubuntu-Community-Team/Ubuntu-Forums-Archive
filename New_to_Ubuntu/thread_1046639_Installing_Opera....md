---
title: "Installing Opera..."
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-01-21
Can someone please help me with installing Opera browser. I have the file downloaded but the package installer can't or won't install it... Thanx for your help.

---

### Post by fooman on 2009-01-21
exactly what package did you install? (...link?)

if its a .deb file (should be)...double clicking it should get it installed.

---

### Post by Michael.Godawski on 2009-01-21
Did you downloaded the deb file from here:

[http://www.opera.com/download/](http://www.opera.com/download/)

Then just double click for installation.

---

### Post by Leo Dragonheart on 2009-01-21
yes from that link

---

### Post by fooman on 2009-01-21
if nothing happens when you double click on it...perhaps gdebi (deb installer) is not installed?

find gdebi in synaptic and install it if is not already....or in a terminal:

```
 sudo apt-get install gdebi
```

---

### Post by Muffinabus on 2009-01-21
Hmm, I installed it in about 30 seconds just now by double clicking the .deb.  What's the exact problem you have when the package manager tries to install it?

---

### Post by Leo Dragonheart on 2009-01-21
The add and remove thing says I have gdeb installed but I can not find it to click on it...

---

### Post by mjheagle8 on 2009-01-21
go to open with, custom command, then type in gdebi

---

### Post by fooman on 2009-01-21
you do not click on gdebi...it is an installer which works when you *double click on a file ending with ".deb"*

if you downloaded the correct opera installation file....then it should end with .deb (does it?)

if so,  then just double-clicking on it* should* start gdebi and install the opera browser.

---

### Post by mjheagle8 on 2009-01-21
or you could open a terminal and use gdebi to install it through the terminal so you could see the output.

---

### Post by fooman on 2009-01-21
> **mjheagle8 said:**
> or you could open a terminal and use gdebi to install it through the terminal so you could see the output.

yeah,  if its not installing...thats the way to go.

---

### Post by Leo Dragonheart on 2009-01-21
I am still really new to this and don't know how to use the terminals very well...The first package I downloaded said it was gdeb but I can not find where it downloaded to. I am downloading it again but it is really slow only 71% done...

---

### Post by mjheagle8 on 2009-01-21
where did you download to?
in the terminal, navigate to the folder it was downloaded to using ```
cd /directory/file/is/in
``` then to install use ```
sudo gdebi filetoinstall.deb
```
obviously, replace the file path and name of the file to install.

---

### Post by Leo Dragonheart on 2009-01-21
It is installing now, this second download. I must have just done something wrong last time... Thanx for all your patience and advise...

---

### Post by mjheagle8 on 2009-01-21
no problem. glad to be able to help! :)

---

### Post by stchman on 2009-01-21
> **Leo Dragonheart said:**
> Can someone please help me with installing Opera browser. I have the file downloaded but the package installer can't or won't install it... Thanx for your help.

Did you download the .deb file for Ubuntu?  If yes then double click and it will install.

---

### Post by dgerwin11 on 2009-01-21
Did you try installing it from Synaptic?

---

### Post by stchman on 2009-01-22
> **dgerwin11 said:**
> Did you try installing it from Synaptic?

Opera is not in the repositories.

---

