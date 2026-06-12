---
title: "Does not install"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by icemanMN on 2008-12-04
When I try to preview or install ubuntu from disk I get this:

Loading, please wait...
Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686

The programs included with the Ubuntu system....etc

Ubuntu comes with  ABSOLUTELY....etc

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details

ubuntu@ubuntu:~$



I would really like to try out ubuntu. But this is extremely frustrating. I will continue to search around for some guidance but so far I haven't found anything. HELP

---

### Post by Michael.Godawski on 2008-12-04
Are you sure you booted from the Desktop CD? Not the server CD? 

What exactly did you do till this messages is displayed?

---

### Post by jbrown96 on 2008-12-04
Did you download the desktop version? It appears to be a server of minimal disk, but I don't think they have liveCDs. If it is a desktop edition, could you tell us some more about your hardware?

To get to the desktop use the following
```
startx
```
If that doesn't work, try posting your errors, if you can identify them.

---

### Post by jenkinbr on 2008-12-04
Do you get a graphical menu at the very beginning before this happens?  I had this happen on a friend's x86-64 machine, and we tried various things, but it eventually just started working for some reason.

---

### Post by icemanMN on 2008-12-04
I downloaded from here: [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download) selecting 8.10 desktop edition. (ubuntu-8.10-desktop-i386)
Burned the iso and booting with cd.

The graphical menu comes up and I can either preview the operating system or install. Either option leads to what I posted. 

When I select either option the ubuntu loading bar comes up. The little box will go back and forth. Then it will fill up completely.

---

### Post by Michael.Godawski on 2008-12-04
I assume you have burnt the iso correctly... so it is weird.

Have you tried the alternate installer? Perhaps the text-based version will work for you...

---

### Post by mapes12 on 2008-12-04
> Have you tried the alternate installer? Perhaps the text-based version will work for you...I agree. You can get this from here: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by icemanMN on 2008-12-04
Alright Ill try that later and get back to you guys

---

### Post by icemanMN on 2008-12-13
Sorry for the late reply. Just got to it tonight. Well it installed alright. 
But now when I start up i cant get anywhere.
Ok so I power on. 
I choose Ubuntu 8.10 Kernel 2.6.27-7-generic
I get a ubuntu loader then it goes to a dos screen and askes for my username and password.
I enter this and it keeps me at the dos screen wanting a command.
Like this:
Starting up ...
blah blah
blah blah
blah blah
kinit:name_to_dev_t(/dev/sda7) = dev(8,7)
kinit:trying to resume from /dev/sda7
kinit:No resume image, doing normal boot...

Ubuntu 8.10 ubuntuMain tty1

login
pass
last login
text about software and no warranty/ ubuntu documentation.
loginname@ubuntuMain:~$

What do I do at the last part?!!? So confusing...

---

### Post by richaoj on 2008-12-13
try typing 

sudo /etc/init.d/gdm restart

also, as someone above asked, what hardware are you running, specifically the video card.

i know 8.10 has some issues with older onboard intel graphics -

---

### Post by icemanMN on 2008-12-13
Oops did not see the hardware request.
My video card is an ATI Mobility Radeon HD 2600
Intel Core 2 duo 2.2
ACPI x86-based PC

It is an Asus F8sA-x2 laptop.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834220240](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220240)


Ok I type in the command and it asks for my password then it says
Stopping GNOME Display Manager... [ OK ]
Stopping GNOME Display Manager... [ OK ]
username@ubuntuMain:~$

---

### Post by richaoj on 2008-12-13
Ok, a quick google search turned up a driver issue with your hardware.   I think that reconfiguring the x-server will at least get you up and running with a desktop, and then you can work on getting drivers for 3D effects and such after.  

first:

```
sudo dpkg-reconfigure xserver-xorg
```

hit enter through all of the keyboard and mouse stuff, but when the screen about the video driver pops up, choose the vesa driver, then just continue hitting enter through the rest of the screens.  

then try 

[HTML]sudo /etc/init.d/gdm restart[/HTML]

when all you get through the config.  After you get to a desktop, we can work on getting you the proper driver, but it seems there are issues with the most current one.  To read up on it:

[https://bugs.launchpad.net/ubuntu/intrepid/+source/xserver-xorg-video-ati/+bug/274234](https://bugs.launchpad.net/ubuntu/intrepid/+source/xserver-xorg-video-ati/+bug/274234)

Best of luck!  (Xserver issues suck - we feel your pain)

---

### Post by richaoj on 2008-12-13
The other option would be to install 8.04, which has a working driver, and wait for them to sort all of this out with the newer driver.

---

### Post by icemanMN on 2008-12-13
ok i ran the first command and I went through a bunch of keyboard options. It ended on a blank ok box saying:

Configuring xserver-xorg
Keyboard options:
-----
<ok>

then at the bottom of the screen a black box appears saying:
xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc....

then it gives me a command prompt again. There was never an option to modify the mouse or video driver

Should I download 8.04? If I do how would I find out when this issue is resolved?

---

### Post by richaoj on 2008-12-13
did you see the section about video driver?  I personally would probably revert back to 8.04 and wait for the issues to be sorted out.  

Get yourself a launchpad account 
(launchpad is the bug-reporting system for ubuntu--the site i had a link to) and subscribe to the above bug.  It sounds from the posts that a fix is within sight not too long off.  If you subcribe watch for the bug status to go from fix-committed to fix released.

Don't let this taint your linux experience--it was the fault of ATI.  

=)

---

