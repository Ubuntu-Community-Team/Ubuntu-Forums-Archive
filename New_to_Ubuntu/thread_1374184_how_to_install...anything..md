---
title: "how to install...anything."
date: 2010-01-06
forum: New to Ubuntu
---

### Post by ethan073 on 2010-01-06
i can't figure out how to install anything on this netbook remix.
i want to download and use wine so that i can access itunes.
i also want to download unetbootin so that i can create a bootable flash of Ubuntu and try that out.
but once i download something, i have no freakin clue how to actually install and use it. i've been searching the internet for 3 days trying to figure this out. 

i was a windows user before i accidentally installed the ubuntu netbook remix. now i would like to check out the linux perspective but...man i'm having a really hard time doing so.

---

### Post by Bölvaður on 2010-01-06
first of all.
What do you need to accomplish with iTunes?

it might be way too much work to get it to work for a program that doesn't accomplish the task as well as some other programs.




for playing music :
Rythmbox which is already installed.
Amarok is often considered to be the best audioplayer since beginning of time and you can install it by finding one of the following ( Add/Remove, Ubuntu software store, synaptic packagemanager) and install it from there.... or [click this link]("apt:amarok")

if you want iTunes, but only for playing music and NOT for connecting to iPod, then go here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=18308]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18308")
All you need to do is:
[LIST]
[*]Install WINE ([click this link]("apt:wine"))
[*]Double click the iTunes program/installer/binaries
[/LIST]


!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! now I am not happy :(:(:(:(
> I want to be able to sync my ipod with my music library and create playlists. i also need to connect with itunes to reformat my ipod back to factory settings.


ok let rethink this.


TASKS[LIST=1]
[*]sync ipod with my music library
[*]sync ipod & create playlists
[*]format ipod
[/LIST]

Solutions:

1. install iTunes on a virtualmachine running xp
2. find and install a program that does everything on the task list.


ok number 2 is more interesting.

depending on what ipod you have you might be in luck.


// attention. ignor sad_iq (the user below) he doesn't address your problem.


SOLUTION: (wait a sec)



Songbird:
[URL="http://ubuntuforums.org/showpost.php?p=8468997&postcount=2"]http://ubuntuforums.org/showpost.php?p=8468997&postcount=2
[/URL]
[Link to a .deb installer for songbird]("http://www.getdeb.net/updates/Ubuntu/9.10/?q=songbird")
Make sure to check that guy's links out if you want to use them.

This program is similar to iTunes.




Rythmbox:
perhaps more preferable program for you to use.
it's already installed like I said.... just open it and see what you can figure out.

---

### Post by ethan073 on 2010-01-06
I want to be able to sync my ipod with my music library and create playlists. i also need to connect with itunes to reformat my ipod back to factory settings.

---

### Post by sad_iq on 2010-01-06
Go to: [https://help.ubuntu.com/]("https://help.ubuntu.com/") , choose the version of ubuntu you installed (open a terminal and type [COLOR="RoyalBlue"]cat /etc/issue.net[/COLOR] to find out) and read some of the info there. It basically tells you to play with System -> Administration -> Synaptic Package Manager and the repository button found in there :)


P.S. Woow...I'm a sloooow typer :D

---

### Post by ethan073 on 2010-01-06
how do i open a terminal?


i've looked into songbird. it sounded very interesting but unfortunately they do no support the use of ipods from the information i gathered from their website.

---

### Post by Bölvaður on 2010-01-06
> **ethan073 said:**
> how do i open a terminal?

1. Applications &#8594; Accessories &#8594; Terminal
2. you dont have to open the terminal (I HIGHLY doubt it)


also if 1. doesnt work try this:
1a. Alt+F2 , type : gnome-terminal

---

### Post by ethan073 on 2010-01-06
ahh i got to the terminal via the gnome-terminal command, but i have not been able to find the applications - accessories - terminal folders anywhere.

i clicked the link you sent me for Install Wine and now its up. how come i had no luck with it by clicking "download" on websites? what was i missing?

---

### Post by Hospadar on 2010-01-06
Well first off,
Installing things in ubuntu (or linux in general) tends to be a very different process than installing in windows.  In windows you pretty much always download an installer (which is just a program) then you run it and the installer does whatever it pleases and you hope to god that the uninstaller does what it is supposed to do if you ever need to uninstall things.

In ubuntu (and other flavors of linux as well) almost everything is installed through a package manager.  Ubunutu (the organization) maintains a huge repository of software which is pre-packaged for your convenience.  Much of this is just re-dos of debian (another linux distribution, off of which ubuntu is based).  You generally use a package manager to install these.  The package manager automatically downloads the software, installs it, handles library dependencies, updates, etc.  It is possible to download packages and install them by hand. although that is not typically how things go.  (Usually any project serious enough to make a nice package for your convenience, will get their package into the repository).

It's also possible that a developer may just distribute source code (many of the more obscure open source projects, for example scientific packages work this way). It's easier for the developer and lighter on bandwidth.  This sort of software will come with scripts to build and install the package, typically requiring one or two simple commands in a terminal.  It's probably pretty unlikely you'll install very much this way.

Here are some good links which talk more about the nature of installation in ubuntu, some are long, and I'm linking quite a few, but they all basically say the same thing: use the package manager, pick the thing you want, click ok.

[Official ubuntu wiki page]("https://help.ubuntu.com/community/InstallingSoftware")
[some other page]("http://amitech.50webs.com/installing/index.php.html") (looks pretty complete, though possibly slightly outdated)
[Installing on a command line]("http://martin.ankerl.com/2007/04/19/how-to-install-anything-in-ubuntu-condensed/"), basic commands (my preferred mode, very fast and powerful, but slightly arcane).  If you you want to go this route, I'd suggest googling for any of the well written linux command line tutorials that are out there.

I found all these pages with a quick google.  There's probably a writeup or guide for just about anything you might want to do in linux, especially in the beginner department.  I hope you have the patience to stick through learning the differences and quirks of your linux system, I loves me some linux desktop.

---

### Post by ethan073 on 2010-01-06
also, i have a 16g solid state drive on this hp mini netbook i'm using, and for obvious reasons want to install anything and everything i can onto my external hard drive. how do i tell it where to install to?

---

### Post by Bölvaður on 2010-01-06
> **ethan073 said:**
> how come i had no luck with it by clicking "download" on websites? what was i missing?

I dont know.
Depends on what you have been clicking. Normally websites cannot be really trusted 100% to be authentic. What we use is a software repository (my link activated a program on your computer which connected to that software repository).

From reading on this forum on what other ipod people are doing it looks like the safest bet is to run iTunes on a virtual machine.
That is safe because it is very hard to circumvent the locks apple has placed on the latest ipods.

The older ones have been hacked so you are able to use rythmbox, songbird, amarok and GTKpod.


So if you dont know what generation your ipod is of, just install Virtualbox by either [clicking this link]("virtualbox-ose") or open Synaptic package manager (System &#8594; Administration &#8594; Synaptic....) or alternativly Alt+F2 and type *gksu synaptic*

some years ago I used to have tinyxp on a virtiual machine, but if you have a windows cd laying about you can also use that.

---

### Post by Bölvaður on 2010-01-06
> **ethan073 said:**
> also, i have a 16g solid state drive on this hp mini netbook i'm using, and for obvious reasons want to install anything and everything i can onto my external hard drive. how do i tell it where to install to?

depends on how you install it :P

if you find the program as just a folder you can just place the folder where you want.
if you install from repo then it will be placed on your / partition, which might be your ssd. Programs can be moved to a different location and then just link that folder to the old one with a symlink. Hope that makes sense to you.

---

