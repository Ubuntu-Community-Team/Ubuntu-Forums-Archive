---
title: "Help with Jargon/terms"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by smcrossman on 2011-06-05
Okay, I'm getting a little overwhelmed with jargon. Would like to check on some of it and my understanding or lack of.  I haven't actually looked for a wiki or thread that covers this... I just started making my list of things. If there is an easy resource for this please provide it and feel free to close this thread!

DEB/ Debian  --base linux code Ubuntu is based on?  basically these packages should always work in Natty if compatible with this version?

KDE  -- ?  another base linux code? equivilant to DEB?  compatability?

Terminal  -- coding window opened to view code or run commands?  not for code writing or editing

Gedit/ config Editor -- apps/programs that are used to edit or write code

Command Line (CLI) - alternative to terminal for running commands---not sure how to open one or use one, but do I need to know that?

X Window - ?

GNOME -- basic desktop environment for Ubuntu....has many apps & tools designed specifically for it as opposed to designed for the system level

Unity -- the new desktop environment display option with Natty.  Runs only if hardware is up to specs, optional....can be 2D or 3D ....can opt out back into default GNOME display if prefer

CCSM - Compiz - 

Virtual Terminal - ?

Virtual Machine - ?  I'm really needing information on this but will start a separate thread

SSH  -  a way of sharing information between specific computers?  My understanding is that it is a lot like AdHoc netwoking in Windows.  Only runs when specifically opened, not a constant flowing network

SMB (Samba)  A netnworking system that uses Windows networking as a base?

GDM -- a gnome desktop display package/system?

GTK -- ?

keyring/ keys  vs passwords & password managers?   probably need to search on this and then a separate post?

screenlets ?

Tasks (vs. packages, screenlets, etc) ?

Panel -- versions in both GNOME and Unity....separate creatures; basically a toolbar of sorts that either you add the apps/launchers or "shortcuts" to or that is pre-designed as part of the desktop environment.  GNOME panels are very user adaptable. Unity panels don't allow much user personalization (color, text, position, etc)

nautilus --  seeing a lot of references to it....what is it exactly? 

there are others I'm pretty comfortable with that are fairly basic.  To the mods: sorry if there is an easy resource for this that I simply missed.

---

### Post by IWantFroyo on 2011-06-05
KDE- K Desktop Environment. Go check out kde.org and kubuntu.org.
Terminal- Run ctrl-alt-t, and try typing "nano". This is where you can program (or replace nano with another text editor.
X Windows- X.Org controls the graphical interface. 
Virtual Machine- Running another operating system inside of your current one. You can go to the Software Center and install VirtualBox to try it out.
Screenlets- Widgets that you can put on your desktop.
GTK- The GIMP Toolkit. Go to gtk.org.
Tasks?
Hope I helped!

---

### Post by Paqman on 2011-06-05
> **smcrossman said:**
> 
DEB/ Debian  --base linux code Ubuntu is based on?  basically these packages should always work in Natty if compatible with this version?


Debian is a Linux distro, like Ubuntu. Ubuntu is based on Debian, it takes Debian and makes some changes to some of the desktop and default packages. All the changes are designed to make it more usable for an average person.


> KDE  -- ?  another base linux code? equivilant to DEB?  compatability?

KDE is a desktop environment. The standard desktop environment of Ubuntu is called Gnome. KDE is basically a just a different interface and a different set of default applications. There is a KDE version of Ubuntu called Kubuntu.

> Terminal  -- coding window opened to view code or run commands?  not for code writing or editing

No, you can do just about anything in a terminal window. There are terminal apps to do photo editing, browse the web, edit photos, etc.

> Gedit/ config Editor -- apps/programs that are used to edit or write code

Gedit is a just a text editor. You could use it to write code, lots of people do. Gconf editor is a tool for changing some of the settings of Gnome. 

> Command Line (CLI) - alternative to terminal for running commands---not sure how to open one or use one, but do I need to know that?

CLI = terminal

> X Window - ?

X is the system that runs the display. Don't worry too much about it, that's behind-the-scenes stuff

> GNOME -- basic desktop environment for Ubuntu....has many apps & tools designed specifically for it as opposed to designed for the system level

Spot on.

> Unity -- the new desktop environment display option with Natty.  Runs only if hardware is up to specs, optional....can be 2D or 3D ....can opt out back into default GNOME display if prefer

Pretty much. Technically Unity is a new "shell" or interface for Gnome that runs through Compiz.

> CCSM - Compiz - 

CCSM = Compiz Config Settings Manager. Compiz is the system that does nice 3D effects on your desktop like wobbly windows and dropshadows.

> Virtual Terminal - ?

Virtual Machine - ?  I'm really needing information on this but will start a separate thread

A VM is a virtual computer that you can run on your desktop. You can install an operating system into the VM, and that system will think it's running on a real machine. So you could run a copy of Windows, or OS X or another Linux distro on your desktop.

> SSH  -  a way of sharing information between specific computers?  My understanding is that it is a lot like AdHoc netwoking in Windows.  Only runs when specifically opened, not a constant flowing network

SSH is just a security protocol. You can use it to create secure communications between two machines, what you do with that link is up to you.

> SMB (Samba)  A netnworking system that uses Windows networking as a base?

SMB is the Windows file sharing protocol. Samba is a Linux implementation of it, and allows Linux machines to share in a way Windows machines understand.

> GDM -- a gnome desktop display package/system?

Gnome Display Manager. You see it when you log in.

> GTK -- ?

Gnome Tool Kit. A tool kit of bits and pieces that help developers write Gnome apps.

> keyring/ keys  vs passwords & password managers?   probably need to search on this and then a separate post?

The keyring is a secure store for passwords and encryption keys. Your wifi passwords, for example, get stored there.

> screenlets ?

I think Windows calls them widgets? Little doodads that sit on your desktop and tell you things.

> Tasks (vs. packages, screenlets, etc) ?

A task is a program that's running. A package is a piece of software, all packaged up for installation.

> Panel -- versions in both GNOME and Unity....separate creatures; basically a toolbar of sorts that either you add the apps/launchers or "shortcuts" to or that is pre-designed as part of the desktop environment.  GNOME panels are very user adaptable. Unity panels don't allow much user personalization (color, text, position, etc)

Pretty much.

> nautilus --  seeing a lot of references to it....what is it exactly? 

Nautilus is the file browser. Any time you're browsing through folders, you're using Nautilus.

Hope that helps!

---

### Post by JKyleOKC on 2011-06-05
And GIMP=GNU Image Manipulation Program, functionally like Photoshop but with very different interface.

GNU=GNU's Not Unix, a term originally intended to apply to an entire body of operating systems but now referring primarily to those packages maintained by the Free Software Foundation.

A "distribution" is a collection of programs, including a Linux kernel and its surrounding utilities as a minimum, and possibly many others, all tuned and tested to work together. Each distribution has a name; one of the first was Slackware. Debian is a distribution, with a name coined from that of its originator Ian and his girlfriend Deb. Ubuntu is a variant of Debian, specifically designed for ease of installation and use, and based on the Gnome window manager/development environment. Kubuntu is a variant of Ubuntu, using the KDE (Kool Development Environment) manager instead of Gnome. Xubuntu is another, using the XFCE manager and including fewer additional applications. Mint is a variant of Ubuntu. As you can see, the family tree becomes quite tangled in a hurry!

The two most widely used distribution families today appear to be Debian and Red Hat, although Slackware is still popular as well. The file layouts differ widely between the three. Many introductory books describe only the Red Hat setups and fail to mention the others, as do many how-to descriptions found on the Internet.

---

### Post by Dondermans on 2011-06-05
I found Googlubuntu invaluable in learning the ropes: [http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by JKyleOKC on 2011-06-05
You might also find this helpful: [http://www.catb.org/jargon/html/](http://www.catb.org/jargon/html/)

The Jargon File dates from the earliest days of the internet, well before the web existed. It's a gold mine of historical trivia!

---

### Post by smcrossman on 2011-06-05
Thanks so very much!   I have a really BAD HABIT of inferring information based on the material I see it in and assuming I understand it from context. Which leads to some very broad and often not so accurate interpretations when it comes to jargon and slang.

Reading through the forums things come up and terms take on an ominous tone....such as X Window....and then it pops somewhere else and I think...what the heck am I thinking? I thought I could change that or do that or.....?!

the KDE/Deb/XFC always makes me uncomfortable when looking at new/different apps.

Sounds like I have some good areas for more exploration. looking at the alternate desktop interfaces, learning more about VM (I think that may lead to answers for several of the issues that have me beating my head against the wall). The links for more information are going to be invaluable!

Back to figuring out how to best track the changes I'm making and on to setting up Samba so I can keep accessing the materials as I move from computer to computer!

---

