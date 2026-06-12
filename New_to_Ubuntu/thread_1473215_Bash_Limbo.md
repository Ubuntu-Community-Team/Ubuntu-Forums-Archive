---
title: "Bash Limbo"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by nnjond on 2010-05-05
Hi,

Synaptic Pkg Manager recommended i ran this command. 


nnjond@nnjond-desktop:~$ sudo dpkg --configure -a
[sudo] password for nnjond: 
Setting up libgdata1.4-cil (1.4.0.2-3) ...
* Installing 14 assemblies from libgdata1.4-cil into Mono

....nothing 's happened for 15 minutes?

---

### Post by houseworkshy on 2010-05-06
> **nnjond said:**
> Hi,

Synaptic Pkg Manager recommended i ran this command. 


nnjond@nnjond-desktop:~$ sudo dpkg --configure -a
[sudo] password for nnjond: 
Setting up libgdata1.4-cil (1.4.0.2-3) ...
* Installing 14 assemblies from libgdata1.4-cil into Mono

....nothing 's happened for 15 minutes?

If you look at the system moniter that will tell you what tasks are running.  System>Admin'.  Right clicking on any of the tasks in the list of processes gives several options including both diagnostics and the ending  or killing of tasks.
 
It may be worth choosing a differant servor in software sources.  Which are better vary day to day for me so I just select other in the "download from" drop down menu and go with the fastest.  Then refresh the lists, then repeat whatever you were doing in synaptic or :-

sudo apt-get update
sudo apt-get upgrade

in the terminal and see if the command is recomended  again, if so see if it completes this time.


Sometimes I've found that the downloading part of this can stick, that may have happened to you as you didn't get as far a size count and a y/n option.
 
The "man" command in the terminal could also be informative, "man dpkg" and "man top" for example.

---

