---
title: "Installing GnoMenu..."
date: 2010-02-11
forum: New to Ubuntu
---

### Post by benjamin.s.vaccaro on 2010-02-11
Hello, I have recently undergone some renovations of everything in Ubuntu. I've added beryl themes to Emerald Theme Manager, added folder styles and control styles to Appearance and now I have discovered that I can change the GnoMenu (as I learned its called). So I've downloaded the zips I liked from [www.gnome-look.org](www.gnome-look.org) and then I extract but I cannot figure out how to apply it or choose different themes for GnoMenu. 

This is what I have done so far.
Installation on Ubuntu:

Save the GnoMenu file to your desktop (Gnomenu)

[https://launchpad.net/gnomenu/trunk/2.2](https://launchpad.net/gnomenu/trunk/2.2)

Once it's downloaded, right-click the file and choose 'Extract Here'.

Next you need to make sure the correct dependencies are all installed, so open a terminal (Applications >> Accessories >> Terminal) and type in :

sudo apt-get install python python-xdg python-cairo python-gconf python-xlib deskbar-applet

Next, in the terminal you need to change in to the directory you extracted earlier. Type in:

cd ~/Desktop/gnomenu

now type:

sudo make install

REF: [http://gnome-look.org/content/show.php/HOW+TO+INSTALL+%22GNOMENU%22?content=108571](http://gnome-look.org/content/show.php/HOW+TO+INSTALL+%22GNOMENU%22?content=108571)

The problem is that I don't understand, "This will install GnoMenu, it comes with some themes installed by default. Once this is done, you'll be able to right-click on your panel and select 'Add to panel'. Select GnoMenu from the list, it'll add an icon to the panel, right-click the icon and choose 'Preferences'. From there you'll be able to install the menu themes you've downloaded and download others from the Internet."

Where on 'Add to Panel' should I see this program GnoMenu? Because I don't have one. 

any ideas?

---

### Post by k3lt01 on 2010-02-11
What version of Ubuntu are you using? Beryl was remerged back into Compiz a few years ago so it is possibly old if you have a newer version of Ubuntu.

---

### Post by benjamin.s.vaccaro on 2010-02-11
9.04

---

### Post by k3lt01 on 2010-02-11
> **benjamin.s.vaccaro said:**
> 9.04 And you installed Beryl themes? Are they available in the repos?

---

### Post by benjamin.s.vaccaro on 2010-02-11
Beryl themes are used by the Emerald Theme Manager, my issue is with the GnoMenu, I don't know if they are made in beryl or what. Beryl is just the category name on [www.gnome-look.com](www.gnome-look.com) for Emerald Themes. There is a separate category called GnoMenu....thats where my issue is.

---

### Post by k3lt01 on 2010-02-11
What I am trying to point out is you may be inadvertently using incompatible software. If you mix and match software that is old in a new system you may be causing problems without even knowing it.

I might also ask have you asked about this on gnome-look?

---

### Post by benjamin.s.vaccaro on 2010-02-11
I haven't, if that is the case, do you know of any ways to modify the "gnomenu" if thats what its called? It has to be possible to change the interface right?

---

### Post by k3lt01 on 2010-02-11
I'd be asking and searching in the Desktop Environment section of this forum.

---

### Post by benjamin.s.vaccaro on 2010-02-11
I'll try that, thanks for the suggestions.

---

### Post by wojox on 2010-02-12
Reboot your computer and then add to panel ;)

---

