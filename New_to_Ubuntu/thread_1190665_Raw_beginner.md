---
title: "Raw beginner"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by mcnaugg on 2009-06-18
Hi there
 

 I am a complete and I mean complete beginner to Ubuntu or any Linux system.  I am, I think, reasonably comfortable with Windows systems but would like to try Linux for a change.  I have received a copy of Ubuntu 9.04 and have installed it on a spare PC running inside windows.  So far it seems to be working OK.  However I am having trouble in installing additional programs that I  have downloaded.   
 

 I should say that if I put the original Ubuntu disk into the DVD player it is recognised immediately as is another Linux disk that I obtained a few years ago.  By that I mean that they appear on the Desktop as icons.  I have also downloaded the free Ubuntu Pocket Guide and am going slowly through it.
 

 I have downloaded two programs, Gnome-Commander and Thunderbird.  The latter I am already using on my windows system.  The Gnome-Commander has a double exn - .tar.bz2 and Thunder bird also has a double extn- .tar.gz
 

 As yet I don't have any software to allow me to use my wireless modem with Ubuntu so I am having to down load via my windows PC and then copy to a DVD.  The Ubuntu PC DVD does not recognise either of the two programs, in fact the the DVD just carries on running.  I have noticed in many of the “help” files that programs can/should be loaded via the command line.  Is this where I am going wrong?


Gareth

---

### Post by lisati on 2009-06-18
It would be a good idea to get your internet connection working first. You can then use the "add/remove software" option to install many programs like thunderbird.

---

### Post by clive littlewood on 2009-06-18
Hi

As lisati says get your internet connection working first.

You should never (almost) ever have to download programs from the internet.

The 2 options in Ubuntu are synaptic package manager and add/remove where you can search for, install and uninstall all the programs available for the OS.

Both systems require an internet access to download add files and dependancies for the programs.

If you cannot get your internet up and running just post here with as much detail as posible and people will try and help.

Good luck

Clive

---

### Post by mcnaugg on 2009-06-18
I am currently waiting for feedback from my service provider regarding their "windows front end" for the wireless module.  They have told me that it won't work with Linux but didn't say if there is an alternative.

---

### Post by joshedmonds on 2009-06-18
The process for installing files from tar files is not something you want to be doing when trying out Ubuntu. It is relatively simple, but relies on use of the command line and can cause issues as the versions of the software you are installing are not tested by the package maintainers. If you really feel the need you will find information on these forums by searching for 'make' and 'install'.

If you can connect to the internet (can you use ethernet just for testing?), the process of installing will be very easy (both programs are in the repositories):
1. Open System>Administration>Synaptic
2. Reload (update package information)
3. Search for thunderbird/gnome-commander
4. Mark for installation (double click)
5. Apply.

EDIT: Definitely post details about your wireless problems. While your service provider will likely not be interested in helping with Linux, your router should have a simple interface you can access using an IP address (check the labels on your router for something like 192.168.1.1 and the default username and password)

---

### Post by nothingspecial on 2009-06-18
Hi Gareth,

Do you know which wireless card you have?

If you go to your menu and navigate Accessories > Terminal and type

```
sudo lshw -C network
```

It will tell you.

If you post that information here I`m sure someone can help you get your wireless working. You will probably want a wired connection to do it.

Welcome to Ubuntu.

---

### Post by 3rdalbum on 2009-06-18
Which wireless modem is it? Many mobile broadband modems work in Linux with a little tinkering. Some work out-of-the-box.

---

### Post by oldos2er on 2009-06-18
"I have downloaded two programs, Gnome-Commander and Thunderbird. The latter I am already using on my windows system. The Gnome-Commander has a double exn - .tar.bz2 and Thunder bird also has a double extn- .tar.gz"

   To install these two programs, open a terminal (Applications, Accessories, Terminal), and run
```
sudo apt-get update && sudo apt-get install gnome-commander thunderbird
```
 Here's more info on how to install programs in Ubuntu:

 [https://help.ubuntu.com/9.04/add-applications/C/index.html](https://help.ubuntu.com/9.04/add-applications/C/index.html)

 [https://help.ubuntu.com/community/Applications](https://help.ubuntu.com/community/Applications)

---

### Post by mcnaugg on 2009-06-18
The Wireless modem is a Kyocera UTD known, I think, as a Desk Top Modem.  It is part of the package for my IBurst Wireless Broadband setup.  Details are shown at [www.iburst.co.za](www.iburst.co.za).  A fixed landline dial up package is not an option in my part of the world, too expensive and unreliable as is the ASDL packages so wireless has been a godsend.
So far I have not had feedback from my service provider regarding Linux.  

Gareth

---

### Post by Cheesemill on 2009-06-18
> The Wireless modem is a Kyocera UTD known, I think, as a Desk Top Modem.This isn't enough info for us to be able to help, you need to follow the instructions that nothingspecial posted above and reply back with the text that gets output from 'sudo lshw -C network'.

---

### Post by nothingspecial on 2009-06-18
I think I misunderstood your first post. I take it this is one of those usb wireless thingys that mobile phone companies use?

I really don`t know much about them, except that there are fixes.

Plug it in and post the output of ```
lsusb
```

The exact model would be really useful

---

### Post by mcnaugg on 2009-06-18
I have tried the code as suggested but all I get is Command not found.  I think the main problem is that the modem (USB) has never been installed in Ubuntu.  Even when I plug it in there is no reaction as there is in windows.  The modem came with a piece of software which IBurst calls the Dashboard which actually installs the modem when first loaded and then gives a nice graphic showing how much "data" has been used for the current period.  Their helpdesk told me that this Dashboard software does not work with Ubuntu so I mailed back asking if the modem can be figured manually to work with Ubuntu.  So far I'm still waiting.

Gareth

---

### Post by philinux on 2009-06-18
You need to run the codes in ubuntu from the terminal.

Applications>Accessories>terminal.

---

### Post by Mortus Pryde on 2009-06-18
From my understanding, if given and typed correctly the command should still give you some information.

Now I am not yet a Linux wiz but I would ask the obvious, have you had this particular wireless modem connected to this computer before under windows and did it work? If not it may be a hardware compatablity issue between the computer and modem and not between the moden and OS.

If you have used that particular modem on that computer in windows, then ensure you typed the lsusb command correctly. Else wise physically inspect the modem it's self for a lable that gives the exact make and model of the modem. Almost all periferal deviced will have this unless it's a "Store Branded" device.

---

### Post by nothingspecial on 2009-06-18
> **mcnaugg said:**
> .  I think the main problem is that the modem (USB) has never been installed in Ubuntu.  


Forget the help desk. If they know nothing of linux, they cannot help. Your best bet is here. But you need to post the exact make and model of your wireless modem and the output of lsusb when it is plugged in.

---

### Post by mcnaugg on 2009-06-21
Hi guys

Sorry for not getting back sooner but I have been in contact with a LoCo group here in SA as I have an idea that somebody here will be familiar with my type of Iburst UTD modem.  It has turned out that way but it also appears to me that there may be some files missing when I installed Ubuntu.  I have decided to clean the PC and reformat the HD and install as the only OS and not within windows as it is at the moment.  So some time over the next few days I will do and then take it from there.

Many thanks for the feedback and patience.

Gareth

---

### Post by The-Don on 2009-06-21
> **mcnaugg said:**
> The the DVD just carries on running.
Right-click the DVD icon on the desktop and press 'Unmount' and/or 'Eject' :)

---

### Post by Johan Botha on 2009-07-20
I'm having the same problem - my iburst usb modem worked on windows but there's no reaction when I plug it in now, on Ubuntu.  I downloaded a "tarball" that can apparently be used to create the necessary drivers, but no luck so far.  Anyway, I'll keep trying and record what I do and where I get stuck and perhaps the seasoned Ubuntu'ers can guide me a bit.

---

### Post by roach33 on 2009-11-02
[http://blog.hostinghabitat.com/2009/02/iburst-usb-modem-installation-tutorial.html](http://blog.hostinghabitat.com/2009/02/iburst-usb-modem-installation-tutorial.html)

see if that gets you anywhere

---

### Post by heyho on 2009-11-02
> **nothingspecial said:**
> Forget the help desk. If they know nothing of linux, they cannot help. Your best bet is here. But you need to post the exact make and model of your wireless modem and the output of lsusb when it is plugged in.

You need to take notice of the above advice, I doubt that you need to reinstall.

Open up a terminal, Applications > Accessories > Terminal, then type lsusb, and post the output.

---

### Post by m4tic on 2010-01-02
wow, its that hard to click applications lol. a friend of mine uses that modem. all he had to do is point to the point to system and under networks. using the guide he set it up as mobile broadband. it worked. i notice people loose interest quickly when they decide to try another os. maybe there should be a sticky thread telling users to atleast try and spend time on their threads as theyl find a solution quickly

---

