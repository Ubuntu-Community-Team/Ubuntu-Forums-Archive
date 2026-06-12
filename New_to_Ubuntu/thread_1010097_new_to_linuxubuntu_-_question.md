---
title: "new to linux/ubuntu - question"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by jtj on 2008-12-13
Hi all. I am extremely new to ubuntu/linux and had a couple of questions. I am a lifelong windows user and downloaded the ubuntu server 8.04 to set up a server at home for testing web sites I built with php. I followed the link/instructions here from a recent article on this at psdtuts and had a couple of hiccups during install.

the PC I am using for this is a pentium 3 with 1 gig of ram (550mhz processer). When it boots up it gives an error message of forced acpi failed due to cutoff (not verbatim but thats the basic message) and shows 2000 in parenthesis, and my bios as 1999 in parenthesis. I am assuming its saying my bios is too old for something. Is this going to be a problem? it goes past it automatically like it just warns me but will still work.


The install went fine except for detecting network settings. I didnt have the pc connected to my router and just bypassed the network setup during install. How do I get back to this so I can download apache, php etc? Should I just set it up on the network and reinstall ubuntu or can I access those menus again?

Learnignto do things without graphics is not as easy as I thought it would be. A command list would be nice, and I am sure I am overlooking it somewhere... Thanks for any help..

---

### Post by Titan8990 on 2008-12-13
Alright, to fix your ACPI issue:

When the grub menu is up (you may have to hit ESC while booting to enter the menu), highlight the Ubuntu that you boot to.

Press the "e" key to edit that line.

Move the highlighted are down one to the kernel line and hit "e" again.

Type:

acpi=off

then press enter. Then hit "b" to boot.

To fix this permanently you need to edit /boot/grub/menu.lst

Start by making a backup of the file:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.BAK

Now it is safe to edit it:

sudo nano /boot/grub/menu.lst

Add acpi=off to the kernel line in the same place you did in the grub menu.


Starting off learning Linux with a server is tough. Linux server typically are not for beginning users.

> The install went fine except for detecting network settings. I didnt have the pc connected to my router and just bypassed the network setup during install. How do I get back to this so I can download apache, php etc? Should I just set it up on the network and reinstall ubuntu or can I access those menus again?


Post the output of the following:

cat /etc/apt/sources.list

ifconfig

cat /etc/network/interfaces


Here is a list of commands and man pages for those commands:

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)


In order to see all the commands available to you, enter the following:

echo $PATH

All the directories that are listed in the path variable contain executables that you run when you enter the command. However, I do not recommend this as a way to learn the commands but thought it might be helpful to show you the PATH variable which in turn will help you to learn a bit more about the directory structure.

I'm going to give a few that I think are a "must know to do anything"

cd - change directories

ls - list directories 

man - manual pages on commands

find - search for files, see: man find

nano - command line text editor

./NAMEOFEXECUTATBALE - This is how you would execute a file that is in your current directory

sudo - must prefix all commands with sudo that require administrative priledges

ifconfig - windows equivalent is ipconfig

apt-cache search - search repositories for programs

apt-get install - install program from the repositories


I hope that is enough to get you started, good luck!

---

### Post by Paqman on 2008-12-13
ACPI: I wouldn't worry too much about this, it's power management stuff. If your machine boots alright and is stable without it then it's not a biggy.

You can install a graphical desktop onto your server if you want. Just install the package ubuntu-desktop. You can always uninstall it later.

As for lists of linux commands, if you Google for "linux commands" you'll find more of them than you could shake a stick at.

---

### Post by billgoldberg on 2008-12-13
> **jtj said:**
> Hi all. I am extremely new to ubuntu/linux and had a couple of questions. I am a lifelong windows user and downloaded the ubuntu server 8.04 to set up a server at home for testing web sites I built with php. I followed the link/instructions here from a recent article on this at psdtuts and had a couple of hiccups during install.

the PC I am using for this is a pentium 3 with 1 gig of ram (550mhz processer). When it boots up it gives an error message of forced acpi failed due to cutoff (not verbatim but thats the basic message) and shows 2000 in parenthesis, and my bios as 1999 in parenthesis. I am assuming its saying my bios is too old for something. Is this going to be a problem? it goes past it automatically like it just warns me but will still work.


The install went fine except for detecting network settings. I didnt have the pc connected to my router and just bypassed the network setup during install. How do I get back to this so I can download apache, php etc? Should I just set it up on the network and reinstall ubuntu or can I access those menus again?

Learnignto do things without graphics is not as easy as I thought it would be. A command list would be nice, and I am sure I am overlooking it somewhere... Thanks for any help..

I suggest you install the xfce4 dsktop. I think the command is "sudo apt-get install xfce4". (start the gui from the command line using "startxfce4")

It has a resource friendly gui.

Once everything is installed and running correctly, you can remove the unneeded things and gui.

---

### Post by jtj on 2008-12-13
thanks for the help.. I will play with it tonight and update on how it goes. It looks like this isnt too much different from DOS, but that was ages ago and windows came out a year after I got that first computer and I never looked back. I thought that I would never need more than the 40 MB HDD and 8 MB memory that came on that 286!!! things arent like that anymore! I figured I would be a bit over my head with this at first, but I really just want the convenience of a server to test with.. The pc I had to use had windows xp installed but it didnt have a disk with it and it acted wierd/crashed all the time, so I figured use a free OS so that I am not too invested in it at first. Plus themore I am around my friends mac's, the more I realize windows isnt such a great thing..

---

