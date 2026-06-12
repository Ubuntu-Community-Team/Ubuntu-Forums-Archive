---
title: "How do I install the RadeonHD driver?"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by gdbutcher on 2009-11-17
I'm trying to install the radeonHD driver in Ubuntu 9.10 i386, I've read that its worth trying with my Ati Mobility x1250 chipset.

the guides i've read appear to be out of date, the ones i've read state you need to need to download, compile and install the driver then edit /etc/X11/xorg.conf.... except this file doesn't exist!?

I also found and installed xserver-xorg-video-radeonhd from the repos believing that this would replace the driver... but nothing.

What am I doing wrong? Can you tell me the correct way to install this driver? any help would really be appreciated!

---

### Post by Yarui on 2009-11-17
The easiest way I have found to install ATI drivers is with the program envyng.  Just apt-get install envyng-qt and then you can find the application under Applications > System Tools.

---

### Post by gdbutcher on 2009-11-17
Thanks for your help, it was worth a try but envy said the drivers weren't compatible. ATI/AMD stopped supporting the GPU so there aren't any propriety drivers for it. Thats why I wanted to try the RadeonHD driver

---

### Post by Yarui on 2009-11-17
That's a shame.  That is the extent of my knowledge of ATI in Ubuntu, so I can't offer any other advice.

---

### Post by 3rdalbum on 2009-11-17
Xorg these days has been trying to get to the stage where it doesn't need an Xorg.conf file, so some Linux users have been finding that they don't even have one, and although I have one it is truly miniscule.

Apparently, you can create one by running this command when there is no X running:

sudo Xorg -configure

How do you get to the stage where X is not running? Easy - switch to a virtual terminal by pressing Control-Alt-F2, log in, and type this command:

```
sudo killall gdm
```

Type your sudo Xorg -configure command. When it's done, restart X by typing this:

```
sudo gdm
```

Note that you'll need to install xorg-dev, build-essential and the linux-headers-generic package in order to compile the driver. But once you have an xorg.conf file, you can just change the "driver" bit to "radeonhd" and use the RadeonHD driver that you got from the repositories.

---

### Post by 5mattyb5 on 2009-11-17
Hold on guys it's a good idea to leave that file alone as it decides weather you have a gui or not.  I assume you have the gnome desktop so go to >System >Administration >Hardware Drivers it will launch a program called "jockey-gtk which will automatically scan for a compatible driver if it doesn't find one then there probably isn't one.  but you can check ati's web site for the catalyst driver, and install it after that then the Hardware Drivers application will have it in there and it's just a matter of enabling it.  Remember try jockey first!

Cheers!

---

### Post by Mark Phelps on 2009-11-18
OK, several issues ...

First, you're right in not listening to the folks that keep telling you to either use envy or go to hardware drivers.  Neither is going to solve your problem.

Second, look through the details in the link below:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

You will see a reference to changing your Xorg.conf to include Radeon as the driver.  Perhaps that will help.

There's also a link at the bottom of the page to other pages where you can get some settings info.

---

