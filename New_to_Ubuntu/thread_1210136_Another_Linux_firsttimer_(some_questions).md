---
title: "Another Linux firsttimer (some questions)"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by Struki on 2009-07-11
Hi all! As it is said I've installed ubuntu for the first time, and it's a new undiscoverd land form me, and I'm liking it. Anyway since im switching from XP I would like some things to stick in ubuntu.
1. So how do you creat XP like shortcuts on gnome ubuntu desktop, and im not talkin about application launcher or a location launcher. I want to open folder, and drive partitions over my desktop launchers/shortcuts, witch the latter dont allowe me. I tried "make link" dragin it to the desktop, but when i reboot it reports that its broken, or the (partition) launcher is  just removed from desktop.
2. What is the easiest way and quickest way, or how to install adobe flash?

Consider that I'm expirienced computer user, only not in linux :P, so u can trow anything at me I'll manage (more or less), but since I don't know my way round linux yet, you could present any explanations in a "for-a-child-manner".
):P

---

### Post by nhasian on 2009-07-11
the easiest way to create a shortcut (called links in linux) is to use the middle mouse button to drag and drop the item where you'd like the shortcut created.

the fastest way to install flash is to open up a terminal from applications->accessories and typing in:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by QIII on 2009-07-11
For an application, just drag an icon off your panel (or from the Applications menu) on to your desktop.  The icon will also stay on the menu.

For a folder, go to the directory in the file browser, right click a folder, select "create link" and then drag the link on to your desktop.

---

### Post by kixome on 2009-07-11
I dont undrstand your english in your first question. What exactly are you trying to do?
flash is easy open add/remove, search for flash or adobe =whala obviously, get flash 10

---

### Post by kixome on 2009-07-11
are you trying to mount a secondary drive?

---

### Post by jerome1232 on 2009-07-11
> **Struki said:**
> Hi all! As it is said I've installed ubuntu for the first time, and it's a new undiscoverd land form me, and I'm liking it. Anyway since im switching from XP I would like some things to stick in ubuntu.
1. So how do you creat XP like shortcuts on gnome ubuntu desktop, and im not talkin about application launcher or a location launcher. I want to open folder, and drive partitions over my desktop launchers/shortcuts, witch the latter dont allowe me. I tried "make link" dragin it to the desktop, but when i reboot it reports that its broken, or the (partition) launcher is  just removed from desktop.
2. What is the easiest way and quickest way, or how to install adobe flash?

Consider that I'm expirienced computer user, only not in linux :P, so u can trow anything at me I'll manage (more or less), but since I don't know my way round linux yet, you could present any explanations in a "for-a-child-manner".
):P

1. Connected external drives should be showing up on your desktop by default as long as they are being mounted under /media or in your home directory. 

If it's an internal drive and you need help with changing the mount point to one of those locations just ask :) 
Post your fstab file to help us help you. To do that type this command into a terminal and post the output, this command just read the contents of a file (/etc/fstab) and prints them on the screen.
```
cat /etc/fstab
```

2. Open a terminal and type this
```
sudo apt-get install flashplugin-nonfree
```
What that does

sudo - escalate to root privileges temporarily, you will be prompted for a password just enter your users password

apt-get - this is a package manager for debian based systems, it's how ubuntu tracks your installed programs, it also allows you to install programs from a HUGE online repository maintained by the community and also by Canonical.

install - this just tells apt-get that we want to install a package

flashplugin-nonfree - This is the name of the package that installs adobe's flash plugin, it will integrate with popular browsers seamslessly (like opera/firefox)

---

### Post by PureLoneWolf on 2009-07-11
> **Struki said:**
> 
1. So how do you creat XP like shortcuts on gnome ubuntu desktop, and im not talkin about application launcher or a location launcher. I want to open folder, and drive partitions over my desktop launchers/shortcuts, witch the latter dont allowe me. I tried "make link" dragin it to the desktop, but when i reboot it reports that its broken, or the (partition) launcher is  just removed from desktop.


Actually, you can use a launcher to do what you want - Right click the desktop and choose "Create Launcher"  in the box that appears, click on "Application" and change it to "Location".

On top of that, it sounds like you have NTFS drives that only mount when you click them in nautilus.  Install pysdm, this is a gui that will allow you to configure your fstab file so that the drives will be automounted and available for your links.

```
sudo apt-get install pysdm
```

Hope that helps

---

### Post by Struki on 2009-07-11
> **PureLoneWolf said:**
> 
On top of that, it sounds like you have NTFS drives that only mount when you click them in nautilus.  Install pysdm, this is a gui that will allow you to configure your fstab file so that the drives will be automounted and available for your links.

```
sudo apt-get install pysdm
```Hope that helps

THANK YOU! thats it! I have 2 ntfs partitions. BUT, my folder links still dont work I've tried all of the above, draging, making links, and such, but as I said when I reboot my desktop link has that "broken/not working" sign and it's dead (*sob*sob*). Could that also be cause of my ntfs partitions, cause the folders im trying to link are on them?

---

### Post by PureLoneWolf on 2009-07-11
Try pysdm as I suggested.  It will list all of your available hard disks and their partitions.  You can specify to mount the NTFS drives at boot and ensure that they are not read only.

This way, your links will work each time.

Alternatively, when you boot up, go to the Places menu and choose the hard disks that you are referring to - At this point, your broken links should start working.

*EDIT*

Additionally, once you have installed pysdm, you will find it under the "Administration Menu" (System/Administration/Storage Device Manager.  I should have mentioned this before - my apologies.

---

### Post by theozzlives on 2009-07-11
I don't "do" icons on the desktop, I like a clean one (did in XP also). I drag folders to the left pane of Nautilus and it shows up in "Places".

As far as Flash, you may as well get the whole *shabang* and go:
```
sudo apt-get install ubuntu-restricted-extras
```

Welcome to the Ubuntu family.


EDIT: you can also create a side panel like so:

---

### Post by Struki on 2009-07-11
Pysdm worled like a charm, thanks for that i got my shortcuts.

But my flash problem remains, or so it seems. The real problem are flash players, like youtobue. They are all "lagy" and runing real slow while in linux, and at first I read that it could be due to bad flash file, but I installed it and I still got the sam problem, and some of my "dirty"(if u know what i mean, redtube wink wink) video players on the net are also unwatchable, so does any1 got an idea what could be the problem?

---

### Post by Struki on 2009-07-11
> **theozzlives said:**
> I don't "do" icons on the desktop, I like a clean one (did in XP also). I drag folders to the left pane of Nautilus and it shows up in "Places".

As far as Flash, you may as well get the whole *shabang* and go:
```
sudo apt-get install ubuntu-restricted-extras
```Welcome to the Ubuntu family.


EDIT: you can also create a side panel like so:

What will that get me?

---

### Post by carml on 2009-07-11
You'll get some Microsoft's fonts,the adobe flash player,the Sun Java Virtual Machine etc.

---

