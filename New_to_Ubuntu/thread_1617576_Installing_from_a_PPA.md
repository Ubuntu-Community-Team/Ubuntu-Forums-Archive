---
title: "Installing from a PPA"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by bobman500 on 2010-11-09
Hi people. I have been on Ubuntu for about a month now. I am getting to grips with most things, but haven't really worked with terminal yet. I am trying to install Handbrake DVD ripper, which has to be done using a PPA.

I have followed all the instructions given for registering a PPA to your system using terminal, and from what I can tell, it is all done correctly.

Here comes the 'noob' bit. At the end it tells me "now you can install the program through terminal as normal" but I have never done that! And whenever I looks for instructions, it just gives me the same details on registering the PPA!

Any help would be greatly appreciated. 

If it helps, this is where I got all the information. [https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by AngusH on 2010-11-09
Hey, to install a program from the terminal the command your after is ```
sudo apt-get install packagename
``` but that's not actually necessary. Synaptic should have the packages in them if you've enabled the PPA properly.
Angus

---

### Post by Verbeck on 2010-11-09
from a terminal:

sudo apt-get install handbrake

or in synaptic, select the origins filer then select the handbrake repository from the list to see the available software from that repository

in software center, expand the menu 'get software' and you should see the repository listed (might take some time, dunno why : try logout/in)

---

### Post by bobman500 on 2010-11-09
I tried that, and it said:

Building dependency tree       
Reading state information... Done
Package handbrake is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'handbrake' has no installation candidate

---

### Post by madmax75 on 2010-11-09
Remembee to update your software list first.

From the Terminal:

```
sudo apt-get update
```

Or in the Synaptic window, hit the Update button.

---

### Post by Verbeck on 2010-11-09
just checked, its 
```
sudo apt-get install **handbrake-gtk**
```

EDIT: Reply to the post below,
system>administration>Synaptic Package manager

---

### Post by bobman500 on 2010-11-09
I have updated and retried, I get the same message, I logged out and back in and the PPA doesn't show in the software centre dropdown, and I don't know what the synaptic is.

---

### Post by Zill on 2010-11-09
bobman500: Welcome to Ubuntu and I am sure you will get to like it as much as we do.  However, I politely suggest you learn to "walk before you run". :-)

The PPA you referred to clearly states "...These are not stable releases. ... They are only recommended for experienced users and developers."  I therefore suggest you learn the basics of installing *before* installing PPAs to your system which *could* cause you more trouble than they are worth. ;-)

The "sticky" at the start of this forum section entitled "[New to Ubuntu? Start here...]("http://ubuntuforums.org/showthread.php?t=801404")" has several useful guides which help to explain different aspects of your new OS, including software installation.

---

### Post by bobman500 on 2010-11-09
Then, could somebody please recommend a DVD ripper that works? I just wanna put some movies from DVDs onto an external hard drive, and every piece of software I have used goes into error or tells me I cancelled the rip as soon as I start it.

---

### Post by Verbeck on 2010-11-09
> **bobman500 said:**
> Then, could somebody please recommend a DVD ripper that works? I just wanna put some movies from DVDs onto an external hard drive, and every piece of software I have used goes into error or tells me I cancelled the rip as soon as I start it.

have you got the restricted extras installed?
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

also, I've posted the correct installation name in the previous post ([#6]("http://ubuntuforums.org/showpost.php?p=10094926&postcount=6"))

---

### Post by bobman500 on 2010-11-09
I don't have the restricted extras, that must be the problem. I am downloading them now. WIll post again if it is still an issue, but I doubt it will be. Thanks! :KS

---

### Post by Nightstrike2009 on 2010-11-09
New ppa repositories usually involves a terminal command cut and paste from a website (try googling what you want), not trying to be sarcastic that is how you usually do it, hope that helps. :-)

If you mean installing thats:
sudo apt-get install (Package name)

don't include (package name) replace with program name that you want eg for docky:
sudo apt-get install docky

---

### Post by TSJason on 2010-11-09
This should be fairly simple if you're looking to learn how to add repos and perform installs from the command line.

```
sudo add-apt-repository ppa:handbrake-ubuntu/ppa
sudo apt-get update
sudo apt-get install handbrake-gtk handbrake-common
ghb
```

---

### Post by JohnAStebbins on 2010-11-09
> **TSJason said:**
> This should be fairly simple if you're looking to learn how to add repos and perform installs from the command line.

```
sudo add-apt-repository ppa:handbrake-ubuntu/ppa
sudo apt-get update
sudo apt-get install handbrake-gtk handbrake-common
ghb
```

Does the version of HandBrake from that PPA even work on lucid and maverick?  If it does then the maintainer has had to patch it.  New distributions have an updated version of libgtk that is not backwards compatible with the version that HandBrake 0.9.4 was designed for.  

For this reason, I recommend people use the nightly build till the next official release comes out (which will be soonish).  The developers are preparing for a release which means things are stabilizing.
```

sudo add-apt-repository ppa:stebbins/handbrake-snapshots
sudo apt-get update
sudo apt-get install handbrake-gtk handbrake-cli
ghb

```

---

