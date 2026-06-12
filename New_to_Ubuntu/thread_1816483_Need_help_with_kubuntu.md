---
title: "Need help with kubuntu"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by publicladykilla on 2011-08-02
I cannot install any applications. Ive tried many different apps. All come up with an error saying to close any legacy package. and it stops at manaer lock when downloading. Please help.

---

### Post by josephmills on 2011-08-02
Hi there when trying to install things other applications that depend on it can not be open ie synaptic and kpackagekit 

try and install htop using Konsole htop shows all programs that are running on system. 

```
sudo apt-get install htop 
``` 


did it work ? if it did great if not any errors ? also 
What are you trying to install ?

---

### Post by publicladykilla on 2011-08-02
I tried that command and nothing happend. I dont think i have anything running but im trying to install wine and some games, but everytime no matter what i try to install it says this exactly " Cannot get the exclusive lock on the package backend. Please close any other legacy packaging tools that may be open"
Im stuck. Cant download any apps games or anything.

---

### Post by bodhi.zazen on 2011-08-02
Usually this happens when you are running more then one package manager at at time. Are you running ADD/Remove applications, synaptics, update manager, or any other application ? 

If you have configured automatic updates, it may be running in the background.

---

### Post by publicladykilla on 2011-08-02
I dont have anything running at all. It just at my desktop. Just a few dumb little widgets on the desktop. I havnt been able to install apps since i loaded kubuntu into my laptop.

---

### Post by bodhi.zazen on 2011-08-02
Open a terminal, try to install something with apt-get, post any error message you get here.

---

