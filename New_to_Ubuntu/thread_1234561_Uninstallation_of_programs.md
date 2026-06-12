---
title: "Uninstallation of programs"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by sp176 on 2009-08-08
How do I go about uninstalling programs I do not wish?  For many of the simpler stuff I use Applications/AddRemove.  

I have tried to install VirtualBox and discovered that I installed the wrong version, and now I cannot install the correct one until I get rid of the old one.  It tells me to check out etc/vbox/vbox.cfg to find the location of the installation.  Do I simply delete these files and I am good to go?  Windows wouldve hated that approach, but I don't know if Ubuntu would be fine with it.

---

### Post by SunnyRabbiera on 2009-08-08
For applications you did not install with add/remove use synaptic located under system> administration> synaptic package manager.\
its easy enough to use

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

this will help understand how synaptic works

---

### Post by computerkid2000 on 2009-08-08
well you have to go into Acccesories> add/remove programs than click on the drop down box in the new window and click on already installed programs than uncheck all the programs you dont want and click apply or somthing else that relates to that (i am not in ubuntu right now :() and your done!:popcorn:

---

### Post by SunnyRabbiera on 2009-08-08
> **computerkid2000 said:**
> well you have to go into Acccesories> add/remove programs than click on the drop down box in the new window and click on already installed programs than uncheck all the programs you dont want and click apply or somthing else that relates to that (i am not in ubuntu right now :() and your done!:popcorn:

nono, let him do it with synaptic, synaptic is easy enough anyway.

---

### Post by sp176 on 2009-08-08
I cannot find the program in either the add/remove section or synaptic.

I installed virtualbox 2.0.2.  I can see the 2.0.4 in synaptic, but not the one I wish to uninstall.

---

### Post by mthalis on 2009-08-08
If you like you can use **Ubuntu-Tweak** to install or uninstall software.

---

### Post by lisati on 2009-08-08
Don't forget to click the button in Add/Remove to show all available software.

---

### Post by sp176 on 2009-08-08
I am not familiar with tweak, how do I go about getting it?

---

### Post by sp176 on 2009-08-08
Sorry, but maybe I should mention that I got this virtualbox from a free Linux CD in a mag, and not originally from synaptic

---

### Post by SunnyRabbiera on 2009-08-08
> **sp176 said:**
> Sorry, but maybe I should mention that I got this virtualbox from a free Linux CD in a mag, and not originally from synaptic

should not matter, but did you install it with a .deb installer?

---

### Post by sp176 on 2009-08-08
The disk said copy this file to home directory and run in terminal "sh Virtualbox-2.0.2-36488-Linux_x86.run" so I did.  I see it in Applications/System Tools, but it don't work, so I look in the DVD and I see a deb file under the Virtualbox/Ubuntu folder, so I figure maybe I should run that.  It says that my previous install is an older version and I need to uninstall.

---

### Post by mthalis on 2009-08-08
Regrading Tweak 
you can use [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) official details 

I installed it after reading this blog
[http://goblog.vergilhost.info/?p=57](http://goblog.vergilhost.info/?p=57)

---

### Post by shae on 2009-08-08
You should first recopy the .run file you used before and use the following:

```
sudo sh NameOfFile.run uninstall /path/you/installed/it/to
```

Then you should remove the version from synaptic and then install it again.

I hope that clears things up.

---

### Post by 3rdalbum on 2009-08-08
What does the documentation from [www.virtualbox.org](www.virtualbox.org) say?

---

### Post by sp176 on 2009-08-08
Worked like a charm shae.  Thank you very much.  I did not have to include the installation path for uninstallation, because I did not include it during installation.

---

