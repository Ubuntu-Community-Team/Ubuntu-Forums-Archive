---
title: "Cant install python 3.0.1"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by Beest on 2009-06-19
I am new to Ubuntu and cant figure out how to install python 3.0.1. I've tried to extract it but nothing seems to work.Do I have to use the terminal and if so, how do I do it. I am definitely a newbie.Any info would be helpful

---

### Post by starcraft.man on 2009-06-19
Uhm, are you trying to learn python? I can't recommend resources off the top of my hand, but a quick google for python ubuntu tutorials and I'm sure you'll find something good.

As to install, 3.0.1 is in the repos to my knowledge. The package is called python3 I believe. You can open up System > Administration > Synaptics and search for python3/python3-all and install graphically (just check the boxes and push apply) or simply use the following command in the terminal Applications > Accessories > Terminal to install all that you need.

> sudo aptitude install python3 python3-all

Have fun!

---

### Post by blackxored on 2009-06-19
If you're installing from source, as I can guess, since if you're using apt wouldn't have those problems. I'm not sure if that version is included yet at all, I think not.

```

tar jvxf Python3.0.1.tar.bz2
cd Python3.0.1/
./configure
./make
sudo make install

```if you downloaded the .tar.gz then the command is tar zvxf ... 
After you install it please go ahead to your linux manual (kidding...)

EDIT: well I've checked python-3.0.1 is on the ubuntu repos, so skip all that and go with apt.

---

### Post by raydeen on 2009-06-19
Your best bet is to go to Synaptic Package Manager (under System) and search for idle-python3.0 and install it from there. After it's installed, launch it from the Applications/Programming menu. You'll then have Python 3 and the IDLE development environment.

---

### Post by starcraft.man on 2009-06-19
I just had a look at the version in the repos, and it is indeed 3.0.1. Here is the output of the show command, it's in universe section. Just pointing that out, however ya, you can still make and install from source if you wish. Up to you. Replying to blackxored btw.

> aptitude show python3
Package: python3
State: not installed
Version: 3.0.1-0ubuntu4
Priority: optional
Section: universe/python
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 77.8k
Depends: python3.0 (>= 3.0.1), python3-minimal (= 3.0.1-0ubuntu4)
Suggests: python3-doc (>= 3.0.1-0ubuntu4), python3-tk (>= 3.0.1-0ubuntu4),
          python3-profiler (>= 3.0.1-0ubuntu4)
Description: An interactive high-level object-oriented language (default python3 version)
 Python, the high-level, interactive object oriented language, includes an
 extensive class library with lots of goodies for network programming, system
 administration, sounds and graphics. 
 
 This package is a dependency package, which depends on Debian's default Python
 version (currently v3.0).

---

### Post by Beest on 2009-06-20
I did what you instructed and it seemed as though it worked. I just don't know where it is or how to start it. Its not in applications. I think your instructions worked. I just have to figure this out. This is definitely not Windows. Thanks, your help was appreciated.

---

### Post by Beest on 2009-06-20
Did what you said, but python was not in applications/programming menu.I'll have to read this ubuntu manual. Thanks for your help.

---

### Post by starcraft.man on 2009-06-20
> **Beest said:**
> I did what you instructed and it seemed as though it worked. I just don't know where it is or how to start it. Its not in applications. I think your instructions worked. I just have to figure this out. This is definitely not Windows. Thanks, your help was appreciated.

Your welcome and good luck. I'm afraid I'm not really familiar with python so I can't help you past this point. I advise you google for some good guides. Something like "ubuntu python tutorial", I'm sure good stuff will pop up. Heck, I bet if you search these forums you can come up with something good to get ya started.

Good luck.

Note: Any applications that don't add to the applications menu can be launched usually with their package name. Just open a terminal and type it in then enter. In this case, it's python3.0. In this instance however, your dealing with a programing language, it doesn't come with a GUI by default I don't think. Google is your friend as indicated and I'd go look for a good tutorial.

---

### Post by Beest on 2009-06-20
I tried what you said and got this error message:   tar: Python3.0.1.: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: tar.bz2: Not found in archive
tar: Error exit delayed from previous errors

Thanks for the help and you're right, I really should read the manual; which I will do soon. Maybe today.

---

### Post by Beest on 2009-06-20
[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG]You were right. I typed in "python3.0" in terminal and it worked. I guess I got brand new toy to play with. Your help was significant, thank you again.

---

