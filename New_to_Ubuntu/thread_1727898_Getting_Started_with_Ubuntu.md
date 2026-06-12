---
title: "Getting Started with Ubuntu"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by ChuckLeJam on 2011-04-13
Help!
Hello, all.
I think I just installed Ubuntu 10.04 but I can not get past entering my password.
I bought the book "Ubuntu for Non-Geeks" which came with a live CD.
After spending a few hours exploring running from the CD, I decided to install on the harddrive.
This is an old PC which I have not used for years.
It has a Pentium III processor running at 866 MHz, with 768MB ram.
It had been running Windows 2000 Pro.
Following the installation instructions on the CD, I decided to erase Windows and do a clean Ubuntu installation.
The installation seemed to go without a hitch but now when I attempt the start the system, I get as far as entering my password then it just sits with the purple screen.  No messages!
Nothing!! After a while the screen go to black. I hit enter and the dialog box asking for my password is displayed. I enter it and click "Unlock" and it starts the cycle with the purple screen again. I do the "CTRL-ALT-DELETE" and shutdown!
Help!!
I am not interested in the graphical interface.
I just want to run Apache and MySQL for personal use here at home.
Appreciate any help I can get.
Thanks.

---

### Post by josephmills on 2011-04-13
Give  xubuntu [http://www.xubuntu.org/](http://www.xubuntu.org/) a try.If that don't work try lubuntu but I think that xubuntu will work fine

---

### Post by falko on 2011-04-13
If you don't need a desktop, try to install the Ubuntu Server version instead ( [http://www.ubuntu.com/business/get-ubuntu/download](http://www.ubuntu.com/business/get-ubuntu/download) ).

If you need a LAMP system, take a look here: [http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-10.04-lamp)

---

### Post by mastablasta on 2011-04-13
you didn't say what graphics card you have (it might be the one causing the problem).
 
Server version comes with command line only.

---

### Post by dejuren on 2011-04-13
> **ChuckLeJam said:**
> 
I am not interested in the graphical interface.


Ctrl-Alt-F1

---

### Post by BertN45 on 2011-04-13
Yes CTRL-ALT-F1 to go to the command line and CTRL-ALT-F7 to go back to the purple screen. Probably you need to find another driver for your video card.

---

### Post by ChuckLeJam on 2011-04-16
Thank you all for your suggestions and for taking the time to respond.
I ended up just loading it on a different (faster processor & more memory) PC
and I I am getting my Linux education.
I am sure I will be back here asking for more advise as I progress
and hopefully being able to offer some advise in the future.

ChuckLeJam...

---

### Post by kaldor on 2011-04-16
> **ChuckLeJam said:**
> Help!
Hello, all.
I think I just installed Ubuntu 10.04 but I can not get past entering my password.
I bought the book "Ubuntu for Non-Geeks" which came with a live CD.
After spending a few hours exploring running from the CD, I decided to install on the harddrive.
This is an old PC which I have not used for years.
It has a Pentium III processor running at 866 MHz, with 768MB ram.
It had been running Windows 2000 Pro.
Following the installation instructions on the CD, I decided to erase Windows and do a clean Ubuntu installation.
The installation seemed to go without a hitch but now when I attempt the start the system, I get as far as entering my password then it just sits with the purple screen.  No messages!
Nothing!! After a while the screen go to black. I hit enter and the dialog box asking for my password is displayed. I enter it and click "Unlock" and it starts the cycle with the purple screen again. I do the "CTRL-ALT-DELETE" and shutdown!
Help!!
I am not interested in the graphical interface.
I just want to run Apache and MySQL for personal use here at home.
Appreciate any help I can get.
Thanks.

Ubuntu for non-geeks when you basically want to start a personal server? You're ahead of a lot of people.

Just grab Ubuntu Server Edition and don't install a GUI. The installer is pretty straightforward and easy to follow, and adding software is easy. I recommend you get the 32-bit 10.04 LTS (Lucid Lynx) version and install from there; reason being that you get security updates and support until 2015.. meaning you can just install it, set it up, and forget it for a few years.

Learn a few Linux commands, and install a basic text editor. Nano is a perfect editor for a new user, since you can easily edit configuration files with it. Your PC is more than capable of running a personal server. I've had 10.04 running with 85 MB of RAM on a vanilla install.

Download for Ubuntu Server _[here]("http://www.ubuntu.com/business/get-ubuntu/download")_

---

### Post by deconstrained on 2011-04-16
Or, since you don't want the GUI and are installing it on low-end hardware, I'd recommend a slimmed-down Debian, or even FreeBSD (heck, it's really light/secure and the free documentation is top-notch). 

Regardless of which non-GUI Linux/Unix you pick you're going to have the same learning curve, and Apache/SQL/etc will require more or less the same procedure for installing and configuring.

---

