---
title: "CentOS vs. Fedora"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by WitchCraft on 2010-01-23
Hi, question:

I currently have one laptop with a version of arch linux installed which has 2 faulty dhcp clients, and I can't work with it, so I have to reinstall another version of Linux.

I wanted to try a version of red hat linux, so my question now:

Which one is better, fedora or CentOS ?

I mean better in terms of stability and mainly in the number of available packages. Also, do both have the same package manager, or is one notably better?


Anybody has any experience with those?

---

### Post by chuina on 2010-01-23
Hi, there,

I prefer CentOS , specially 5.4 , the latest one.
It is more stable in Server tasks than fedora.

You can use fedora's softs in CentOS. 
In fact, many of the fedora 6's packages used in CentOS 5.4 (even  in the RHEL5)

So, packages will not bother you.
But you need more query for using it in laptop.

Thanks.

---

### Post by Abhijit Navale on 2010-01-23
I am a newbie. 
Now I am using Ubuntu.
But before going to Ubuntu I gave try for Fedora 10.

I have come to know from various sources that Fedora is one linux distro which has most hardware support. If Fedora dont support a specific hardware then no linux on earth support it.

But when I install Fedora 10 on HP-COMPAQ A965TU laptop 2gb ram 160 gb hdd intel core 2 duo then Fedora unable to detect my harddrive. After trying for 3-4 times I go to their forums. There I found info that Fedora dont have SATA harddisk drive. To install Fedora 10 one has to disable SATA from BIOS then Fedora will install.

So I was shocked by this. Fedora dont have SATA support? oh no! Fedora completely disappointed me. 

Then I decided to use Ubuntu.

---

### Post by WitchCraft on 2010-01-23
> **Abhijit Navale said:**
> 
Then I decided to use Ubuntu.

I know that debian based Linuxes are better than red hat based, namely because apt-get is the better package manager.

But I already have Ubuntu on another computer and on the server, and I wanted to try out RedHat/compatible, mainly because I want to write RPM installers, and I can't really do that on a Debian/Ubuntu system (well I mean I can write and pack one, but I can't really test it, except in a VM).

---

### Post by whoop on 2010-01-23
> **WitchCraft said:**
> Hi, question:

I currently have one laptop with a version of arch linux installed which has 2 faulty dhcp clients, and I can't work with it, so I have to reinstall another version of Linux.

I wanted to try a version of red hat linux, so my question now:

Which one is better, fedora or CentOS ?

I mean better in terms of stability and mainly in the number of available packages. Also, do both have the same package manager, or is one notably better?


Anybody has any experience with those?

I think a big difference between the two is:
fedora: bleeding edge (the latest)
CentOs: stability (old(er) software)

So when choosing between the two these factors should be considered (among others)...

---

### Post by chuina on 2010-01-23
> Also, do both have the same package manager

For both of them package manager is "yum".
U can create your own package repo very easily with both of them.
Truly, easy than apt-get.

If your laptop has enough [COLOR="DarkRed"]hardware power[/COLOR] then try with fedora and CentOS's live CD. 

NOTE: fedora and CentOS's Live CD are uninstallable,i.e. need network installation.

---

### Post by WitchCraft on 2010-01-23
> **chuina said:**
> For both of them package manager is "yum".
U can create your own package repo very easily with both of them.
Truly, easy than apt-get.

If your laptop has enough [COLOR="DarkRed"]hardware power[/COLOR] then try with fedora and CentOS's live CD. 

NOTE: fedora and CentOS's Live CD are uninstallable,i.e. need network installation.

Actually, I'm probably more interested in the latest packages than in the actual number, as long as all the major programs and automation scripts are in there (g++, gcc, Python, mono, xsp/lighthttp/apache/nginx, postgre sql,wxWidgets) [and a working dhcp of course ;-)].

That's actually why I tried arch linux, and it's wounderful, except it has a crappy package manager, apart from the not-working dhcps.

No, I'll try a live installation ;-))
I think 1 GB RAM and 250 GB IDE (i know why i don't buy sata) hard drive should be enough.
Are you saying yum is better than apt?

I just hope the driver for the IPW 2200 bg wlan card works ...

---

### Post by chuina on 2010-01-23
Right now i can tell about CentOS,

>  as long as all the major programs and automation scripts are in there (g++, gcc, Python, mono, xsp/lighthttp/apache/nginx, postgre sql,wxWidgets) 

You can check these softs [[COLOR="SeaGreen"]here[/COLOR]]("http://mirrors.igsobe.com/centos/5.4/os/i386/CentOS/") 
and also [this]("http://rpm.pbone.net/") is a good site for various distros rpm's , just reminding u redhat,centos,fedora ... are rpm based soft management.

> No, I'll try a live installation
I just tried to say, u can't install from live CD like we do in Ubuntu. LiveCD need network connection through internet.

> Are you saying yum is better than apt?
Obviously.

> I just hope the driver for the IPW 2200 bg wlan card works ...
I just hope too..!

---

### Post by chuina on 2010-01-23
Just find something about your wlan [[COLOR="DarkRed"]here[/COLOR]]("http://wiki.centos.org/HowTos/Laptops/Wireless#head-7120b8469149d0d562a134fd201f3af4bbf45048").:D

Not sure how will it work.:confused:

---

### Post by MisfitI38 on 2010-01-23
> **WitchCraft said:**
> I know that debian based Linuxes are better than red hat based, namely because apt-get is the better package manager.

Stating questionable opinions like this, or trolling, is always counterproductive, but a good way to start a flamewar. If you are truly interested in advice from people who use RPM based distros, it may be wise not to insult their OS of choice.

> **WitchCraft said:**
> ...I tried arch linux,(sic) and it's wounderful, (sic) except it has a crappy package manager, apart from the not-working (sic) dhcps.
Heh, I lol'd. So, rather than actually solving your dhcp issue, you have decided to wipe and reinstall an RPM-based distro?
> I think 1 GB RAM and 250 GB IDE (i know why i don't buy sata) hard drive should be enough.
FWIW, 192MB RAM is enough to install CentOS, just not with the graphical Anaconda installer.

---

### Post by WitchCraft on 2010-01-23
> **chuina said:**
> Just find something about your wlan [[COLOR="DarkRed"]here[/COLOR]]("http://wiki.centos.org/HowTos/Laptops/Wireless#head-7120b8469149d0d562a134fd201f3af4bbf45048").:D

Not sure how will it work.:confused:

Thanks for the hint, but I'm actually aware that the firmware has to be installed, and it is. The driver is actually in the kernel, and it works fine (at least with ubuntu/debian). 

The thing is just that I have little enough time for doing my work, so I'm really not interested in debugging dhcp programs, and I won't start debug pacman neither. Those things are basic, and have to work once you put them in the repository.

---

### Post by WitchCraft on 2010-01-23
> **MisfitI38 said:**
> Stating questionable opinions like this, or trolling, is always counterproductive, but a good way to start a flamewar. If you are truly interested in advice from people who use RPM based distros, it may be wise not to insult their OS of choice.


Heh, I lol'd. So, rather than actually solving your dhcp issue, you have decided to wipe and reinstall an RPM-based distro?
.
FWIW, 192MB RAM is enough to install CentOS, just not with the graphical Anaconda installer.

Actually 64 MB is enough to install a full server, including mysql postgresql and mono with xsp plus php.
And you can go down to 48 or even less.

---

### Post by WitchCraft on 2010-01-23
Installing Fedora, ahahahahahahaha.

Just started, and it offered the choice to review the default partition configuration. I was happy, because when you install Ubuntu, you only have the choice between automatic partitioning and manual partition, but not of reviewing and alter the automatic parition.

But, hahaha, what a joke.
I altered the filesystem from ext4 to xfs, because xfs needs less space, is faster (needs less cpu), and doesn't have the inode problem. But oh joy:
Error: You cannot install the boot partition on an xfs file system...
Error: You cannot install the data partition on an xfs file system because the filesystem you selected doesn't match the filesystem on your live install cd (ext4). 

Ahahahaha. Arch can both. With Fedora, you have the choice, but in the end, you have to take ext4 anyway. What a joke. Wondering whether the rest of the system is just as 'good'.

---

### Post by WitchCraft on 2010-01-23
Good. Acquired r**t pwr.
The network works, very well.
Better than on Ubuntu, I can see all the networks in the vicinity.

---

