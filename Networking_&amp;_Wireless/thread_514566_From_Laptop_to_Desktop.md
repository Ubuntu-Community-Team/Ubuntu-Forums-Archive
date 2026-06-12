---
title: "From Laptop to Desktop"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by ccalvinfowler@aol.com on 2007-07-31
II have reently installed Xubuntu on my laptop and my desktop.

I have downloaded several packages and installed them on my laptop(wireless connection via Bcurger King) free internet.

Now, I would like to install some of them on my desktop which does not have an internet connection, but i do have a router.

My router is a SpeedStream, and my network is RTL 8139(wired).  My laptop does have a wired connection also.

I figured that it would be easy to transfer files, but I don't know how.

I have enabled shared folders on my laptop, but I can't on my desktop w/o installing a package.

What can  do?

---

### Post by spd106 on 2007-08-01
The desktop should have the necessary client software already installed. So you should be able to  fetch the files you need without installing anything.

I have found that it sometimes easiest to copy the package you want to install to the package cache under /var/cache/apt/archives/, now they will be found automatically. You can also use gdebi, but that means you have to install the packages manually in the right order.

---

### Post by ugm6hr on 2007-08-01
> **spd106 said:**
> The desktop should have the necessary client software already installed. So you should be able to  fetch the files you need without installing anything.

I have found that it sometimes easiest to copy the package you want to install to the package cache under /var/cache/apt/archives/, now they will be found automatically.

The first time you try to enable a Shared Folder - it installs Samba / Cif.  Try doing that - and it should tell you which files it is trying to install.  Just find them in /var/cache/apt/archives on your laptop - copy to USB-stick - then copy to same location on desktop (using *gksudo thunar*).

Then go to Applications->System->Shared Folders and try again.

---

### Post by ccalvinfowler@aol.com on 2007-08-02
I have managed to find one blank cd and I copied the ndiswrapper packages onto it and installed on desktop.  I was hoping that this would enable my wireless network adapter that is on my desktop.

But i have run into some more difficulties.

1. the wreless network adapter on my desktop is a Lynksys WU54bg, but Xubuntu sees it as an rt2500.

2. I have downloaded the rt2500 package on to my laptop, but I can't copy to desktop.

3. I tried to open the shared folder on my desktop and it told me that i have to install samba

4. when looking in Synaptics, the following are installed already --  libsmbclient, samba-common, smbclient, xubuntu-system-tools

so, what do i do now.  i am stumped

any help would be greatly appreciiated.

---

### Post by ugm6hr on 2007-08-03
> **ccalvinfowler@aol.com said:**
> any help would be greatly appreciiated.

You need to be clear what you want help doing.  Or open multiple threads for each problem, otherwise it will start to get confusing.

The issues as I see it:

**1. You want to install packages from Synaptic on desktop**
Use a USB flash disk (very cheap) to transfer files from laptop (where you download them too) to desktop.  Synaptic can generate download scripts to automate the process if Xubuntu is on both laptop and desktop.  Although it's just as easy to copy manually from *var/cache/apt/archives* on laptop to same folder on desktop.  Of course, if you manage to get file-sharing working, the USB flash disk will become unnecessary (see point 3).  Have a read through this thread: 
[http://ubuntuforums.org/showthread.php?t=512364](http://ubuntuforums.org/showthread.php?t=512364) (particularly posts 5-7).

**2. You want to get your wifi adapter to work on desktop**
This will be tricky - first need to know if your desktop adapter is USB or PCI.  I can't find it on [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/)

**3. You want to file-share between laptop and desktop**
Not sure exactly what networking setup you have.  Sounds like you have an ethernet cable plugged into desktop that connects to a router, but how does the laptop connect to the router (you mention it has a wired connection - is it plugged in at the same time)?  This will be helpful, I think: [http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734)

If you don't understand my questions, just try to reiterate what you are trying to achieve.

---

