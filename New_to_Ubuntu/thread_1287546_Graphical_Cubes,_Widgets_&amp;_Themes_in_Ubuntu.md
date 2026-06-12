---
title: "Graphical Cubes, Widgets &amp; Themes in Ubuntu"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by ifhamr on 2009-10-10
Im totally new to UBUNTU. 

Please advice me how to enable and install 

* Themes
* Widgets 
* Rotating Desktop

eg on [http://s3.amazonaws.com/scrnshots.com/screenshots/142825/desktoppng_large](http://s3.amazonaws.com/scrnshots.com/screenshots/142825/desktoppng_large)

---

### Post by ikisham on 2009-10-10
- For themes you can download them at gnome-look.org then open system>preferences>appearance>themes and drag the downloaded folder to enable it.
- That monitoring thingy at the top-right of the screenshot is conky. You can install it and find how-to's at [http://conky.linux-hardcore.com/](http://conky.linux-hardcore.com/)
- The dock for the apps someone will tell you. I don't use.
- For the desktop effects go to system>preferences>appearance>effects and choose 'extra' (will only work with a 3D driver). Also you should install
```
sudo apt-get install compizconfig-settings-manager
```
so you can configure the effects you want to use.

---

### Post by NightwishFan on 2009-10-10
Welcome to Ubuntu forums.

You can download themes from:
[http://www.gnome-look.org/](http://www.gnome-look.org/)

Themes can be installed by dragging and dropping the .tar.gz file into the first tab of: System -> Preference -> Appearence

Some themes may say not a valid theme file, that means they have more than one theme, and you will have to unpack the tar.gz files inside it, then drag/drop them.

GTK+ is a general appearance. Metacity is a window border. Icons/Mouse etc are obvious what they are.

[LIST=1]
[*]To access 3d desktop, make sure you have desktop effects enabled in System -> Preferences -> Appearance -> Desktop Effects.
[*]Then open System -> Administration -> Synaptic Package Manager
[*]Use the search button (not the bar) to search for simple-ccsm and compizconfig-settings-manager. Right click, and choose mark for installation for both of them. Then hit apply at the top.
[/LIST]

You can go to Desktop Effects and choose the custom setting to change settings, or use the advanced one in the same menu as Appearence.

Good luck, and please ask if you have any questions.

---

### Post by ikt on 2009-10-10
the dock is Awn I think.

---

### Post by ifhamr on 2009-10-10
how do u get those app docks enabled and downloaded.??

---

### Post by NightwishFan on 2009-10-10
You should stick to supported Ubuntu applications:

You can use Applications -> Add/Remove to install applications. When the Add/Remove starts set the drop down menu to 'All Available Applications'.

You can also use Synaptic Package Manager in System -> Administration.


If you have no choice:

To install random applications on the web, I would check to see if they have an Ubuntu tutorial on how to install. It should be straightforward.

---

### Post by drumkitcat on 2009-10-29
Wow there's a lot of great information in this thread!
Thanks everyone who posted replies!
I'm going to take some serious time to learn more about these.

I just downloaded the new Ubuntu 9.10 and Kubuntu 9.10 today so I'm getting back into Linux after a short absence - my last install was Ubuntu's Edgy.

---

