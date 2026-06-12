---
title: "I removed Python, half of my applications gone!"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by BioVirtual on 2009-12-16
Hi, 
I removed Python from Synaptic Package Manager. lots of thing became removed from ,y Ubuntu including Terminal and Synaptic itself! How to bring them back?

---

### Post by Physical Hook on 2009-12-16
Aptitude doesn't seem to depend on Python so you should be able to install things by using the following command.

```

sudo apt-get install <package>
```** You should still have xterm.

---

### Post by BioVirtual on 2009-12-16
should I install them one by one now?! Under System I just have Administration and under that 3 options only! How can I get everything back as before?

---

### Post by ankspo71 on 2009-12-16
Hi,
I think if this happened to me I would try to reinstall the package called ubuntu-desktop. If that doesn't work I would at least try to install the packages gnome-terminal and synatic.

So drop to shell
Press Ctrl+Alt+F1   (Ctrl+Alt+F7 should bring you back)

(you might need to write this down because your browser (and desktop) will close.)

Login into the terminal if you have to with your username and password.

type the following:

```
sudo apt-get install ubuntu-desktop --reinstall
```if that doesn't help:

```
sudo apt-get install gnome-terminal synaptic --reinstall
```Now type:
```
sudo reboot
```Now Ctrl+Alt+F7 should bring you back (if needed)

Hope this helps.

---

### Post by lloyd_b on 2009-12-16
> **BioVirtual said:**
> Hi, 
I removed Python from Synaptic Package Manager. lots of thing became removed from ,y Ubuntu including Terminal and Synaptic itself! How to bring them back?

Hold the <CTRL> and <ALT> keys, and press <F1> - this should bring you to one of the virtual consoles (there are others on F2 thru F6).  Login in, and then run "sudo apt-get install python" to reinstall Python.

Now for the bad news - it probably uninstalled a lot of other things when you removed Python, because of the various dependencies.  You may be reinstalling things for a while.

I'd recommend reinstalling "update-manager", "yelp", "totem", "gnome-system-tools", and "synaptic" just to get started.  I'm pretty sure there'll be more...

Lloyd B.

---

### Post by BioVirtual on 2009-12-16
Well, I'm Using Ubuntu as my second OS because I expect such things from it. But basically it's so stragne! You uninstall something and well, You are dead ! Do 80% of Ubuntu default applications depend on the Python that I just removed? I was trying to remove it and install Python 3 for developing purposes...

---

### Post by EndPerform on 2009-12-16
> **BioVirtual said:**
> Well, I'm Using Ubuntu as my second OS because I expect such things from it. But basically it's so stragne! You uninstall something and well, You are dead ! Do 80% of Ubuntu default applications depend on the Python that I just removed? I was trying to remove it and install Python 3 for developing purposes...

You can install python and python3.1 side-by-side without trouble as the executable will be named 'python3.1'.  Quite a few Ubuntu utilities depend on python, which is exactly why removing it caused a lot of the applications that depend on it to uninstall.

---

### Post by megamania on 2009-12-16
> **BioVirtual said:**
> Well, I'm Using Ubuntu as my second OS because I expect such things from it. But basically it's so stragne! You uninstall something and well, You are dead ! Do 80% of Ubuntu default applications depend on the Python that I just removed? 
You get a warning and a list of what is going to be uninstalled.

---

### Post by BioVirtual on 2009-12-18
You're right. But who knows what these short alphabetical names are!? And the same name for Python repeated many times which I don't understand why.
 And I have another question, Python installation as a language is used to develop Python applications. How all these OS apps can depend on that? e.g. Ubuntu Terminal depends on Python installation?! Or the Python I removed was its virtual machine (like JVM) or framework or something like that? Appreciate some technical information about these concepts...
 

 Thanks.

---

