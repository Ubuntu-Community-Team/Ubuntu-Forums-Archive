---
title: "windows applications"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by krishnakittu on 2009-02-11
How can i run windows applications on ubuntu 8.10 ?
help me out

---

### Post by ainsworth_t on 2009-02-11
There are two ways you can run Windows applications within Ubuntu. You can either try to run them through emulation by installing WINE through the Synaptic Package Manager and running your programs through their.

The second option would be to install VirtualBox (virtualbox-ose), install Windows within a virtual machine, and run your apps on the virtual machine. You can install guest additions on the guest Windows OS which will allow for seamless mode.

---

### Post by unixeducation on 2009-02-11
You can give Wine a try. Install it using the Add/Remove option from your Applications menu. A company called CodeWeavers ([http://www.codeweavers.com](http://www.codeweavers.com)) markets a version of Wine designed to make running many Windows applications a lot easier, which may help as well.

If you like, you can install VirtualBox and run Windows inside Ubuntu. I use this method for testing Win32 software without the need for separate machines.

---

### Post by Peter09 on 2009-02-11
Well the first question to consider is why run a windows application on Linux. Linux has almost all the software functionality that you want with native apps.

If there is an application that you need that cannot be found, use wine (its in the repositories). Its not too difficult, google it. The other option is virtualBox, it allows you to run XP etc within Ubuntu as a virtual machine.

Jsut seen the above reply, great minds etc....

---

### Post by ibizatunes on 2009-02-11
windows application dont natively run on linux 
[www.winehq.org/](www.winehq.org/) is your best bet 
Wines allow window application to run in linux but it hit or miss

---

### Post by krishnakittu on 2009-02-11
> **ainsworth_t said:**
> There are two ways you can run Windows applications within Ubuntu. You can either try to run them through emulation by installing WINE through the Synaptic Package Manager and running your programs through their.

The second option would be to install VirtualBox (virtualbox-ose), install Windows within a virtual machine, and run your apps on the virtual machine. You can install guest additions on the guest Windows OS which will allow for seamless mode.

how can i install WINE ?

---

### Post by dca on 2009-02-11
Click 'Applications -> Add/Remove Applications' from the menu bar.  On the 'show' drop-down, select 'All available applications'.  In search type 'wine' and hit [ENTER]
 
...put a check-mark in either Wine Microsoft compatibility layer or you can install the PowerPoint Viewer app which automatically pulls in Wine with it...

---

### Post by unixeducation on 2009-02-11
Go to your "Applications" menu in the upper left corner, click "Add/Remove" at the bottom of the popup menu. Search for "wine" and install it. You can do this from a terminal session by tying "sudo apt-get install wine"

---

### Post by Peter09 on 2009-02-11
Install WINE through synaptic - System->Administration->Synaptic Package Manger

or in a terminal

```
sudo apt-get install wine
```

both do the same thing.

---

