---
title: "Beginner to Ubuntu; need help making a customized installation CD"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by Goombomb on 2010-04-25
I'm fairly new to Ubuntu, but I've had some experience with command line work before. Anyway, I need to essentially make a customized installation CD for Ubuntu, which will include several programs for data analysis, but I don't know how to do this. I've been trying off and on for the past two weeks with little success, and this is my status thusfar:
I've been using:
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
as a guide, but I can't seem to install squashfs-tools. I've downloaded squashfs4.0.tar.gz, extracted it to my desktop, and tried to install it via command line, with no success. Every time I attempt to install it, I get the message:
While in the desktop, I go to the extracted directory and type 
sudo apt-get install squashfs-tools
And get the error
E: Couldn't find package squashfs-tools

I've tried installing this many ways; installing the .tar.gz directly, and all manner of directory changes. My main problem is that I don't know precisely how to do it; I know about 5 or 6 ways to possibly do it, and none are working.
Either I need help with this one very specific problem, or I need an easier way to do this. Either way, help would be appreciated.
Also, I'm running it on a computer where I can't find the network drivers for the native wireless card, so I don't have internet access on it (and there's no easy way to hardwire it to the internet around here). Luckily, internet access is not a prerequisite for this project, but it is a minor annoyance that might be relevant.

---

### Post by bville09 on 2010-04-25
I'm pretty sure that unless you have the tools on a CD or USB, you can't install from apt-get without a net connection (or at least this was my understanding), and I don't think there is a .deb package for squashfs in apt, but I'll check.

So, did you do the "make" and "make-install" commands while in the directory of the .tar.gz?

From memory, it's something like:
cd ~/wherever_it's_downloaded/squashfs-tools.tar.gz
configure
make
make install

Then it should just install, but you need the gcc libraries.

EDIT: Well, doing "sudo apt-get install squashfs-tools" does install it right away, on my end. What version of Ubuntu are you using?

---

### Post by Goombomb on 2010-04-25
I haven't tried the commands there, I'll give them a try when I get the chance.
Also, running Karmic.

---

### Post by louieb on 2010-04-25
Installing software without an Internet connection is a pain in the butt.  If you know exactly what packages you need you can use apt-on-cd and download them on a computer with an Internet connection. 

Also there is [http://keryxproject.org/](http://keryxproject.org/)  -  still you need a computer with an Internet connection.   

Another alternative is to buy the Ubuntu repositories on DVD.  osdisk.com sells then.

---

### Post by anewguy on 2010-04-26
Why don't we also ask for the output of lspci and lsusb to see if we can be of help getting the OP's wireless working?

Dave ;

---

