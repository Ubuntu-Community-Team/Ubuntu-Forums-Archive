---
title: "&quot;on debian do&quot; ?"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by EdwardD26 on 2009-01-14
I'm trying to install Xnee... and after running the configure it tells me im missing couple X11 things, RECORDER and Xtest

so it gives me the command to get the apt-install blah blah... its says doit on debian...


On Debian do: apt-get install libxtst-dev


where do I do this?

Consider im ultra noob, so be sure to explain step by step

---

### Post by taurus on 2009-01-14
You would run that command from a terminal.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install libxtst-dev
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Bölvaður on 2009-01-14
This is not to solve the problem but to tackle how you normally should install software.
Getting files from websites is only the last resort, this is how we do it.

A.
1. System &#8594; Administrator &#8594; Synaptic Package manager
2. put in "Xnee" into the empty search box
3. mark the Xnee package
4. accept the changes
5. review what you are going to change and accept it.

B.
1. Applications &#8594; Accessories &#8594; Terminal
2. sudo apt-get install xnee

C.
1. Applications &#8594; Add/Remove
well sadly Xnee is not on there.

D.
Go to website and follow the instructions :P

---

### Post by EdwardD26 on 2009-01-14
Sweet thanks, now...

It says I need gtk+-2.0 package...?

---

### Post by jerome1232 on 2009-01-14
> **EdwardD26 said:**
> I'm trying to install Xnee... and after running the configure it tells me im missing couple X11 things, RECORDER and Xtest

so it gives me the command to get the apt-install blah blah... its says doit on debian...


On Debian do: apt-get install libxtst-dev


where do I do this?

Consider im ultra noob, so be sure to explain step by step

Unlees you really need the bleeding edge version, why not install from the repos? Looks like version 3.02 is there. This will automatically resolve dependencies.

```
sudo apt-get install xnee
```

---

### Post by Bölvaður on 2009-01-14
> **EdwardD26 said:**
> Sweet thanks, now...

It says I need gtk+-2.0 package...?

it is strange that it is not automatically set up for you.
it should be automatically downloaded and installed if you do it via the command line (terminal): sudo apt-get install xnee

But what you should do is to copy the name of the package you are missing and paste it (ctrl+shift+v) at end of "sudo apt-get install".

like if I would be missing the x package I would go to terminal and type

sudo apt-get install x

---

### Post by EdwardD26 on 2009-01-14
sudo apt-get install xnee


I did this!
the thing is that I have no idea where the app was installed or how to run it :(

---

### Post by jerome1232 on 2009-01-14
---edit--- I installed that program to see and wow it's man page and info page are incredibly poor, also xnee doesn't seem to launch it.

So it's the hard way on this one.

I found it like this,
```
sudo updatedb   #updates a search database
locate xnee
/usr/share/xnee
/usr/share/doc/xnee
/usr/share/doc/xnee/AUTHORS
/usr/share/doc/xnee/BUGS
/usr/share/doc/xnee/NEWS.gz
/usr/share/doc/xnee/README
/usr/share/doc/xnee/TODO
/usr/share/doc/xnee/TODO.Debian
/usr/share/doc/xnee/changelog.Debian.gz
/usr/share/doc/xnee/copyright
/usr/share/man/man1/xnee.1.gz
/usr/share/xnee/example1.xns
/usr/share/xnee/pixmaps
/usr/share/xnee/simple_bash.sh
/usr/share/xnee/xndetail.jpg
/usr/share/xnee/xndetail.png
/usr/share/xnee/xnee.html
/usr/share/xnee/xnee.pdf
/usr/share/xnee/xnee.ps
/usr/share/xnee/xnee.sh
[COLOR="Blue"]/usr/share/xnee/xnee.txt[/COLOR]
/usr/share/xnee/xngener.jpg
/usr/share/xnee/xngener.png
/usr/share/xnee/xnrec.jpg
/usr/share/xnee/xnrec.png
/usr/share/xnee/xnrep.jpg
/usr/share/xnee/xnrep.png
/usr/share/xnee/xnswinp.jpg
/usr/share/xnee/xnswinp.png
/usr/share/xnee/pixmaps/pnee-record.png
/usr/share/xnee/pixmaps/pnee-replay.png
/usr/share/xnee/pixmaps/pnee-stop-mini.png
/usr/share/xnee/pixmaps/pnee-stop.png
/usr/share/xnee/pixmaps/xnee.png
/usr/share/xnee/pixmaps/xnee.xpm
/var/cache/apt/archives/xnee_3.02-0ubuntu1_amd64.deb
/var/lib/dpkg/info/xnee.list
/var/lib/dpkg/info/xnee.md5sums
```




Well I guess that txt document is the documentation, so I took a look at it and it is. looks like anothger one is at /usr/share/doc/README
```
vim /usr/share/xnee/xnee.txt
```

---

### Post by EdwardD26 on 2009-01-14
"man xnee" 

provided me with the description of the app, version, etc

no path or instructions

lol

linux is fun, I feel like im in a new world learning how it works =)

---

### Post by WitchCraft on 2009-01-14
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-cache search xnee
sudo apt-get -y install xnee

```

---

### Post by jerome1232 on 2009-01-14
from /usr/share/xnee/xnee.txt

> Xnee is a suite of programs that can record, replay and   distribute
user actions under the X11 environment.    Think of it as a robot that
can imitate the job you just   did.

   Xnee consists of one library and two applications

   cnee - command line program

   gnee - graphical user interface program

   pnee - a Gnome Panel Applet

   libxnee - library used by xnee and gnee

1.2 Xnee features


---

### Post by EdwardD26 on 2009-01-14
Yeah

I want to use pnee


How do I open it?????????

---

### Post by jerome1232 on 2009-01-14
right click on your panel, click "add to panel" find Pnee Xevent-Recorder/Replayer, click "add"

---

### Post by EdwardD26 on 2009-01-14
jerome1232   you rock, thanks.

---

