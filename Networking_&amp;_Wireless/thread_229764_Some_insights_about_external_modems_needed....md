---
title: "Some insights about external modems needed..."
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by CytoTech on 2006-08-04
Hi, I'm still taking impt notes from this post:[Click here.]("http://ubuntuforums.org/showthread.php?t=192222&page=5") I'm using Ubuntu 6.06 LTS the one that was shipped and just came in yesterday. My external serial modem works fine with GnomePPP, but I want to use the KDE desktop from Kubuntu. problem with Kubuntu, I can't get the modem to be detected (I will give the previously posted suggestions a try). I'm thinking of some questions in mind:

1) Is it possible to combine both Gnome versions of Ubuntu and Kubuntu and get two display managers? (install Ubuntu on one partition, then install Kubuntu on the same partition)

2) Was there something that happened with KDE 3.5 distros? I was using different distros before and those came with KDE 3.4.something and KPPP was working well with those distros. And then came Fedora core 5 that had KDE 3.5.something and SLAX 5.1.6 also has KDE 3.5.something. I was dismayed that i couldn't use my ext modem with those good distros. And now, i got Kubuntu from my office, and lo and behold when i tried it here at home, KPPP can't detect my modem. tried the SLAX 5.1.7b with KDE 3.5.something use KPPP, no modem's detected on all ports available in the list. Are they (KDE developers) also leaving out modems and favoring DSL users? I mean, I trashed my WinModem to buy an external one and i also want to be updated with the lastest Linux distro. oh well, sooner or later, i must go with the flow...

---

### Post by CytoTech on 2006-08-05
Me and my quick hands,hehe, I just tried to put in the Kubuntu CD, and poof, it asked me if I want to install additional packages, which i did; installed KDE and stuff.. and i'm good to go, question 1 answered.
 
Quick problem with question #2 though, I cant seem to edit the configuration files (/etc/network/interfaces or /etc/ppp/options or /etc/ppp/peers/kppp-options) even when i use sudo, i tried kate, it tells me that the files are in read-only mode. how do i edit the files in a root-less Ubuntu???.. waaaa!!

---

### Post by Matchless on 2006-08-05
In Kubuntu, navigate in konquerer to the file, right click, Actions, Edit as root and be happy!

---

