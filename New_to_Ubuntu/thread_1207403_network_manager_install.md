---
title: "network manager install"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by benh13 on 2009-07-08
Hey
i'm new to ubuntu, and after following some advice while trying to set up a static ip address, i uninstalled network manager and now have no internet connection on that machine. is there any way to reinstall network manager?
thanks

---

### Post by binbash on 2009-07-08
Yes download network-manager-gnome and its deps from : 

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

And of course install them.

---

### Post by benh13 on 2009-07-08
are there any commands i could use to install it via the terminal?

---

### Post by binbash on 2009-07-08
Before downloading the packages, give this command : 

sudo apt-get install network-manager-gnome

You will see the deps there.Go to that page, download that packages.Then go to the folder you have downloaded them and give this command : 

sudo dpkg -i *.deb

---

### Post by benh13 on 2009-07-08
is it possible to do this on the ubuntu computer with no internet connection? i have tried going to the page using the debs but it is not working

---

### Post by benh13 on 2009-07-08
> **binbash said:**
> Before downloading the packages, give this command : 
 
sudo apt-get install network-manager-gnome
 
You will see the deps there.Go to that page, download that packages.Then go to the folder you have downloaded them and give this command : 
 
sudo dpkg -i *.deb
 
i tried this, but i can't use the deps and go to these pages, since i don't have internet connection anymore

---

### Post by carml on 2009-07-08
Don't panic,you can also download the package from an oher PC and then boot into your double-click the package and it will install. :)

---

### Post by tarps87 on 2009-07-08
If you have a copy of the live cd you can put that in then System -> admin -> Software Sources now tick on installable from cdrom
Now
```
sudo apt-get install network-manager-gnome
```

Once installed untick installable from cdrom.

---

### Post by irv on 2009-07-08
Once you get your network working, I would install wicd network manager from Synaptic package manager. It is much better then Gnome network manager. It is very easy to setup a static IP address. once you install it, you need to log off and then back on again after installing it. A network icon will appear in your notification part of your toolbar. Just click on the icon and a dialog box will appear with all the available network connection. click on the advance setting on your connection and put a check mark in the static IP box. fill in the address and sub mask and gateway and you are all set. See screen shots.
[ATTACH]120340[/ATTACH]

[ATTACH]120341[/ATTACH]

[ATTACH]120343[/ATTACH]

In order to install wicp network manager it will have to un-install Gnome network manager because it will conflict with wicp. You can only use one or the other.

---

