---
title: "I'm getting started with Linux"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by ShinIori319 on 2009-12-03
Hello everyone!
Today I decided to download Ubuntu v9.10 and installed it into Virtual PC. Since the only thing I've ever used is Windows, I have no idea of what to do.

I've managed to install a few packages with Synaptic/Sudo, but I need some help in installing tar.gz files, as well as the Virtual Machine Additions (if someone has managed to).

Thank you :D

---

### Post by clive littlewood on 2009-12-03
Hi

In virtualbox start the guest system (Ubuntu) then use the machine menues and you will see install guest addittions.

Click on this and all will be done for you.

Tar.bz files are compressed files and can be extracted using the right click option. Usually a readme file will have instructions for installing.

You should not need these as most apps can be installed using the package manager or .deb files.

Hope this helps

Clive

---

### Post by ShinIori319 on 2009-12-03
> **clive littlewood said:**
> Hi
 
In virtualbox start the guest system (Ubuntu) then use the machine menues and you will see install guest addittions.
 
Click on this and all will be done for you.
 
Tar.bz files are compressed files and can be extracted using the right click option. Usually a readme file will have instructions for installing.
 
You should not need these as most apps can be installed using the package manager or .deb files.
 
Hope this helps
 
Clive
 
 
Thanks, but what I'm using is Microsoft Virtual PC. I've downloaded the Virtual Machine Additions for Linux from the page [http://www.microsoft.com/downloads/details.aspx?familyid=bf12642f-77dc-4d45-ae4e-e1b05e0a2674&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=bf12642f-77dc-4d45-ae4e-e1b05e0a2674&displaylang=en)
 
The ISO image from that package contains a sh script that I could not execute and RPM packages that the system requests me to use Alien to convert, and Alien fails to convert as well... :-k

---

### Post by szymon_g on 2009-12-03
with all due respect- i do not think that you will gain anything by installing this extention- it is designed to host specified distros (SLES and RHEL) on specified host.

and secondary: welcome to the forum!

---

### Post by yeats on 2009-12-03
> Thanks, but what I'm using is Microsoft Virtual PC.

VirtualBox is available for Windows and will give you *much* more flexibility (I say this never having used MS Virtual PC, myself):

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by MelDJ on 2009-12-03
to install .tar.gz files see: [How to install ANYTHING in Ubuntu!]("http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually")

---

### Post by 3rdalbum on 2009-12-03
.tar.gz files are the Linux equivilant of Zip files. They can contain very nearly anything.

If it's a theme, drag it onto the Gnome Appearance program window (and you might need to click the Customise button to apply it if it's not a full theme).

If it's a compiled program, then extract it and check the contents for something you can run. If it's an installer, you may need to make it executable for root:

```
sudo chmod a+x <drag the file into the terminal>
```

Then run it as root:

```
sudo <drag the file into the terminal>
```

If it's just a program that you run "in-place", do the same thing as above but WITHOUT sudo.

If the archive contains source code, then you need to extract it, change the terminal into the new directory that is created, and run:

```
./configure
make
sudo make install
```

And install any development headers that it asks for. If this doesn't make any sense to you, then don't try compiling from source; these days it's rare that you'd need to anyway, there are often Deb packages or PPAs (repositories) available for you to use.

---

### Post by cartisdm on 2009-12-03
> **ShinIori319 said:**
> Hello everyone!
Today I decided to download Ubuntu v9.10 and installed it into Virtual PC. Since the only thing I've ever used is Windows, I have no idea of what to do.

I've managed to install a few packages with Synaptic/Sudo, but I need some help in installing tar.gz files, as well as the Virtual Machine Additions (if someone has managed to).

Thank you :D

Welcome!

I have never used virtual machines for a long period of time but now that you have seen what Ubuntu is all about might I suggest dual booting? What are you hoping to get out of your Ubuntu/Linux experience (random fun, learning the terminal, etc)?

Honestly, what helped me learn Ubuntu the fastest was to completely wipe my Windows install.  That way I was "forced" to learn Ubuntu and couldn't cheat and go to Windows when I got stuck (I eventually dual booted because I have school work that must be done in Windows)

---

