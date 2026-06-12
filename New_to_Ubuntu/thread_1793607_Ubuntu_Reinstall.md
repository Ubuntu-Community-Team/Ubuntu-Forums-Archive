---
title: "Ubuntu Reinstall"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by jb61264 on 2011-06-29
Hi everyone...completely new to Linux in general...I have installed the Ubuntu desktop and played around and now I have installed the Ubuntu server 11.04 but during the installation I am unsure that I added all the features that I wanted and know that I did not select networking at the time because I installed to a virtual server on a Dell PowerEdge server I have (yes I am a Windows 2003/2008 admin wanting to test the Linux waters).
 
Got ubuntu installed to my virtual server fine and have been messing around learning commands from the command line after I boot it up, but I am trying to figure out 
 
1 - is there a GUI interface I can install? if so, was it something i missed during the original install?
 
2 - can I just force another install to "start over"?
 
Thanks for any assistance
 
Jeff

---

### Post by jtarin on 2011-06-29
> 1 - is there a GUI interface I can install? if so, was it something i missed during the original install?
GUI interface......do you mean a desktop?


> 2 - can I just force another install to "start over"?
Sure just format your disk or partition and reinstall.

---

### Post by Ozymandias_117 on 2011-06-29
> **jb61264 said:**
> Hi everyone...completely new to Linux in general...I have installed the Ubuntu desktop and played around and now I have installed the Ubuntu server 11.04 but during the installation I am unsure that I added all the features that I wanted and know that I did not select networking at the time because I installed to a virtual server on a Dell PowerEdge server I have (yes I am a Windows 2003/2008 admin wanting to test the Linux waters).
 
Got ubuntu installed to my virtual server fine and have been messing around learning commands from the command line after I boot it up, but I am trying to figure out 
 
1 - is there a GUI interface I can install? if so, was it something i missed during the original install?
 
2 - can I just force another install to "start over"?
 
Thanks for any assistance
 
Jeff

1. The server edition starts out without a GUI. If you want to get one after installation, simply install the package "ubuntu-desktop" to get the regular GUI on top of the server utils. (Alternatively, you can install the Desktop edition, and install the server utilities on top of it) - Not to say bad things, but for a stable, solid server, Ubuntu really isn't the distro to use long term, but it's fine to start learning!

2. I'm not sure what you mean here. If you just mean reinstall, do what jtarin said. ;P

---

### Post by jb61264 on 2011-06-30
> **Ozymandias_117 said:**
> 1. The server edition starts out without a GUI. If you want to get one after installation, simply install the package "ubuntu-desktop" to get the regular GUI on top of the server utils. (Alternatively, you can install the Desktop edition, and install the server utilities on top of it) - Not to say bad things, but for a stable, solid server, Ubuntu really isn't the distro to use long term, but it's fine to start learning!

2. I'm not sure what you mean here. If you just mean reinstall, do what jtarin said. ;P

Thanks for the info about installing ubuntu-desktop

What server distro do you recommend as a stable long term solution?

---

### Post by mastablasta on 2011-06-30
Ubuntu 10.04 LTS (came out last year in april and is supported for five years with server edition).
 
Debian stable - a rock solid distribution. Stable Debian Squeeze 6 came out this year. support time to be anounced.
 
Another option is to go Red Heat Enterpise Linux (for business) but to try it out you need to find a community edition. or buy it.
 
Aside form ubuntu desktop there are plenty other desktop environments available (i am just saying if you find the Ubuntu one a bit strange). You would also have the option of KDE (looks and acts like windows), XFCE (a bit lighter and looks kind of like old default Ubuntu desktop), LXDE (kind of still evolving but very light) looks like win98...

---

### Post by el_koraco on 2011-06-30
> **jb61264 said:**
> 
What server distro do you recommend as a stable long term solution?

The Ubuntu LTS (Long Term Support) versions, 10.04 is the current one, have a five year support cycle. i don't wanna start a flame war, but Ubuntu Server has been steadily increasing its market share. If you wanna go another route, there's CentOS, as a free RHEL clone, or Debian, on which Ubuntu is based. Both are regarded pretty highly. 

If you want to put a graphical interface on an Ubuntu server, do

sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop
sudo apt-get install lubuntu-desktoop

Then you get the Gnome, KDE, XFCE, or LXDE graphical interface. Check them out online, and see which one you like the best.

---

