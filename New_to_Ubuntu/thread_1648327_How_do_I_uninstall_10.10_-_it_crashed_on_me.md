---
title: "How do I uninstall 10.10 - it crashed on me"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by julioarrecis on 2010-12-18
I have been having some trouble with the update manager on version 10.04 for a while.  I started having problems with some updates returning an error message that some applications could not install.  Being a beginner, I was not paying much attention to the errors.  However the system appeared to be working so I have kept on using it.    Yesterday, when I saw upgrade to 10.10, I thought perhaps that would fix the problem.  During the install, I have several more error messages during the install.  I completed the install (or so I thought) I needed to reboot (it did not do it automatically).  When I rebooted, all I got was the tty screen; no autologin, no graphical user interface, just a unix prompt.  Next to the famous blue screen in windows, this looks pretty bad. 

Is there a way to motor around at the tty prompt and have the system reboot to the previous version of Ubuntu?  I'm pretty sure it was 10.04, and even though it was buggy, it was working just fine. Thanks.

---

### Post by earthpigg on 2010-12-18
hi,

it sounds like the easiest solution would be to back up your /home, reinstall ubuntu, and restore that /home.

do you have an ubuntu livecd and external hard drive handy?

[this]("http://www.psychocats.net/ubuntu/backup") will explain how to back up your home folder from the terminal.

after that is done, reinstall ubuntu.

after ubuntu is reinstalled, you can drag/drop the stuff from your backed up /home into your new /home folder. make sure you have the 'show hidden files and folders' thing checked. 

once that is done, you will have to change the permissions of the stuff in your /home folder to make your username the owner. run nautilus as root by typing 'gksu nautilus' in a terminal, navigate to the home folder, right click -> properties -> permissions.



if you don't want to do all of that to keep your application settings, you can just boot from a livecd, copy your data onto a thumb drive or whatever, and reinstall ubuntu.

---

### Post by julioarrecis on 2010-12-18
Thanks for the information.  However something odd happened. 

I found a thread on Ubuntu 10.10 with a person having a similar problem to mine - an upgrade leading to a tty screen.  They suggested the following:

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg

followed by a shutdown and restart.  

My old gui came back but when I checked on the version of ubuntu it said that I had loaded 11.04 Natty Narwhal which is suppose to be released next year.  Weird.  Is there any point in keeping this version?  

I do not have a external CD but now that I have my gui back, I'll back up my /home and try to do a fresh install of ubuntu.

---

### Post by fatal_ERROR777 on 2010-12-18
You have successfully installed an alpha version of the next ubuntu! Nothing more to say... The best solution (I don't know any better) is to back-up your /home/ folder, fresh install ubuntu and restore it(I mean /home/ folder :) ) after installation.

Fatal_Error

---

### Post by joneez on 2010-12-19
I was looking up why my "About Ububtu" says I have the Natty version. It seems to be a bug that's being worked on. This link describes it a bit and shows how to check your *real* version. You may actually still be running 10.10.

[http://ubuntuforums.org/showthread.php?t=1648262&highlight=natty]("http://ubuntuforums.org/showthread.php?t=1648262&highlight=natty")

---

