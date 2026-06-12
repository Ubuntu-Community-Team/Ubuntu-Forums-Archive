---
title: "Installing libflashplayer on amd x64"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by typos1 on 2009-06-29
Anyone know about this? I ve tried to do it several ways. How do I move a .so file to a location? I ve tried  but it doesnt seem to work

---

### Post by Celauran on 2009-06-29
> **typos1 said:**
> How do I move a .so file to a location?

```
mv origin destination
```

---

### Post by scrooge_74 on 2009-06-29
If I remember right, dont move it you just make a link, this is what I did last week:

go to the directory you want it to be in and then do something like this

sudo ln -s /usr/lib/flashplugin-nonfree/libflashplayer.so

---

### Post by typos1 on 2009-06-29
I m supposed to "extract/unpack the package then move the libflashplayer.so file to either /home/'user'/.mozilla/plugins (make the plugins folder) or /usr/lib/mozilla/plugins, thats all you have to do to install flash." I ve tried places but when the box pops up theres no way to add a folder and dragging and dropping doesnt work

---

### Post by Arup on 2009-06-29
sudo mv libflashplayer.so /usr/lib/mozila/plugins

---

### Post by typos1 on 2009-06-29
Right, I get it. But I ve got to create a new folder called plugins in mozilla first but it wont let me create one

---

### Post by SuperSonic4 on 2009-06-29
```
mkdir ~/.mozilla/plugins
```

or

```
sudo mkdir /usr/lib/mozilla/plugins
```

---

### Post by Arup on 2009-06-29
If you have Gnome Ubuntu it has Mozila insalled and that directory already exists by default.

---

### Post by typos1 on 2009-06-29
> **SuperSonic4 said:**
> ```
mkdir ~/.mozilla/plugins
```or

```
sudo mkdir /usr/lib/mozilla/plugins
```

Ah, I see I like commands much quicker than messing about with menus! I suppose theres a list of them all somewhere

> **Arup said:**
> If you have Gnome Ubuntu it has Mozila insalled and that directory already exists by default.

Yes have gnome and the directory mozilla/firefox exists but not mozilla/plugins. I m supossed to create it in mozilla. The only /mozilla I can find is this one. Not even sure if its the right one. I just want to be able to watch iplayer and for flash type vids to play properly

---

### Post by scrooge_74 on 2009-06-29
check again you should have several directories under /usr/lib I have directories for mozilla and firefox and those have a sub called pluggins.

If you put the so file link here then flash is enable for other users (if you have them), if you only put it inside your home folder then only you have flash.

If I'm not mistaken the guides say to link the file not move it (at least the old one I remember). And if Im not mistaken if you install the packages flash non free that is in Synaptic you dont have to manually do this. I had to do it manually cause I was installing firefox 3.5 so I had to do the linking by hand

---

### Post by typos1 on 2009-06-29
The package manager doesnt find it

---

### Post by typos1 on 2009-06-29
Stuck it in the right folder (I think) doesnt make any difference-still wont play iplayer stuff

---

### Post by scrooge_74 on 2009-06-29
package name is flashplugin-nonfree and is on the multiverse repositories. What I don't know if it exist for the 64 bit version.

In which directory did you put it

I was reading abour Iplayer and found this, don't know if it helps you

[http://bbciplayerlinux.sourceforge.net/index.php/Main_Page](http://bbciplayerlinux.sourceforge.net/index.php/Main_Page)

---

### Post by oldos2er on 2009-06-29
There's an install script here: [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by typos1 on 2009-06-29
I was using a guide that was slightly later- [http://ubuntuforums.org/showthread.php?t=1121740](http://ubuntuforums.org/showthread.php?t=1121740)
and another one that I cant find now

There are people who say they can ru iplayer without using Wine

---

