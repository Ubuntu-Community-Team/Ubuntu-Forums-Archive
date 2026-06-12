---
title: "Ubuntu 8.04 &amp; Java &amp; Flash &amp; PhET"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by PhysicsBrown on 2009-10-02
[FONT=Times New Roman][SIZE=3]Under Ubuntu 8.04, I have installed an application called PhET (from Univ. of Colorado) that provides a nice set of Physics simulations. When I launch the application then try to run a specific simulation, instead of actually seeing the simulation running, I get a dialog asking if I want to save a document or specify an application to open it. I’m guessing this is because the simulation requires Java and/or Flash.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I’m not sure how to tell whether Ubuntu has previously installed Java and Flash. So I’ve been attempting to install (or reinstall?) them. I’m a beginner at this stuff, but I found the documentation that says go to System / Administration / Software Sources, and select “Software restricted by copyright or legal issues (multiverse)”.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Trouble is, that checkbox is already checked. There does not seem to be a way to tell this dialog “Please go ahead and install the multiverse stuff”. How do I do this? Or, if this means that Java and Flash are already installed, how do I actually get the PhET simulations to run?[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]Thanks in advance to anyone who can provide a clue for me![/SIZE][/FONT]

---

### Post by chaanakya_chiraag on 2009-10-02
Try the following:
Open a terminal (Applications -> Accessories -> Terminal) and copy and paste the following code.
```
sudo apt-get install adobe-flashplugin sun-java6-jre
```
type "y" whenever it asks if it is okay to do something.

---

