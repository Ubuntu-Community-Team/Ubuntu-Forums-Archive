---
title: "I've problem installing gimp 2.7.1!!"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-07-16
Gimp 2.6 is currently installed on my ubuntu karmic, but the multiple windows issue is confusing me a bit, so i decided to install 2.7.1 by adding both ppa and key for lunchpad repo, but some errors accrued occurred[U][I][B] in begginging of installation process:

[/B][/I][/U][PHP]$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gimp: Depends: libgimp2.0 (>= 2.7.3) but 2.6.7-1ubuntu1 is to be installed
        Depends: libatk1.0-0 (>= 1.29.3) but 1.28.0-0ubuntu1 is to be installed
        Depends: libbabl-0.0-0 (>= 0.1.3-2010020903.1~ll) but 0.0.22-1 is to be installed
        Depends: libc6 (>= 2.11) but 2.10.1-0ubuntu15 is to be installed
        Depends: libfontconfig1 (>= 2.8.0) but 2.6.0-1ubuntu12 is to be installed
        Depends: libgegl-0.0-0 (>= 0.1.2) but 0.0.22-0ubuntu3 is to be installed
        Depends: libgtk2.0-0 (>= 2.19.1) but 2.18.3-1 is to be installed
E: Broken packages
[/PHP]

what exactly happen?

---

### Post by linuxman94 on 2010-07-16
Try:

```
sudo apt-get -f install gimp
```

---

### Post by MBG1987 on 2010-07-16
> **linuxman94 said:**
> Try:

```
sudo apt-get -f install gimp
```
  
nothing change, same thing

---

### Post by mrphud on 2010-07-17
Do you have the universe and multiverse repositories enabled? It might not be able to find the appropriate packages.

Besides, cant you install gimp from the gui package manager?

---

### Post by ronnielsen1 on 2010-07-17
> Besides, cant you install gimp from the gui package manager? 	

The gimp in lucid is 2.6.8. I really don't think you can install gimp 2.7.1 in karmic because (for one) a newer version of libc6 is needed and to upgrade this file, you would have to update your whole system. Have you tried gimpshop? This makes gimp look more like photoshop.

> GIMPshop is a modification of the free/open source GNU Image  Manipulation Program (GIMP), intended to replicate the feel of Adobe  Photoshop. Its primary purpose is to make users of Photoshop feel  comfortable using GIMP. 

[http://www.gimpshop.com/](http://www.gimpshop.com/)

You can get a deb from here:

[http://rapidshare.com/files/86270575/gimpshop_2.2.11-1_i386.deb](http://rapidshare.com/files/86270575/gimpshop_2.2.11-1_i386.deb)

---

### Post by MBG1987 on 2010-07-17
> **mrphud said:**
> Do you have the universe and multiverse repositories enabled? It might not be able to find the appropriate packages.

already enabled

> Besides, cant you install gimp from the gui package manager?
I tried and got the same problem


 > Have you tried gimpshop? This makes gimp look more like photoshop.
ugly interface, thank you any other suggestions?

---

### Post by ronnielsen1 on 2010-07-18
According to your signature, you are using

> Ubuntu 9.10 Karmic Koala                                                                                      9.10 uses older lib files than newer distros do. I'm running Ubuntu 10.04

My libc6  file is 2.11.1-0ubuntu7.2.  Karmics is 2.10.1-0ubuntu15. Debian testing is 2.11.2-2
You would have to update your system to 10.04 in order to upgrade gimp

> You do not want to upgrade libc6...trust me.

Just about every app that runs under Ubuntu depends on the version you  have. That is why it won't let you upgrade.

libc6 is locked for Ubuntu...you would have to add Debian repos to be  able to upgrade and would most likely hose your system.[http://ubuntuforums.org/showthread.php?t=239626](http://ubuntuforums.org/showthread.php?t=239626)


> [COLOR=#000000][COLOR=#0000bb]gimp[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]Depends[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]libgimp2.0 [/COLOR][COLOR=#007700](>= [/COLOR][COLOR=#0000bb]2.7.3[/COLOR][COLOR=#007700]) [/COLOR][COLOR=#0000bb]but 2.6.7[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]1ubuntu1 is to be installed
        Depends[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]libatk1.0[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]0 [/COLOR][COLOR=#007700](>= [/COLOR][COLOR=#0000bb]1.29.3[/COLOR][COLOR=#007700]) [/COLOR][COLOR=#0000bb]but 1.28.0[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]0ubuntu1 is to be installed
        Depends[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]libbabl[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]0.0[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]0 [/COLOR][COLOR=#007700](>= [/COLOR][COLOR=#0000bb]0.1.3[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]2010020903.1[/COLOR][COLOR=#007700]~[/COLOR][COLOR=#0000bb]ll[/COLOR][COLOR=#007700]) [/COLOR][COLOR=#0000bb]but 0.0.22[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]1 is to be installed
        Depends[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]libc6 [/COLOR][COLOR=#007700](>= [/COLOR][COLOR=#0000bb]2.11[/COLOR][COLOR=#007700]) [/COLOR][COLOR=#0000bb]but 2.10.1[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]0ubuntu15 is to be installed
        Depends[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]libfontconfig1 [/COLOR][COLOR=#007700](>= [/COLOR][COLOR=#0000bb]2.8.0[/COLOR][COLOR=#007700]) [/COLOR][COLOR=#0000bb]but 2.6.0[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]1ubuntu12 is to be installed
        Depends[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]libgegl[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]0.0[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]0 [/COLOR][COLOR=#007700](>= [/COLOR][COLOR=#0000bb]0.1.2[/COLOR][COLOR=#007700]) [/COLOR][COLOR=#0000bb]but 0.0.22[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]0ubuntu3 is to be installed
        Depends[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]libgtk2.0[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]0 [/COLOR][COLOR=#007700](>= [/COLOR][COLOR=#0000bb]2.19.1[/COLOR][COLOR=#007700]) [/COLOR][COLOR=#0000bb]but 2.18.3[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]1 is to be installed[/COLOR][/COLOR]Your error messages tell you what it's looking for and what you have installed

---

### Post by ronnielsen1 on 2010-07-18
Update. I browsed some more and found this

[http://news.softpedia.com/news/First-Look-GIMP-2-7-1-on-Ubuntu-10-04-145681.shtml](http://news.softpedia.com/news/First-Look-GIMP-2-7-1-on-Ubuntu-10-04-145681.shtml)

> It appears that GIMP 2.7.1 is  also available for other versions of the Ubuntu operating system, such  as Karmic Koala and Jaunty Jackalope. Install it using the PPAs listed  below:
[COLOR=#008080][I]
deb [http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu](http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu)  karmic main[/I][/COLOR]

They have ppa's for lucid, karmic and jaunty. Which did you use?

---

### Post by MBG1987 on 2010-07-18
thanks to all of use, i did the following steps to install gimp2.7
1-remove gimp 2.6 or older
2-delete any newly add restores
3-update
4-install gimp
 every thong went well, enjoy gimp!

---

### Post by RodneyLee on 2010-10-11
I used this from Softpedia [http://news.softpedia.com/news/First-Look-GIMP-2-7-1-on-Ubuntu-10-04-145681.shtml](http://news.softpedia.com/news/First-Look-GIMP-2-7-1-on-Ubuntu-10-04-145681.shtml), then did apt-get update, worked perfect and its Gimp 2.7.1

---

