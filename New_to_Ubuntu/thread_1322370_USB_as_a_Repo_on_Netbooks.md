---
title: "USB as a Repo on Netbooks"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by tom.swartz07 on 2009-11-10
Hi everyone,

i need really quick help with a simple question.

I have a netbook (eeepc to be exact) that has ubuntu 9.04 installed on it via a live usb.

HOW can i make it so that the driver updates (specifically the restricted wifi driver) and other major packages are installed from the live usb?

I know that you go into software sources and check off the box that says to use the cd as a repo, but i cannot figure out how to point it at the usb instead of the cdrom (that doesnt exist).

any help asap would be greatly appreciated! I would like to quickly get wifi for my friend on his netbook here, so that i could finish my other work. haha

Thanks!

---

### Post by jms1989 on 2009-11-10
Give this a shot, open your software sources app and click on the "Other Software" tab. you should be able to enter "file:///path/to/usb/repo version repo-type" and it would work. Should work like a local repo stored on the hdd.

---

### Post by tom.swartz07 on 2009-11-10
> **jms1989 said:**
> Give this a shot, open your software sources app and click on the "Other Software" tab. you should be able to enter "file:///path/to/usb/repo version repo-type" and it would work. Should work like a local repo stored on the hdd.

ok- i understand what you are getting at, but i cant seem to make the command acceptable to the sources.

the live usb is mounted at /media/UBUNTU LIVE/

how would i formulate the command?

---

### Post by jms1989 on 2009-11-11
I'm not sure if this would work but perhaps try "file:///media/UBUNTU%2FLIVE/ version repo-type". I myself would just create a link to the usb disk to eliminate the space. In the repo line, you'll need to replace "version" with the repo version you have created, like intrepid would just use intrepid but that that largly depends on what you name your repo. The "repo-type" could just be "main" if you'd like but same rule applies as "version". Keep in mind, to use a usb stick as a repo, you'll need a directory setup as a proper repo system. Just look at ubuntu's repo directory listing as an example. [http://archive.ubuntu.com](http://archive.ubuntu.com)

[http://ubuntuforums.org/showthread.php?t=352460](http://ubuntuforums.org/showthread.php?t=352460) <- Here's how, mind you, the dvd section can be left out for a simple hard drive/flash drive based repo.

Cheers!

---

