---
title: "Amarok 2.0"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by maheshjr2000 on 2008-12-12
Im pretty sure that its already in the Kubuntu repositories but how do I grab it for Ubuntu? Can I just install it from the repository or should I just download the source and compile?

---

### Post by Dj Melik on 2008-12-12
[http://www.kubuntu.org/news/amarok-2.0](http://www.kubuntu.org/news/amarok-2.0)

---

### Post by maheshjr2000 on 2008-12-12
unfortunately those are kubuntu instructions I am running Ubuntu 8.10 there is no instruction set for those.

---

### Post by albinootje on 2008-12-12
According to this 
[http://packages.ubuntu.com/search?keywords=amarok](http://packages.ubuntu.com/search?keywords=amarok)
amarok is still 1.4.x in all (K)ubuntu releases.

---

### Post by Gepetto on 2008-12-12
It's the same idea, go to System, Administration, Software Sources, and add 

deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main 

to the 3rd party software sources. Then you should be able to use synaptic to install Amarok 2

---

### Post by albinootje on 2008-12-12
If you still want to try it, you could try the instructions for Debian Experimental. YMMV.
[http://amarok.kde.org/wiki/Download:Debian](http://amarok.kde.org/wiki/Download:Debian)

---

### Post by maheshjr2000 on 2008-12-12
the package manager still isnt showing the correct package. Ah forget it Ill just compile it myself.

---

### Post by Funnnny on 2008-12-12
I think in Ubuntu it must be "amarok-kde4"
try > sudo apt-get install amarok-kde4

---

### Post by maheshjr2000 on 2008-12-12
thats what I looked for in the package manager :( BINGO :D it worked though :D the package manager just didnt show the package for some reason :D

---

### Post by RedRat on 2008-12-12
This brings up the question, can you install Amarok 2 in Ubuntu 8.04. I am still running 8.04 and will do so for the next 6 months or so. Will it run? I currently use the 1.4 version, which is ok, but the front end for the new Amarok looks a bit better.

---

### Post by maheshjr2000 on 2008-12-12
Red rat I dont see why not. Theres no system dependencies that I am aware of.

---

### Post by tgalati4 on 2008-12-12
Don't get your hopes up.  I'm using 2.0 (actually 1.98  ) on OpenSUSE11.1 and it crashes often and my sandisk player doesn't show up and podcast management is funky.

Last.fm works OK and music lyrics seem to show up.

Not quite ready for prime time.  KDE 4.1.3-Release 4.3 is shaping up, but it's buggy as well.

---

### Post by Funnnny on 2008-12-13
> This brings up the question, can you install Amarok 2 in Ubuntu 8.04. I am still running 8.04 and will do so for the next 6 months or so. Will it run? I currently use the 1.4 version, which is ok, but the front end for the new Amarok looks a bit better.
Just use your Amarok 1.4 and forget about Amarok 2, it's like a piece of sht

---

### Post by VastOne on 2008-12-13
I Agree 100000000 Percent

> **Funnnny said:**
> Just use your Amarok 1.4 and forget about Amarok 2, it's like a piece of sht

---

### Post by RedRat on 2008-12-14
> **VastOne said:**
> I Agree 100000000 Percent

The consensus here seems to be to stick with 1.4.  Also noted that on the Amarok web page, sounds like they have not implemented a lot of stuff too. I think I will wait a bit.

---

### Post by noren on 2009-01-25
> **Gepetto said:**
> It's the same idea, go to System, Administration, Software Sources, and add 

deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main 

to the 3rd party software sources. Then you should be able to use synaptic to install Amarok 2

hi my system is showing the following please help

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A7CEB1D8A626B42

regards

---

### Post by IanW on 2009-01-25
> **noren said:**
> hi my system is showing the following please help

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A7CEB1D8A626B42

regards

That's OK, just accept the error and continue.
Public keys are still "coming soon" for PPAs.

---

