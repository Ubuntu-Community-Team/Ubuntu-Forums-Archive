---
title: "Need help running setting up Ubuntu Server and Raid"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by Photobug on 2011-02-01
I have just put Wubi on my laptop to test run Ubuntu and like it a lot so far.

My plan is to build a server running Ubuntu to act as storage for all my other computers.

Since so many parts of this whole process is new I would like to get as much advice as possible so i do it right the first time.  The case is a special server case with many fans and a number of sata back planes.

I am running an Athalon X2 64 mobo in a 939 socket.  The Raid will be controlled by a High Point Rocket Raid  PCI card.

I am hoping for any advice on how to set this up.

First question is do I set up the Raid first or Ubuntu server?
The driver for the raid card is located here.
[http://www.highpoint-tech.com/BIOS_Driver/page/rr1740.htm](http://www.highpoint-tech.com/BIOS_Driver/page/rr1740.htm)
Up until yesterday they only had support for Ubuntu 8.10 but I see they just added 9.4.  Should I just install that and go with 9.4 or should I try this with Ubuntu 10.10?

Any other suggestions for setup and configuration appreciated.

Thanks

---

### Post by cariboo on 2011-02-01
I would suggest using 10.04, as it is supported until April 2015. The LTS versions only get bug fixes and security updates over the life of the version, so there won't be any big surprises after doing updates.. You setup raid during the install procedure.

The other thing to keep in mind is that the server version doesn't have a gui, everything is done from the command line. I personally very rarely need a graphical application to do anything,so on the few occasions where I do, I use a combination of ssh and X forwarding to run an application.

If you can't do anything without a gui, I would suggest you install one of the more lightweight desktop environments, like Xfce, or LXDE, they can be installed from the command line using the following commands:

```
sudo aptitude install xfce4
```

or

```
sudo aptitude install lxde
```

---

### Post by heyandy889 on 2011-02-01
Hey, man! Yes, yes. This is a beautiful thing. I will direct you to "Full Circle – Special Edition #01 – The Perfect Server" [http://fullcirclemagazine.org/2011/01/26/full-circle-special-edition-01-the-perfect-server/](http://fullcirclemagazine.org/2011/01/26/full-circle-special-edition-01-the-perfect-server/) I am working thru that, I successfully installed Ubuntu Server Edition. I can't log into it yet, but that is another story! The tutorial uses Ubuntu 9.10, which I assume was the latest and greatest flavor at the time of the publication. Anyways, take a shot at it.

One thing I would like to mention is that it might be a good idea to back up any music, old school papers, or lolcat photos you have kicking around. When you're partitioning the hard drive or installing new operating systems, there is a risk for writing over any other data you have on that hard disk.

Rock on, good luck, my man. :-D

---

