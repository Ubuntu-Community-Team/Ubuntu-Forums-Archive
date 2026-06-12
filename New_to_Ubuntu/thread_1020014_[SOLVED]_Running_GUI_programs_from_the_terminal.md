---
title: "[SOLVED] Running GUI programs from the terminal"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by thenocturnalhoodie on 2008-12-23
Hey guys,
quick question. 

I've got my machine set to boot up right into the terminal. (I prefer it that way. The GNOME kind of irks me every now and then). But I was wondering if it is possible for me to say, run firefox from the terminal, so I wouldn't have to run GNOME before running firefox. Or do I have to already be in the gnome?

Thank you.

---

### Post by Idefix82 on 2008-12-23
You have to run some graphical interface like GNOME to be able to use firefox. However, you can use a text mode browser, like Lynx for example. Here is a list of the most popular ones: [http://en.wikipedia.org/wiki/List_of_web_browsers#Text-based]("http://en.wikipedia.org/wiki/List_of_web_browsers#Text-based")

---

### Post by andrewc6l on 2008-12-23
You can't run GUI programs from a terminal unless there's a display somewhere that the GUI program can draw to. (So, if you had another machine that had X running, you could set DISPLAY=my.other.machine:0.0 and use xhost to give permission for your machine on the machine with the display - but then Firefox would display on that machine, not locally.)

---

### Post by Eisenwinter on 2008-12-23
The only type of "graphical interface" you can run under a terminal, is called a "curses GUI".

For "full blown GUI" applications, you'll need to have at least the X server running with a window manager (like Openbox, Fluxbox, Metacity, and so on).

---

### Post by thenocturnalhoodie on 2008-12-23
> **Idefix82 said:**
> You have to run some graphical interface like GNOME to be able to use firefox. However, you can use a text mode browser, like Lynx for example. Here is a list of the most popular ones: [http://en.wikipedia.org/wiki/List_of_web_browsers#Text-based]("http://en.wikipedia.org/wiki/List_of_web_browsers#Text-based")

Alrighty.
So what would be the command for running it?
```
sudo lynx open
```
?

---

### Post by Idefix82 on 2008-12-23
First
```
sudo apt-get install lynx
```
and then the most basic usage would be
```
lynx http://www.google.com
```
or any other address. For more versatile usage type
```
man lynx
```
and see what options you can use. You can for example use the up and down arrows to scroll through hyperlinks and enter to follow hyperlinks.

---

### Post by Xavieran on 2008-12-23
I wouldn't use lynx as it's interface is not very user friendly and it doesn't render CSS. Go for links or elinks.

sudo apt-get install elinks

---

### Post by snova on 2008-12-23
Try this:

```
startx /usr/bin/firefox
```

This will start the X server for the sole purpose of running Firefox.

And **only** Firefox. Nothing else, not even a window manager.

---

### Post by oldos2er on 2008-12-23
"sudo lynx open"

 Lynx doesn't require X, and I don't think you really want to run it as root, so "lynx" would be the command. But, as was mentioned, try elinks instead.

---

