---
title: "Installing Ubuntu Studio desktop in 10.04 Is it possible ???"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by Souptik on 2011-02-19
I am using Lucid Lynx for quite a while now and for just a change of taste I want to try out the different desktop environments available like KDE(Kubuntu) , Mythbuntu, Ubuntu Studio etc. I googled about it and got a result from [http://blog.sudobits.com/2010/05/09/how-to-install-kde-in-ubuntu-10-04-2/](http://blog.sudobits.com/2010/05/09/how-to-install-kde-in-ubuntu-10-04-2/) saying

> Ubuntu 10.04 uses GNOME desktop as their default desktop.If you want to  use only KDE desktop then there is special KDE version of Ubuntu known  as Kubuntu(KDE+Ubuntu).But you may like to test all the desktop of  ubuntu as each has its own taste and significance then you can do that  in few steps.Actually all different versions of ubuntu like  Kubuntu,Xubuntu,edubuntu,Mythubuntu,Ubuntu Studio or others differs only  in their default desktop and the basic applications installed by  default.So if you want to use other desktops then use synaptic manager  to install them and you will be able to use all desktop in single  installation(e.g in ubuntu 10.04 you can enjoy  kde,xfce,edubuntu,UbuntuStudio etc.).

I have intensively googled about installing the ubuntu studio desktop in my Lucid Lynx (not because I do not like the GNOME desktop) so that when I log in I can choose which desktop I want to use but it did not yield much results. Is it possible and how????

Thanks in advance...

---

### Post by Souptik on 2011-02-19
Just an update. I checked the Package manager, it shows lots of installable packages, but which ones should I install ????

---

### Post by inobe on 2011-02-19
despite what web sites may state, i would advise against it!


as these desktops can be installed and used from in sessions, it is very difficult removing them without major complications.

the applications may not play nice, for example, you will see kde applications in your ubuntu menu, or ubuntu apps in kde's menu, in short, a mess.

the best way to get an accurate feel, is to install them to a hard drive.

---

### Post by Souptik on 2011-02-19
> **inobe said:**
> 

the best way to get an accurate feel, is to install them to a hard drive.

By asking me to install in the hard drive do you mean that I will get the whole Kubuntu installed like I did for my Ubuntu using a Live CD ???

---

### Post by ajgreeny on 2011-02-19
> **inobe said:**
> despite what web sites may state, i would advise against it!


as these desktops can be installed and used from in sessions, it is very difficult removing them without major complications.

the applications may not play nice, for example, you will see kde applications in your ubuntu menu, or ubuntu apps in kde's menu, in short, a mess.

the best way to get an accurate feel, is to install them to a hard drive.
In spite of inobe's comments here, I would say "try it", but keep a "Save markings as" from synaptic of all the packages installed when you add ubuntustudio-desktop as it will make it much easier to remove everything if you want in future.

1.  Open synaptic
2.  Search for ubuntustudio-desktop and mark it for installation with all other packages it needs.
3.  Go to File menu and "save markings as" a file studio.txt
4.  Click "apply" icon.

I have often used both ubuntu-desktop and kubuntu-desktop on one installation in past with no problems;  the menus do get a bit large, but there are ways to avoid that by editing the menu in each desktop environment.  It certainly was not a problem to me ever.

If you should decide that it really does make things too unwieldy,and you want to remove ubuntustudio, you can simply use your studio.txt to list the packages added and with command ```
sudo apt-get remove *list of packages*
```you can get rid of the lot and go back to where you were.

---

### Post by Souptik on 2011-02-20
> **ajgreeny said:**
> In spite of inobe's comments here, I would say "try it", but keep a "Save markings as" from synaptic of all the packages installed when you add ubuntustudio-desktop as it will make it much easier to remove everything if you want in future.

1.  Open synaptic
2.  Search for ubuntustudio-desktop and mark it for installation with all other packages it needs.
3.  Go to File menu and "save markings as" a file studio.txt
4.  Click "apply" icon.

I have often used both ubuntu-desktop and kubuntu-desktop on one installation in past with no problems;  the menus do get a bit large, but there are ways to avoid that by editing the menu in each desktop environment.  It certainly was not a problem to me ever.

If you should decide that it really does make things too unwieldy,and you want to remove ubuntustudio, you can simply use your studio.txt to list the packages added and with command ```
sudo apt-get remove *list of packages*
```you can get rid of the lot and go back to where you were.

I have a question, suppose I like the Ubuntu Studio desktop just too much after I install it, could I just remove my old desktops and use my new Ubuntu Studio ???

---

### Post by ajgreeny on 2011-02-20
> **Souptik said:**
> I have a question, suppose I like the Ubuntu Studio desktop just too much after I install it, could I just remove my old desktops and use my new Ubuntu Studio ???
I see no reason why not.  US uses all the same repos as ubuntu, plus it's own, I assume, so you can add what you need without problem as far as I can make out.

---

### Post by Souptik on 2011-02-20
> **ajgreeny said:**
> I see no reason why not.  US uses all the same repos as ubuntu, plus it's own, I assume, so you can add what you need without problem as far as I can make out.


OK for now I guess, I will get back to the Forums if I face any problem.

---

