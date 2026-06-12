---
title: "Application help"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by frogdude on 2009-03-23
Hello, I am still new to this ubuntu business, so I have a couple questions about applications.  First, is there anyplace with a near complete list of applications for download and where to get them? O r is it just a shop around find what you need setup?

My second question is: Where do I install applications so they work, and how do I make them run? Like recently I downloaded the Frets on Fire application, but I have NO idea how to start it up.:(

---

### Post by linuxguymarshall on 2009-03-23
Ok, let me start by saying, welcome to Ubuntu! 
It may be a little rough getting started but you will adapt quick. 

First thing you should know is that unlike Windows where you get a '.exe' or a '.msi' file to install something here you normally get applications in one of 3 ways.

[LIST=1]
[*]A installer package (In '.deb' or '.rpm' format)
[*]Through Synaptic (I will explain in a bit)
[*]By compiling source (Last resort, for the uber-geek or desperate man)
[/LIST]
First thing is that the Frets on Fire application you downloaded is a binary. You can run it but there are easier ways to get it. On your top bar go to Applications > Add/Remove...

Now search Frets on Fire and install it. Real simple. 

There is a much bigger list of applications in a program called Synaptic, google that to learn more about it.

---

### Post by mvalviar on 2009-03-23
> **linuxguymarshall said:**
> Ok, let me start by saying, welcome to Ubuntu! 
It may be a little rough getting started but you will adapt quick. 

First thing you should know is that unlike Windows where you get a '.exe' or a '.msi' file to install something here you normally get applications in one of 3 ways.

[LIST=1]
[*]A installer package (In '.deb' or '.rpm' format)
[*]Through Synaptic (I will explain in a bit)
[*]By compiling source (Last resort, for the uber-geek or desperate man)
[/LIST]
First thing is that the Frets on Fire application you downloaded is a binary. You can run it but there are easier ways to get it. On your top bar go to Applications > Add/Remove...

Now search Frets on Fire and install it. Real simple. 

There is a much bigger list of applications in a program called Synaptic, google that to learn more about it.

4. Through installers. Much like setup.exe in windows but usually ends in .bin

You can try Applications>Add Remove find what you need and install it.

---

### Post by frogdude on 2009-03-23
> **linuxguymarshall said:**
> Ok, let me start by saying, welcome to Ubuntu! 
It may be a little rough getting started but you will adapt quick. 

First thing you should know is that unlike Windows where you get a '.exe' or a '.msi' file to install something here you normally get applications in one of 3 ways.

[LIST=1]
[*]A installer package (In '.deb' or '.rpm' format)
[*]Through Synaptic (I will explain in a bit)
[*]By compiling source (Last resort, for the uber-geek or desperate man)
[/LIST]
First thing is that the Frets on Fire application you downloaded is a binary. You can run it but there are easier ways to get it. On your top bar go to Applications > Add/Remove...

Now search Frets on Fire and install it. Real simple. 

There is a much bigger list of applications in a program called Synaptic, google that to learn more about it.

Thank you , I know how to work synaptic, lol, and I was not aware of the capability for the add/remove/ to find applications nothe net, thank you very much for your help.

Next question, is there any plug-in or app or converter to run .exe files on linux/ubuntu?

---

### Post by Chemical Imbalance on 2009-03-23
> **frogdude said:**
> Thank you , I know how to work synaptic, lol, and I was not aware of the capability for the add/remove/ to find applications nothe net, thank you very much for your help.

Next question, is there any plug-in or app or converter to run .exe files on linux/ubuntu?

WINE is an app that has the ability to run quite a bit of windows apps with varying degrees of success.

```
sudo apt-get install wine
```


check here for compatibility with programs you want to run:[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by presence1960 on 2009-03-23
> **frogdude said:**
> Thank you , I know how to work synaptic, lol, and I was not aware of the capability for the add/remove/ to find applications nothe net, thank you very much for your help.

Next question, is there any plug-in or app or converter to run .exe files on linux/ubuntu?

Wine is very limited in what it can run successfully. Your best bet is to dual boot or run windows in virtualisation inside Ubuntu. Virtualisation though has limited or no 3d effects.

---

### Post by frogdude on 2009-03-23
Ok, and as well, I just entered Frets on Fire and it says that to get the "guitar hero" songs I need to install Ogg Vorbis Encoder, which is not on the add/remove programs list, nor can it find it in the terminal.

---

### Post by aeiah on 2009-03-23
i believe the ogg vorbis encoder is in the package vorbis-tools. you could use synaptic to search for it or if you trust me you could do 
```
sudo apt-get install vorbis-tools
```

you should of course be aware of what the command line tool apt-get does before pasting things in willy-nilly, although i guess its fairly obvious that in the command i gave it downloads and installs vorbis-tools for you. synaptic is a graphical front end for it.

---

### Post by frogdude on 2009-03-23
> **aeiah said:**
> i believe the ogg vorbis encoder is in the package vorbis-tools. you could use synaptic to search for it or if you trust me you could do 
```
sudo apt-get install vorbis-tools
```

you should of course be aware of what the command line tool apt-get does before pasting things in willy-nilly, although i guess its fairly obvious that in the command i gave it downloads and installs vorbis-tools for you. synaptic is a graphical front end for it.

my terminal doesnt do copy paste for codes, i have to manually type them in, which by default lets me know what im actually telling the computer to do.

---

### Post by mvalviar on 2009-03-23
> **frogdude said:**
> my terminal doesnt do copy paste for codes, i have to manually type them in, which by default lets me know what im actually telling the computer to do.


Ctrl-Shift-C - to copy from terminal
Ctrl-Shift-V - to paste to terminal

---

### Post by frogdude on 2009-03-23
> **mvalviar said:**
> Ctrl-Shift-C - to copy from terminal
Ctrl-Shift-V - to paste to terminal

Yes, I have tried all variations of that, and still no copy/pasting

---

