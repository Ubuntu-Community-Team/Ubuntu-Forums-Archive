---
title: "New to Ubuntu"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by Caboose104 on 2009-08-05
Hey, I just got Ubuntu, and I need some help getting things started on my new OS. When I tried to watch a youtube video, I had to download flash player but there were four different ones I had to choose from, and I still don't know which one to do! I finally downloaded one, and it won't open or anything to install. So can anyone help me with this problem and list some apps/programs that I could use to get myself on track. Also can you tell me some problems I may run into being new to Ubuntu and Linux and how to solve them.

---

### Post by SunnyRabbiera on 2009-08-05
Welcome!
To start off with for your flash issue you may wish to start with Adobes flash website:
[http://get.adobe.com/flashplayer/?promoid=DXLUJ](http://get.adobe.com/flashplayer/?promoid=DXLUJ)

Download and install the one for Ubuntu 8.04 in the pulldown (.deb), it saves on some of the confusion

---

### Post by Caboose104 on 2009-08-05
Also I got this message when I try to install things. "Error: Dependency is not satisfiable" Anyone know what it means? And when downloading things, which type do I download, I know there is .deb, .rpm, and other ones. Can anyone tell me how to find out which I should get? Also im using the version 9.04 if that Helps anyone.

@Sunny
Thanks :). When I tried to download that, this came up "Error: Dependency is not satisfiable: libnspr4-dev"

---

### Post by SunnyRabbiera on 2009-08-05
Ubuntu uses the .deb installer format.
In linux there is more then one kind of installer so it pays good to know what version you use.
For your dependency issue I am unsure, are you using the 64bit Ubuntu?

---

### Post by wojox on 2009-08-05
Download .deb version.

What does it say when you run in terminal:

```
uname -m
```

---

### Post by SunnyRabbiera on 2009-08-05
For your issue try installing the file you need here:
[http://packages.ubuntu.com/jaunty/libnspr4-dev](http://packages.ubuntu.com/jaunty/libnspr4-dev)

make sure you know what version you are using, 64bit or 32.

---

### Post by super kim on 2009-08-05
Hi, i'm a noob (i hate that term of phrase soo much) and i find the best way to install things is with the synaptic package manager. it always installs the software and will automatically install any depencies too, it is verry neat, and i think the safest way to install things properly
with regards to the flash (and any other software) search the synaptic package manager for flash, completely remove the ones you installed then search for "adobe flash" you'll want the one called "flashplugin installer" thats the one you need for youtube bbc facebook etc etc...

---

### Post by Caboose104 on 2009-08-05
Now when I try to download that, it says Error:Wrong Architecture. :(

---

### Post by Caboose104 on 2009-08-05
> **wojox said:**
> Download .deb version.

What does it say when you run in terminal:

```
uname -m
```

It says i686

---

### Post by bugritall on 2009-08-05
What CPU are you using and what flavour of Ubuntu 9.04, 32-bit or 64-bit?

Edit:
I see it's 32-bit! Whenver you are presented with a choice of software download, choose the 32-bit version.

---

### Post by Caboose104 on 2009-08-05
Yea, so the packages thing that sunny said I should download didn't work and I'm really confused lol.

---

### Post by Ji Ruo on 2009-08-05
> **Caboose104 said:**
> Yea, so the packages thing that sunny said I should download didn't work and I'm really confused lol.

There's a really simple way to get your flash working, and also get a lot of the other things you'll want like mp3 playback, java, the microsoft fonts and (all but one of) the dvd packages. Go to Applications>Accessories>terminal, then type in```
sudo apt-get install ubuntu-restricted-extras
```enter your password and follow the prompts, and you will get all of the restricted extras in one go. (You can copy and paste as well, to paste into the terminal its Ctrl-Shift-V).

I think this might be helpful to you - [http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)

---

### Post by super kim on 2009-08-05
> **bugritall said:**
> What CPU are you using and what flavour of Ubuntu 9.04, 32-bit or 64-bit?

Edit:
I see it's 32-bit! Whenver you are presented with a choice of software download, choose the 32-bit version.

is it possible to install a package for 64 bit when i'm running a 32 bit system if i am using the synaptic package manager? i've always assumed that all the software listed is for 32 bit. (or 64 bit depending on your system)

---

### Post by bugritall on 2009-08-05
I'm sure you're right about Synaptic, **super kim**. I was thinking about downloads like the one for Adobe's Flash, where it's left to the user to select the correct version.

---

