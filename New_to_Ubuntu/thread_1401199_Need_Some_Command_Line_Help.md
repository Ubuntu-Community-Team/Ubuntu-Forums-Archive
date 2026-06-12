---
title: "Need Some Command Line Help"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by The Sorrow on 2010-02-07
Ok, Ive been working on a Linux Server (9.10) and i need some commands to manage the files on it. I have some basic commands but i am very confident in calling myself an amateur. I'm mainly interested in figuring out how to modify .txt and .config files. I know the cat command and that's about it. Any help is GREATLY appreciated.

---

### Post by mushwars on 2010-02-07
```
nano /etc/resolv.conf
```[s]ctl +&#12288;[s]&#12362;[/s]

sorry my computer is inputing only in japanese for some reason on a different one.

you can save with ctl +&#12288;&#12362;[/s]

was fiddleing with locales, and was inputing in english for like 10 seconds then it started with anthy input method.

---

### Post by Dullstar on 2010-02-07
I really don't understand why you would need to use the terminal for modifying a .txt file.  Maybe there's something I don't know about...

EDIT:  Oh wait.  Server. I know nothing about server Ubuntu.

---

### Post by dyingsun on 2010-02-07
There's a list of useful commands here:

[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)

A very useful starting point. Good luck!

---

### Post by werecatomega on 2010-02-07
you can use the nano command, it is pretty easy to learn the combinations

you can also use vi/vim, but i have no experience with that, for i can't figure it out

---

### Post by NightwishFan on 2010-02-07
On a server some may not want or require a GUI. However personally I use Nano, as was said above.

---

### Post by The Sorrow on 2010-02-07
> **Dullstar said:**
> I really don't understand why you would need to use the terminal for modifying a .txt file.  Maybe there's something I don't know about...

Ubuntu Server is strictly command line without a GUI, so im stuck with command line.

I also see this character all over the place "|" What is is and whats the key command to input it?

---

### Post by Paul41 on 2010-02-07
As mushwars suggested you can use nano.

---

### Post by mushwars on 2010-02-07
forgive me for my REALLY strange post. I fiddled with my locale and I couldnt type in anything but japanese.


DONT FIDDLE WITH locales..

there is vim and nano I like nano for simple config edits ( ctl + o to save ctl + x to quit ctl + w to search ctl + w ctl + r to search replace )

vim you need to hit 'i' to edit
then to save hit escape then :wq

---

### Post by audiomick on 2010-02-07
> **The Sorrow said:**
> 
I also see this character all over the place "|" What is is and whats the key command to input it?
That is a pipe.
[http://en.wikipedia.org/wiki/Pipe_%28Unix%29](http://en.wikipedia.org/wiki/Pipe_%28Unix%29)
I don't know where it is on an english keyboard, but it will probably be in the third layer somewhere, i.e. Alt Gr + somekey

On the German keyboard is is Alt Gr + <

---

### Post by pirateghost on 2010-02-07
> **audiomick said:**
> That is a pipe.
[http://en.wikipedia.org/wiki/Pipe_%28Unix%29](http://en.wikipedia.org/wiki/Pipe_%28Unix%29)
I don't know where it is on an english keyboard, but it will probably be in the third layer somewhere, i.e. Alt Gr + somekey

On the German keyboard is is Alt Gr + <

shift + \

---

### Post by Paul41 on 2010-02-07
> **audiomick said:**
> That is a pipe.
[http://en.wikipedia.org/wiki/Pipe_%28Unix%29](http://en.wikipedia.org/wiki/Pipe_%28Unix%29)
I don't know where it is on an english keyboard, but it will probably be in the third layer somewhere, i.e. Alt Gr + somekey

On the German keyboard is is Alt Gr + <

On the English (US anyway, not sure if UK is different) keyboard it is over the \.

---

### Post by nc_jed on 2010-02-07
@pirateghost:  If you're coming from the Windows/DOS command prompt, try [www.ss64.com](www.ss64.com).  It has a very handy cross reference of Linux and DOS shell commands,  I.e. "Well in DOS I would have done dir to see the files, wonder what that is in Linux..."

vi is a great editor, but a not quite a user friendly one (if you ask me).  see here for a getting started guide.  [http://www.tuxs.org/vi.htm](http://www.tuxs.org/vi.htm)

-Jed

---

### Post by pirateghost on 2010-02-07
> **nc_jed said:**
> @pirateghost:  If you're coming from the Windows/DOS command prompt, try [www.ss64.com]("http://www.ss64.com").  It has a very handy cross reference of Linux and DOS shell commands,  I.e. "Well in DOS I would have done dir to see the files, wonder what that is in Linux..."

vi is a great editor, but a not quite a user friendly one (if you ask me).  see here for a getting started guide.  [http://www.tuxs.org/vi.htm](http://www.tuxs.org/vi.htm)

-Jed


LOL what?

i have been using Linux CLI for 10 years.

somebody asked where the | was....

---

### Post by The Sorrow on 2010-02-07
ok found it thanks guys

---

