---
title: "can't find newly installed programs in menus"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-01-04
i just installed gimpshop and virtualbox from deb files online but i can't find out how to run them can somebody please help me out?

---

### Post by drs305 on 2009-01-04
VirtualBox is in Applications, System Tools or you can run it from terminal with:
```

VirtualBox

```

To find the run command for a program, you can type:
```

which <appname>

```
Example:  which gimpshop

---

### Post by kestrel1 on 2009-01-04
With Virtual Box it should be under Applications - System Tools
To run from the terminal type:
```
virtualbox
``` for the OSE version 
or
```
VirtualBox
``` for the non OSE version
Gimpshop would probably be under Applications - Graphics
or in the terminal possibly
```
gimpshop
```

---

### Post by gettinoriginal on 2009-01-04
Two ways, Right click the main menu and select edit menu and make sure these are checked, or you can choose terminal and just type in the program name.  :P

---

### Post by mamamia88 on 2009-01-04
ok i found virtualbox but i get error saying could not retrieve setting file i can't figure out how to remove it also i can't find gimpshop anywhere

---

### Post by kestrel1 on 2009-01-04
Did you get your deb for virtualbox from here:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by mamamia88 on 2009-01-04
> **kestrel1 said:**
> Did you get your deb for virtualbox from here:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

yeah thats exactly where i got it

---

### Post by kestrel1 on 2009-01-04
Did you get the correct version for your OS?
I got mine from there only yesterday & it installed no problem.
You could try installing it again.

---

### Post by carml on 2009-01-04
You have to create user group for Virtualbox,I did it when I launched the first time Virtualbox.:)

---

### Post by mamamia88 on 2009-01-04
anyone know how i can remove it so i can try installing it again?

---

### Post by carml on 2009-01-04
I think you can find gimpshop under usr/bin,tell us if you need more help.

---

### Post by carml on 2009-01-04
Simply go to System->Synaptic package manager and search the package you want to reinstall,then mark the package for reinstallation with a right click.(You can do also by terminal,but I don't know exactly how to do that:().

---

### Post by mamamia88 on 2009-01-04
> **carml said:**
> Simply go to System->Synaptic package manager and search the package you want to reinstall,then mark the package for reinstallation with a right click.(You can do also by terminal,but I don't know exactly how to do that:().

thats the problem i can't find it under synaptic

---

### Post by carml on 2009-01-04
[FONT="Times New Roman"]That sounds strange,did you looked for into your system? When you installed the software,how you did the installation?:confused: [/FONT]

---

### Post by mamamia88 on 2009-01-04
i ran a search for virtualbox in synapic but the only one that came up is the one that came with add/remove is there any keywords i should search for?  because when i do virtual box nothing comes up

---

### Post by kestrel1 on 2009-01-04
It doesn't show up in synaptic.
Just run the deb file again & let it re-install.

---

### Post by carml on 2009-01-04
You searched under Applications->Remove?,I meant the one under System->Synaptic package manager :).

---

### Post by starcannon on 2009-01-04
To remove software that was installed using a .deb file you can as suggested search for it in Synaptic; if that fails you can try the command line:
```
sudo apt-get remove {package-name}
```
It is also advisable to take a moment and read the man pages for apt-get, its a very handy command line tool that you may find yourself using regularly if you prefer application packages that are not in the Synaptic repositories:
```
man apt-get
```

Good Luck and have fun

---

### Post by mamamia88 on 2009-01-04
> **carml said:**
> You searched under Applications->Remove?,I meant the one under System->Synaptic package manager :).

yeah man thats the first thing i tried then i tried sudo dpkg -r VirtualBox but it just tells me it isn't installed which i know it is because when i run the deb file it says reinstall

---

### Post by kestrel1 on 2009-01-04
Using apt-get remove doesn't work on VirtualBox. I tried it myself.

---

### Post by kestrel1 on 2009-01-04
With regard to GimpShop try typing gimp into a terminal.

---

### Post by mamamia88 on 2009-01-04
doing that only brings up gimp i just want to uninstall all this so i can free up my harddrive space i didn't use much for my ubuntu partition

---

### Post by carml on 2009-01-04
If you want to remove something,in general it's necessary to perform a search under System->Synaptic package manager :P.

---

### Post by mamamia88 on 2009-01-04
i know but i tried every version of virtualbox imaginable in the search box and even included the version number but the only results that came up was the one from add/remove that isn't installed.  for the life of me i can't find the package to uninstall in synaptic

---

### Post by carml on 2009-01-04
Try to reboot,maybe the system has to refresh its configuration,then reinstall Virtualbox and run it,it should ask you to configure itself and if you want to compile the kernel module for Virtualbox.If you need more help you have only to ask. :)

---

### Post by mamamia88 on 2009-01-04
nah that didn't work ill try one more time to install the package and see if that works

---

