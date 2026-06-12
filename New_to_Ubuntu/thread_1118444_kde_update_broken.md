---
title: "kde update broken"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by rgrigga on 2009-04-07
Attempting to resolve a VIA graphics card/Google Earth problem, I tried to update KDE 4.1 to 4.2.2 through the adept tool that shows up in the tray at the bottom of the screen.

after following what I thought was a normal process, I am now trapped in the command line console.

tried "sudo apt-get install kde" but the list of dependencies is ridiculously long and it says "broken packages" at the bottom.

EEK- PLEASE HELP sorry I am only 3-days linux-deep!

---

### Post by rgrigga on 2009-04-07
SOLVED:

Found it after hours of searching...

the problem was with a ppa key

Someone else with the same problem said:

just got it fixed, comment out deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main in /etc/apt/souces.list, run apt-get update

---

