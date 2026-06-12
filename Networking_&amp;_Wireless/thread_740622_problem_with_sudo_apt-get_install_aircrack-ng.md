---
title: "problem with sudo apt-get install aircrack-ng"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by ngoctuss on 2008-03-30
hi every, when i run terminal to install aircrack-ng, a error show and i don't know how i do
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package aircrack-ng
and when i ran airmon-ng  then error display again:
The program 'airmon-ng' is currently not installed.  You can install it by typing:
sudo apt-get install aircrack-ng
You will have to enable component called 'universe'
bash: airmon-ng: command not found

help me soon thanks!

---

### Post by em3raldxiii on 2008-03-31
Hi!  Here are a couple of things you can do.  First off, I think you will probably have to enable universe and/or multiverse repositories.  You can do this in your Synaptic Package Manager (system > administration > Synaptic Package manager).  Click around in the menus and you will see that you can look at existing repositories and enable others.  I am not precisely sure which repo it's in, but give it a try.

Once you have enabled the additional repositories, you can refresh synaptic and then search for your package (aircrack-ng).  Alternatively, you can try using the console and type this:  
```
sudo aptitude install aircrack-ng
```

You can also add additional repositories using a text editor and editing the /etc/apt/sources.list file.  If you are unsure, don't edit the file ... but it's quite simple.  Then you will have to run:  sudo aptitude update ... then you can try the install again.

Alternatively, it appears that you can download the package from the aircrack website here:  [www.aircrack-ng.org](www.aircrack-ng.org).  You may have to "build" it from source from that site.

Good luck!

---

### Post by ngoctuss on 2008-03-31
hi you when in try typing:

sudo aptitude install aircrack-ng
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

it response the same that, i dont know

---

### Post by Saint Angeles on 2008-03-31
you have to close synaptic while running apt-get

---

### Post by ngoctuss on 2008-03-31
how do open synaptic ?'universe'

---

### Post by em3raldxiii on 2008-03-31
Synaptic Package Manager is accessible in your SYSTEM menu at the top of your desktop:

System > Administration > Synaptic Package Manager

Within that program, you can access your repositories and select to enable your Universe repositories if they are not already enabled.

It sounds like you might need some more one-on-one help.  Have you ever tried accessing the #ubuntu IRC channel?  They can help you in realtime there.

---

