---
title: "Conky, for the first time"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by jermza on 2011-07-15
I love this Conky app thing.  I've spent days googling and I can't see to find a dumbed down version of how to get it running.

Can someone be so kind as to give me a step-by-step process of how to get it running on my desktop, on the right hand side?  I've tried a few things, from copying and pasting that .conkyrc file and I don't see anything different (running 11.04).

---

### Post by snip3r8 on 2011-07-15
If you are changing the .conkyrc file and nothings happening then you probably want to fix that first,make sure that you have put the file in your home directory then restart conky 
```

killall conky
conky

```

do not run it as the root user.

---

### Post by VCoolio on 2011-07-15
You need conky itself and a config file. To generate a default config file, do: ```
 conky -C > ~/.conkyrc
```Now you have to point conky to that config, or another, like so: ```
conky -c ~/.conkyrc
```

Inside the config there is a line TEXT. Above that is settings, under that is contents displayed on the screen. Check [this link](http://conky.sourceforge.net/docs.html). The configuration settings you can use above TEXT, the Objects/variables under it.

Now play with it, get inspiration from howtos and [this insane thread](http://ubuntuforums.org/showthread.php?t=281865).

Important config options are:
own_window yes
own_window_type normal (instead of normal it can be desktop, override, dock, panel)
own_window_transparent yes (if you like)
own_window_argb_visual yes (if you like)
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

For position: 
alignment bottom_middle (or top_left or where-ever)
and adjusted by:
gap_y ?? (value in pixels, for vertical adjustment)
gap_x ??

---

### Post by jermza on 2011-07-15
I've managed to install Conky but am very stuck.  

Apparently, I need to install Conky Colors.

> Download and extract the conky-colors.tar.gz and type in terminal.
[I]make
./conky-colors --help
./conky-colors
make install[/I]

None of that works in Terminal.  It just gives me errors.  And what must I do with the downloaded file?

---

### Post by jermza on 2011-07-15
Ugh, never mind.  This is a bit beyond me.  I don't even know how to open a folder in Terminal, so I get stuck at that point.  How embarrassing.

Maybe one day, when a Dummies Guide is made, I'll get Conky running.  It's very awesome, by the looks of things!

---

### Post by Frogs Hair on 2011-07-15
This link was given to me when I started with Conky  ,  I have found a big difference with how themes are installed.  [http://ubuntuforums.org/showthread.php?p=5436679#post5437628](http://ubuntuforums.org/showthread.php?p=5436679#post5437628)

[http://www.webupd8.org/2009/05/how-to-install-and-configure-conky.html](http://www.webupd8.org/2009/05/how-to-install-and-configure-conky.html)

---

### Post by jermza on 2011-07-15
[B]> Download and extract the conky-colors.tar.gz and type in terminal in the same directory that has been extracted.
$make
$sudo make install
$conky-colors {options}[/B]


I don't know what I'm supposed to do, and no amount of googling seems to help.

I've downloaded Conky.  it's sitting in my Downloads folder.  I've managed to naviagte to that folder in Terminal.

I entered "make" but nothing happened.  

What am supposed to do with those commands?  I can't go any further.

EDIT: COnky-Colors, I mean.  Conky is running.  I'm trying to install Conky-Colors.

---

### Post by jermza on 2011-07-15
Okay, I've managed to get the previous post's issues working.  

However, when I set up Conky, a black box with white text appears on the right of my screen.  

After installing Conky Colors, ANOTHER one appears (which looks better).  When I "killall conky", both disappear, and when I enter "conky" only the (wrong) one appears.

Advice?

---

### Post by MG&amp;TL on 2011-07-15
I can't help you with your conky problems, but as they seem to be related (correct me if I'm wrong! :D) to you not having enough terminal knowledge. IF that's the case, and I'm not barking up the wrong tree, you might want to have a look at this page, which concerns basic navigation commands in a terminal:

[navigation]("http://linuxcommand.org/lts0020.php")

Oh, and:

```
cd ..
``` navigates up one folder. I ended up endlessly closing terminals for a week before I noticed this. ;)

---

### Post by VCoolio on 2011-07-15
if you just run conky, it looks for a config at some default places, doesn't find one in your case and uses a crappy default one that works in any case. If you use conky-colors, you apparently need to run the command conky-colors instead of conky. Try that.

---

### Post by jermza on 2011-07-16
Thanks, except that I get this response:

> conky-colors: command not found

I'd love some more help.  I'm so close to getting Conky (Colors) working, but I just don't have the know-how to do it alone.  

Right now, if I type in "Conky", Conky loads, but it's the ugly version.  If I "killall conky", then it goes away.

I don't know how to load Conky Colors though. 

Any help?

---

