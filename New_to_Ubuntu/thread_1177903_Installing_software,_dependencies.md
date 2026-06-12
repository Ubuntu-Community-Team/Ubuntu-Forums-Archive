---
title: "Installing software, dependencies"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by LarsXI on 2009-06-03
Howdy everyone

I just did a clean install of xubuntu, and have gotten around to trying to install things. 

I'm curious, when you go to install a new piece of software, about how many dependencies do you typically end up having to resolve before reaching success?

I'm currently working on installing mplayer, and have uncovered a very large number of missing dependencies that have kind of branched off to the point where I lose track of where I am in the tree. I'm remaining optimistic about using xubuntu, however, I'm wondering how much time is generally spent hunting down dependencies. Does the process get easier after a couple times once you've built up a good base of libraries and programs? Would this be less painful on a distribution that is less streamlined? 

thanks for your time

---

### Post by nandemonai on 2009-06-03
You shouldn't be installing packages manually.

Use Add/Remove / Synaptic / apt-get or aptitude. Dependencies will be resolved and installed automatically.

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by skyjacker on 2009-06-03
Don't know if xubuntu has it, but synaptic will put all of the dependencies in with the program.

---

### Post by Cheesehead on 2009-06-03
If you are using your package manager correctly, and installing software from the Ubuntu Repositories, then you should be spending almost no time at all chasing dependencies - nearly all dependencies should be resolved automatically.

For example, if I wanted to install OpenOffice 3.0 from the Jaunty repositories, I could do it from the command line (sudo apt-get install openoffice.org-3.0), from Add/Remove (click the box), or from Synaptic (click the box). All the dependencies would be automatically installed too from -coincidentally- the same source. If I wanted to install a bleeding-edge build of OpenOffice from a PPA or third-party repository, the procedure might be a bit uglier, depending on how complete the repo is.

Perhaps if you provided an example, we could help better.

---

### Post by Sir Jasper on 2009-06-03
Hi,

When a package or program is installed, say through Synaptic Package Manager, all necessary dependencies are automatically chosen. The actual number varies considerably with each package.

Removals work similarly and it's anticipated you'll really like the update procedure.

My regards

---

### Post by LarsXI on 2009-06-04
Ah, Ok. 

I probably need to designate more/better repositories. I've been trying to install things through my synaptic, but a lot of programs are missing.

thanks

---

### Post by oldos2er on 2009-06-04
> **LarsXI said:**
> Ah, Ok. 

I probably need to designate more/better repositories. I've been trying to install things through my synaptic, but a lot of programs are missing.

thanks

 Check System, Administration, Software Sources to make sure all repositories are enabled.

 Edit: Sorry, I missed that you're running Xubuntu. If you use Synaptic, check Settings, Repositories.

---

### Post by snowpine on 2009-06-04
> **LarsXI said:**
> Ah, Ok. 

I probably need to designate more/better repositories. I've been trying to install things through my synaptic, but a lot of programs are missing.

thanks

MPlayer should not be missing from Synaptic. 'sudo apt-get install mplayer' should do the trick (or you can use Synaptic).
Can you give specific examples?

---

### Post by zvacet on 2009-06-05
If you didn't add all repos then do what oldos2er adviced.Check all except source under Ubuntu software and first two under updates tab.After that you will find mplayer in synaptic and install it from there.

---

