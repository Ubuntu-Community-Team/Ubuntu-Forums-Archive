---
title: "Where are my programs?!?!?"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by DavidOfLondon on 2010-08-24
Hi,

I really am reaching the edge of sanity now and could really do with your help.

My question is so basic and yet the manual and internet give me very very conflicting or confusing answers.

I just installed libcurl via the software centre. So where the hell is it?!?!?

I seem to have this basic problem all the time - seemingly no one thinks it important to write a proper guide to Ubuntu file structures. With Windows you just use explorer and locate your program files folder or whatever, but with Ubuntu nothing so basic seems to be possible.

So my question is this - where in the name of God is Ubuntu installing programs?! If I download and install something how come it doesn't show up on the applications tab and how do I go about adding it to that tab?

This is now my SEVENTH major issue with Linux functionality (on very basic elements, I might add) in just 2 days. 

The major prob seems to be that the software centre doesn't act like a install wizard ought to - it doesn't tell you post install what folder the f***ing thing installed to.

And neither does the manual!

PLEASE HELP!

---

### Post by jonnywombat on 2010-08-24
If you look at the [curl and libcurl website]("http://curl.haxx.se/") you will see it is a command line tool. 

That is to say there is no gui...

---

### Post by dtoronto on 2010-08-24
could be in the /usr/lib/ directory, or the /etc/ or possibly even the /opt/ directory somewhere.  If the package manager was used it could be installed to a combination of directories.  I'm honestly not sure as I don't use the application.

---

### Post by neilms on 2010-08-24
Presumably you want to use curl?
Open a terminal and type 'curl --help'

If you want to use libcurl /usr/lib
documentation is in /usr/share/lib

use the search for files utility : Places > search for files

---

### Post by oldos2er on 2010-08-24
You can check where each file in a package is installed to with ```
dpkg -L <package name>
``` or in Synaptic Package Manager by right-clicking on an installed package, Properties, Installed Files. I don't know if Ubuntu Software Center shows you this info as I don't use it.

---

### Post by M93 on 2010-08-24
u'll find it in 'Applications tab'...last item!

---

### Post by TheWeakSleep on 2010-08-24
If you can not find a program you have installed, after checking the menu, you could always perform a search.

places -- search for files

Simpler yet, create a launcher for it either on your desktop or in your menu.

However, like others have said before, this is a command-line application, so it can only be run via the terminal.

Make sure you know what you're installing :) have fun :)

---

### Post by uRock on 2010-08-24
Searching through the root directory is much easier than you think, you just have to know where it is.

---

### Post by kroq-gar78 on 2010-08-24
Yes libcurl is a command line tool. This means you have to open Terminal  (Applications => Accessories => Terminal) and type in curl --help (I think) and you're done.

---

### Post by Miljet on 2010-08-24
> seemingly no one thinks it important to write a proper guide to Ubuntu file structures

No one bothers to define Ubuntu file structure since it was defined for Unix years ago and is standard for all Linux distributions.

Here is one link. [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

A Google search will turn up lots more guides.

---

### Post by ironic.demise on 2010-08-24
fullcircle magazine described the file structure quite well...
there are plenty of guides on the structure.

---

### Post by eeperson on 2010-08-24
For an explanation of where files are stored, type the following in the terminal:

```
man hier
```

---

### Post by jazzerit on 2010-08-25
another way to find where a program is located is using the whereis command. For example, to find where curl is located, type whereis curl

---

### Post by migs73 on 2010-08-25
look here;
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

This explains why you are having the problems you are. Please keep an open mind. It'll be worth it in the end.

---

### Post by DavidOfLondon on 2010-08-25
Thanks, I really appreciate this.

> **neilms said:**
> Presumably you want to use curl?
Open a terminal and type 'curl --help'

If you want to use libcurl /usr/lib
documentation is in /usr/share/lib

use the search for files utility : Places > search for files

---

### Post by llamabr on 2010-08-26
As many have mentioned, there's no reason to know where curl lives, since it's already defined in your path.  Just open a terminal, and type

```
curl
```

If you really need to know where it lives, or for any other, you can locate it with

```
which curl
```

from the terminal

---

