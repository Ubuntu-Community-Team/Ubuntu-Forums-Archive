---
title: "need support for webcam!"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by abhishekdagr8 on 2010-02-26
i've got logitech webcam.
i need drivers for it!

---

### Post by robert shearer on 2010-02-26
Plug your webcam in. 
then..

Applications=>Accessories=>Terminal

When that opens type.. 

```
lsusb
```
and hit enter.

Copy and paste, into a post, here the output that this gives.

---

### Post by gradinaruvasile on 2010-02-26
Are you sure you need drivers for it?

Do the following:

Press alt+f2, type:

gstreamer-properties

press enter. Go to the video tab, check under the default input device if you have an item called pc camera or something not default. If there is, select it and press test. If it works, no drivers needed.

BTW if you plan using Skype you might need a workaround:

[http://ubuntuforums.org/showthread.php?t=966882](http://ubuntuforums.org/showthread.php?t=966882)

post #5.

---

### Post by JK3mp on 2010-02-26
It may just automatically detect it. Plug it in, boot up, then enter a program such as cheese or MSN and try using it. Detects my logitech just fine.

---

### Post by abhishekdagr8 on 2010-02-28
yea... i ve got a logitech.
But doesnt seem to detect. I got some driver from off the net on logitech site. But it's for windows. I installed it using wine, but after the installation, nothing happens!

---

### Post by Jalke on 2010-03-02
I can't seem to get mine to work either (I think it's an Exoo M068 - some cheapo webcam).  It says it's meant to work in Linux but it's not starting up automatically on my Karmic Koala system.  It's not working in Cheese or in the GStreamer test as outlined above by gradinaruvasile.  It seems to be recognised, as lsusb gives me:

Bus 007 Device 005: ID eb1a:2571 eMPIA Technology, Inc. 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

How can I get it to work?

---

### Post by lyall on 2010-03-02
check out this link 
it is a place to start from
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#WebCams]("http://ubuntuguide.org/wiki/Ubuntu:Karmic#WebCams")

good luck and have fun learning

---

### Post by Jalke on 2010-03-03
Thanks for the reply.  However, I can't seem to install EasyCam - dependency problems

sudo apt-get install easycam2-gtk
[sudo] password for jalke: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  easycam2-gtk: Depends: python2.4-glade2 but it is not installable
                Depends: python2.4-gtk2 but it is not installable
                Depends: easycam2-core but it is not going to be installed
E: Broken packages

Any other ideas?

---

### Post by ndefontenay on 2010-03-03
My logitech experience so far:
Did you turn it on and off?
 |               |
 |              No-> Turn it on and off
yes                     |
 |                      |
Is it definitively plugged in?
 |      |
 |      No-> Plug it in
 |                   | 
 Yes         Does it work?
 |              |    
Does it work? ->No----------> Wait 6 month until next release.
 |                                       |
Yes                                      |
 |                             Loop until working.
Fine. Install cheese then.

---

### Post by Jalke on 2010-03-03
I'll start a new thread for my question as my webcam isn't a logitech one...

[http://ubuntuforums.org/showthread.php?t=1422734&highlight=exoo]("http://ubuntuforums.org/showthread.php?t=1422734&highlight=exoo")

---

### Post by underquark on 2010-03-03
> **abhishekdagr8 said:**
> i've got logitech webcam.
i need drivers for it!Firstly, it would be a great help if you told us the exact model type/number in your original post.  Logitech make hundreds of webcams.  Even some that sound the same are actually different - e.g. Quickcam, Quickcam 3000 and Quickcam 3000 for business.

What you need to do will also depend upon what you want to do with your webcam i.e. do you want to use it as a surveillance tool, to use Skype, to take still photos's (for identity cards, for instance) or for some other purpose?

Have a look at existing help sites and wiki's such as [here](https://help.ubuntu.com/community/Webcam).

If all else fails - and you absolutely *must* use that particular webcam - then you can probably run it in a virtual machine using Win XP in VirtualBox.

I use a no-name webcam in ubuntu but also connect to people who run Windows and use Logitech Vid software and I do this by running it in a virtual machine.

---

