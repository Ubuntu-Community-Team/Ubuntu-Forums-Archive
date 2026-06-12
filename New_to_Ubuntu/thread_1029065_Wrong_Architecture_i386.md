---
title: "Wrong Architecture i386"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by Darkvengence on 2009-01-03
I'm rather new to Linux and Ubuntu, well actually pretty much completely new, I've had Ubuntu for a day or so now and I keep getting this 'Wrong Architecture i386' error when ever I try to install a .deb package that I downloaded, for instance Adobe Flash Player.

I tried to find something about it and couldn't really find anything, although I did find something saying that it was specific to 64 bit systems, but I have a 32bit one.

Does anyone know what might be the problem? Or even how to fix it? Any help is appreciated.

---

### Post by hansdown on 2009-01-03
Hi darkvengence.

Go to applications> terminal.

Input >  uname --all

---

### Post by jamesrl on 2009-01-03
uname -m will say what architecture your system is using.  It probably will say something like x86_64, which will tell you to download deb's compiled for 64 bit architecture.

EDIT: I'll add that you can install 32 bit (i386) debs on a 64 bit machine (x86_64) if you really want to, by running in compatibility mode.  It's slightly more difficult, but relatively easy to do.  (Basically install the required libraries yourself (or install something in the repository that requires most of them like acroread or wine), and then install using 'dpkg --force-architecture the_32_bit_binary.deb'

---

### Post by jamesrl on 2009-01-03
Also, the default method to install programs is not to download them yourself.  Try using a package manager, its much simpler.  Open synaptic (System->Administration->Synaptic Package Manager), and select flashplugin-nonfree (make sure you have multiverse repository enabled; In synaptic, go to Settings->Repositories and on the first page multiverse is the fourth option down.  Actually it makes sense to enable all of the software sources.)

The package manager downloads the right package (and all required dependencies) for what you want, and installs them for you (as well as keeps you informed of updates).

Note: the flashplugin-nonfree doesn't mean it costs money to download/use--it doesn't.  It means that the source-code isn't publicly available.  [So its free as in beer, not free as in liberty.]

---

