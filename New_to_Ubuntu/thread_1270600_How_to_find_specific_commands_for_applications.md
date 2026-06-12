---
title: "How to find specific commands for applications"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by webwiller on 2009-09-19
Hi there!
I'm trying to make new icons and the process I think is fine, but when I come across the "command" box, I dont know where to find it and how to recognize it. Going through properties of other icons (as firefox) I found out they are somewhat strange (eg: firefox %u ).
Is there an easy way to recognize them? Or to search 'em for?
Ty ;)

---

### Post by ankspo71 on 2009-09-19
Hi,

I was just taught this myself. go to the terminal and type the following:

Option 1
```
firefox --help
```

Option 2
```
man firefox
```
There is nothing in there for firefox, but if you use man in the terminal it will tell you about alot of different programs or commands.

hope this helps get you started,
James

---

### Post by ankspo71 on 2009-09-19
Hi Again,

I'm not sure what the %u stands for in "firefox %u". If you wanted to make an internet shortcut for only firefox to use, use the command 

```
firefox www.google.com
```

Also, shortcuts can be dragged from the menu onto the desktop or the gnome panels. I just thought I would mention that since you said you were creating shortcuts. There is also a tiny utility in the gnome panel to make shortcuts. Just right click on the panel, select "add to panel", select application launcher or custom application launcher and create them. Sometimes you will have to press the browse for file button, because command "shortcuts" doesn't work for all applications.

James

---

### Post by drs305 on 2009-09-19
You can find many of the commands and locations for applications by typing:

```

which <packagename>
whereis <packagename>

```
The first returns the run command, the second the file locations.
Example:  which gimp ;   whereis gimp

Of course, if you aren't sure of the packagename, this may not be all that intuitive. You can type the start of the name, such as *fi* for firefox and then tab twice to see the available commands beginning with *fi*

You can also open Synaptic, highlight the package, then select Properties, Installed Files to see where they reside.

If you enter the run command of many apps into a custom launcher it will often automatically enter the icon. Even if you don't want to create a panel shortcut, it's a quick way to find the icon location as you create the shortcut (doubleclick the icon to reveal it's location).

---

### Post by sandyd on 2009-09-19
> **ankspo71 said:**
> Hi Again,

I'm not sure what the %u stands for in "firefox %u". If you wanted to make an internet shortcut for only firefox to use, use the command 

```
firefox www.google.com
```Also, shortcuts can be dragged from the menu onto the desktop or the gnome panels. I just thought I would mention that since you said you were creating shortcuts. There is also a tiny utility in the gnome panel to make shortcuts. Just right click on the panel, select "add to panel", select application launcher or custom application launcher and create them. Sometimes you will have to press the browse for file button, because command "shortcuts" doesn't work for all applications.

James
the %u means to run firefox with the logged in user.
it, however will work fine without the %U
In fact, a lot of apps work fine without the %u

---

### Post by ankspo71 on 2009-09-19
Thanks Carlee, I wondered what that was too.

---

