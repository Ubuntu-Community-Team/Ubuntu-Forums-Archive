---
title: "Does Linux have an equivalent of &quot;Device Manager&quot; in Windows?"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-03-07
Does Linux have an equivalent of "Device Manager" in Windows?  

Someplace where it tells you all of the hardware that is installed in your computer?

---

### Post by teward on 2011-03-07
To my knowledge, in an out-of-the-box install of Ubuntu (which when I reference Ubuntu i of course am including all Ubuntu variants), there is no GUI program to do this (GUI is a graphical user interface, like the device manager of Windows).

I know of a few CLI (command-line interface) commands that'll spit out a list of hardware, but its in no way a method to get a complete list.


However, I found a GUI package (called gnome-device-manager) which might do what you're looking for, but i havent extensively tested it, so i can't vouch for its effectiveness just yet.

***EDIT***
I've had some time to mess around with it a tiny bit, and it does show you all the devices on your system, but unlike the Windows Device Manager, you cannot enable/disable hardware, nor can you change its properties through the GUI (note that in Ubuntu 10.04, the version number for the program is 0.2-3, which means it isnt even fully developed software, or at least the versions in the repos arent).

---

### Post by Hakunka-Matata on 2011-03-07
several ways to do it.

from the Terminal```
sudo lshw
```

my machine takes a while (couple of seconds) to gather all the information then spits it out.

if you want to spit it out to a file, ```
sudo lshw > ~/Desktop/hardware
``` for instance

---

### Post by Hakunka-Matata on 2011-03-07
if you want a gui version, search in "Synaptic Package Manager" System > Administration > Synaptic Package Manager for "device manager"

---

### Post by teward on 2011-03-07
> **Hakunka-Matata said:**
> several ways to do it.

from the Terminal```
sudo lshw
```my machine takes a while (couple of seconds) to gather all the information then spits it out.

if you want to spit it out to a file, ```
sudo lshw > ~/Desktop/hardware
``` for instance

True, that would work, but in the defense of the beginning user, I think they'd all rather use GUI programs to show this, rather than grep (which is the Linux version of "search" for a text file) a file for what they're looking for  :/


> **Hakunka-Matata said:**
> if you want a gui version, search in  "Synaptic Package Manager" System > Administration > Synaptic  Package Manager for "device manager"

The closest thing is that GUI package I mentioned in my first response (check my edits for details).

---

### Post by Hakunka-Matata on 2011-03-07
```
lspci
lsusb
lsdev
```

and the list goes on.........

---

### Post by Hakunka-Matata on 2011-03-07
[https://help.ubuntu.com/community/UsingTheTerminal#System%20Information%20Commands]("https://help.ubuntu.com/community/UsingTheTerminal#System%20Information%20Commands")

---

### Post by Learning Linux 2011 on 2011-03-07
Ahh, ok, found it.

---

### Post by Hakunka-Matata on 2011-03-07
> **EvilPhoenix said:**
> True, that would work, but in the defense of the beginning user, I think they'd all rather use GUI programs to show this, rather than grep (which is the Linux version of "search" for a text file) a file for what they're looking for  :/




The closest thing is that GUI package I mentioned in my first response (check my edits for details).

Your reply came in whilst I was preparing a reply, sorry didn't see it before I replied.  Several times no less!  

Hopefully the new user will learn the usefulness of the CLI before too long though, it is too useful, nay, essential..........  MO

---

### Post by Learning Linux 2011 on 2011-03-07
Yeah, I grew up with DOS, so a command line isn't a new concept to me.  It is just learning new things.  Alot to take in, alot to learn.

---

### Post by Learning Linux 2011 on 2011-03-07
So looks like the "lshw" is sort of like "List Hardware" and then there are more specific versions, like "List USB", "List PCI", etc.

---

### Post by teward on 2011-03-07
> **Learning Linux 2011 said:**
> So looks like the "lshw" is sort of like "List Hardware" and then there are more specific versions, like "List USB", "List PCI". etc.

Yeppers.  The GUI program I mentioned runs using the HAL daemon (Hardware Abstraction Layer), and it does stuff similar to lshw.  Cept in a GUI setup :P

---

### Post by Hakunka-Matata on 2011-03-07
yes, you get it.  There are simply loads of things one can do with the terminal, and once one gets a bit used to it, often you'll find it's easier, faster, and reproducable.  For instance, type```
history
``` if you issued a command recently but don't recall what it was, like me!!  and the file output pipe is great to "Dump" for instance a history to a simple text file to look at, and learn

```
history > ~/Desktop/clihistory
```

---

### Post by Hakunka-Matata on 2011-03-07
You're aware pretty much everything is case sensitive too?  Filenames, commands, switches, you name it............

---

### Post by Learning Linux 2011 on 2011-03-07
Yes, I'm picking stuff up.  I remember (although have to remind myself) that Linux is case sensitive.  I've found that using the up and down buttons on the keyboard allow you to cycle through previous commands.

I think I remember hearing about the history command, but thanks for reminding me.  That is where you get the entire list of all the commands you typed, right?

Still working on the switches.  "Dir" in DOS (same as "ls" in Linux) only has a few switches, but "ls" seems to have a lot more.

I'm still trying to work out the Linux directory structure.

---

### Post by Hakunka-Matata on 2011-03-07
to see switches and more to any given command, like ls, use the manual```
man ls
``` fyi, if you don't already know that.  And oh yea, to get out of the 'manual', letter "q" is the word, and that's not case sensitive!  go figure..  that one drove me crazier in the beginning, I couldn't clear the terminal............

---

### Post by stinkeye on 2011-03-07
```
sudo lshw -html > ~/hardwarespecs.html
```
Will give you a  html file of hardware.

---

### Post by inobe on 2011-03-07
> Does **Linux** have an equivalent of "Device Manager" in Windows?

similar, but handling drivers aren't the same.

---

### Post by teward on 2011-03-07
> **inobe said:**
> similar, but handling drivers aren't the same.

Note that your image is in KDE.  I dont have a screenshot of the gnome-device-manager, but i personally much prefer the command line.  (perhaps i'm strange...?)

---

