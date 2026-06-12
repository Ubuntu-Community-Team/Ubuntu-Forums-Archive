---
title: "Xfce4"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by Blue Summer on 2009-09-01
How do I actually install this i've downloaded a "tarball?" and it just opens up a load of folders and stuff can't seem to find an install icon or something don't really know what to do here if it was a .deb it'd have an installer thingy right? First day on ubuntu for a few years sorry forgotten everything. And if anyone could kindly explain the "sudo apt-get" command i'd really appreaciate it! :popcorn: Thanx -Rob

---

### Post by bodhi.zazen on 2009-09-01
Sounds as if you are new ?

See : [InstallingSoftware - Community Ubuntu Documentation]("https://help.ubuntu.com/community/InstallingSoftware")

Use the repositories =)

```
sudo apt-get install xubuntu-desktop
```

To compile see : [CompilingSoftware - Community Ubuntu Documentation]("https://help.ubuntu.com/community/CompilingSoftware")

---

### Post by NinjaNumberNine on 2009-09-01
Here is a list of the packages. You could just go in your package installer (Synaptic in Gnome, Adept Package manager in KDE) but othewise just type ```
sudo apt-get install
```then type (with spaces separating)all the packages you want to add. Then, enter and when it finishes, logout and "choose session" and pick XFCE. Good luck! :D 
[XFCE PACKAGENAMES]("http://www.xfce.org/documentation/4.0/userguide/xfce4-install")

---

### Post by Blue Summer on 2009-09-01
Thanx for the help guys, tried some stuff like sudo apt-get install xffm which is the package name? And I get : 

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


same with using sudo apt-get install xubuntu-desktop

Read some stuff on installing but it didnt mention how to install a tarball only a .deb and synaptic etc. I can't find anything on synaptic when I searched for "Xfce" thanks anyways tho guys.

---

### Post by SunnyRabbiera on 2009-09-01
you may have an update running in the background try a logout.

---

### Post by NinjaNumberNine on 2009-09-01
Oh, were you running Synaptic when you ran the commands? That's what the error means. Two package managers cannot run at the same time, and an terminal is considered a package manager *while installing a package*. So basically shut down any other P.Ms and updates like Sunny said.

---

### Post by Blue Summer on 2009-09-01
> **NinjaNumberNine said:**
> Oh, were you running Synaptic when you ran the commands? That's what the error means. Two package managers cannot run at the same time, and an terminal is considered a package manager *while installing a package*. So basically shut down any other P.Ms and updates like Sunny said.


yeah you were right mate. Still can't figure out how to download it though, can't find it on synaptic and that link you gave me ninja I can't find the part i need to type to download the whole of XFCE4 not just the different parts.

---

### Post by SunnyRabbiera on 2009-09-01
> **Blue Summer said:**
> yeah you were right mate. Still can't figure out how to download it though, can't find it on synaptic and that link you gave me ninja I can't find the part i need to type to download the whole of XFCE4 not just the different parts.

use synaptic to install xubuntu-desktop.
Problem solved.

---

### Post by Blue Summer on 2009-09-01
> **SunnyRabbiera said:**
> use synaptic to install xubuntu-desktop.
Problem solved.

Went into synaptic searched for "xbuntu" couldn't find anything

---

### Post by SunnyRabbiera on 2009-09-01
> **Blue Summer said:**
> Went into synaptic searched for "xbuntu" couldn't find anything

its xubuntu, not xbuntu

---

### Post by Blue Summer on 2009-09-01
yeah sorry typo, i typed it into search and nothing mate.

---

### Post by ks07 on 2009-09-01
> **Blue Summer said:**
> yeah sorry typo, i typed it into search and nothing mate.
It's in the universe repository. You need to go to System > Admin > Software Sources and check the box besides "Community maintained Open Source software (Universe)".

Now go into synaptic and search again for xubuntu-desktop.

---

### Post by Blue Summer on 2009-09-01
> **ks07 said:**
> It's in the universe repository. You need to go to System > Admin > Software Sources and check the box besides "Community maintained Open Source software (Universe)".

Now go into synaptic and search again for xubuntu-desktop.


was already ticked mate, still nothing.

---

### Post by ks07 on 2009-09-01
> **Blue Summer said:**
> was already ticked mate, still nothing.
It's gotta be in there somewhere. I can't think why it's not working. Try ```
sudo apt-get install xubuntu-desktop
``` again. Sorry I can't help you anymore. :(

---

### Post by Blue Summer on 2009-09-01
> **ks07 said:**
> It's gotta be in there somewhere. I can't think why it's not working. Try ```
sudo apt-get install xubuntu-desktop
``` again. Sorry I can't help you anymore. :(

rej3kt@Rej3kt:~$ sudo apt-get install xubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xubuntu-desktop is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



i am right in using the terminal/command line to write all this in yeah? Thanx for trying anyways = )

---

### Post by halitech on 2009-09-01
it's already installed

[color="red"]xubuntu-desktop is already the newest version[/color]

log out and at your log in screen,  you'll see an option that says Sessions, click that and choose Xfce then log in and you'll be in Xubuntu

---

### Post by NinjaNumberNine on 2009-09-01
If all that works and you can get in XFCE, then Congrats! Also, those links I gave you are mostly kind of for enhancement, but if you installed all the ones in the first category you would have had the XFCE desktop.  Most of them are not provided in the xubuntu-desktop package. :D

---

### Post by Blue Summer on 2009-09-02
> **NinjaNumberNine said:**
> If all that works and you can get in XFCE, then Congrats! Also, those links I gave you are mostly kind of for enhancement, but if you installed all the ones in the first category you would have had the XFCE desktop.  Most of them are not provided in the xubuntu-desktop package. :D

Got it working thanks for the help guys! Just wondering why I don't have the normal XFCE start bar at the bottom of my screen, it looks very similar to gnome does this one... :S

edit: Ninja 9, I kinda get ya, most of those package names don't work with my terminal and the command sudo apt-get for some reason. a couple of them do, are they out of date those package names?

---

### Post by halitech on 2009-09-02
the later versions of Xubuntu use alot of the Gnome apps and the look is very similiar to Ubuntu. You can customize to suit your needs though.

---

### Post by Blue Summer on 2009-09-02
> **halitech said:**
> the later versions of Xubuntu use alot of the Gnome apps and the look is very similiar to Ubuntu. You can customize to suit your needs though.

How do I get it back to the look of the original xfce?

---

### Post by halitech on 2009-09-02
you would need to find a picture of the default xfce install on something like Debian to get an idea what it looks like without Ubuntus changes. I don't know any more as I've customized all my toolbars and don't remember what it looks like anymore.

---

### Post by Blue Summer on 2009-09-02
[http://www.osnews.com/img/7002/xfce1.jpg](http://www.osnews.com/img/7002/xfce1.jpg)


tbh just wanted that bottom bar.

---

### Post by halitech on 2009-09-02
ok, if you move anything thats in the top bar to the bottom you can then remove the top bar.

---

### Post by cometa2k7 on 2009-09-02
> **Blue Summer said:**
> Got it working thanks for the help guys! Just wondering why I don't have the normal XFCE start bar at the bottom of my screen, it looks very similar to gnome does this one... :S

edit: Ninja 9, I kinda get ya, most of those package names don't work with my terminal and the command sudo apt-get for some reason. a couple of them do, are they out of date those package names?

Right-click the panel you want to change, then select "Customise Panel..."
From there you can change the size and position of panels, add new ones etc.

To add new applets just right click the panel, then select "Add New Items..." You can drag and drop the applets you want onto the panels (it's easier that way). If you want GNOME panel applets, just add XfApplet to the panel, then right click it and select "Properties", you may need to install the GNOME applets you want in Synaptic if they aren't already installed.

---

### Post by Blue Summer on 2009-09-02
lol this is so much ****** hassle im pretty sure i just typed sudo apt-get install xfce and it did everything for me (that was the one before breezy badger) now i'm just messing all my panels up lol

---

### Post by NinjaNumberNine on 2009-09-02
> Install XFCE alone, without Xubuntu, with this command: 

sudo aptitude install xfce4


If you want the entire Xubuntu package, which includes a full suite of software and a lot of improvements, try this command: 

sudo aptitude install xubuntu-desktop
Thats from [here]("https://help.ubuntu.com/community/Installation/LowMemorySystems"), check [it]("https://help.ubuntu.com/community/Installation/LowMemorySystems") out.

---

### Post by gjoellee on 2009-09-02
You have a choice...

You can use the heavily customized Xubuntu desktop which is slow and not any feaster then Ubuntu's gnome desktop:
```
sudo apt-get install xubuntu-desktop
```

Or you can use the lightweight vanilla Xfce desktop which is quite fast (can get it a lot faster on other distributions).
```
sudo apt-get install xfce4
```

---

