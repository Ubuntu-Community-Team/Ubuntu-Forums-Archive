---
title: "Need help installing the ATI catalyst drivers for the HD3200."
date: 2009-11-28
forum: New to Ubuntu
---

### Post by MichaelFTW on 2009-11-28
Hello, I'm having trouble understanding what I'm supposed to do to install the ATI catalyst display drivers.

First, after I download them, I type in (Are there code tags?) "sudo sh /home/michael/Desktop/ati-driver-installer-9-11-x86.x86_64.run"

Okay, that I understand, but after that, I've heard I need to do something with xorg.conf.

Edit it? Update it?

Thanks in advance.

Oh, something that might be important, I'm using the 64bit Ubuntu.

---

### Post by MichaelFTW on 2009-11-28
Wait, is it "sudo dpkg-reconfigure -phigh xserver-xorg"?

---

### Post by jamieleshaw on 2009-11-28
This may be helpful[ _http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually_]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually")
This maybe helpful, it applies to Karmic too.
[]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_Driver_Manually")

---

### Post by admiralspark on 2009-11-28
This may be helpful too, although Karmic is a bit different:
[http://humphreybc.wordpress.com/2009/11/27/understanding-ati-linux-drivers/](http://humphreybc.wordpress.com/2009/11/27/understanding-ati-linux-drivers/)
You'll recognize it from the other conversation in this forum that we're both posting in.
-Admiralspark

---

### Post by admiralspark on 2009-11-28
Wait! I just realized what's going on....did you know that you can install the catalyst control center from the Software Center? Granted, it's probably not the *latest* release but it should be stable!

---

### Post by jamieleshaw on 2009-11-28
errrrrrrr ;)

---

### Post by u.b.u.n.t.u on 2009-11-28
Hi, the following post may be of interest to you:

[http://ubuntuforums.org/showthread.php?t=1311739](http://ubuntuforums.org/showthread.php?t=1311739)

---

### Post by humphreybc on 2009-12-06
> **MichaelFTW said:**
> Hello, I'm having trouble understanding what I'm supposed to do to install the ATI catalyst display drivers.

First, after I download them, I type in (Are there code tags?) "sudo sh /home/michael/Desktop/ati-driver-installer-9-11-x86.x86_64.run"

Okay, that I understand, but after that, I've heard I need to do something with xorg.conf.

Edit it? Update it?

Thanks in advance.

Oh, something that might be important, I'm using the 64bit Ubuntu.

Hi there, I'm the author of the guide to ATI drivers that admiralspark posted just before.

So you've downloaded the .run file to your home directory, and you've run the command in terminal to install it. And it's installed correctly? What did it say, anything unusual?

In a terminal type this and tell me what it says:

```

aticonfig

```

and you can also try this:

```

aticonfig --initial -f

```

That should set up your Xorg.conf to use the ATI drivers, if it hasn't already picked it up automatically.

If you don't have the "Catalyst Control Center" in your menu, you can actually run it via a terminal. I think the command is something like:

```

amdcccle

```

But I'm not 100% sure. If you haven't already, download the PDF manual off ATI's driver page for the same version you downloaded.

I'm sorry for my vagueness, I haven't used the proprietary drivers from ATI for a few months now - been using the good old reliable open source drivers. And now that they [provide 3D for my chipset]("http://humphreybc.wordpress.com/2009/12/04/enable-3d-support-on-r600r700-with-the-open-source-radeon-driver/") it's all good!

EDIT: And yeah, it is dpkg-reconfigure -phigh xserver-xorg - except this command [won't do anything anymore.]("http://ubuntuforums.org/showthread.php?p=8447548")

Last time I messed around with the Xorg.conf file in Karmic I had to re-write the damned thing from scratch myself.

Code tags are like this:

[CODE ]
[/ CODE]

Except without the spaces.

- Benjamin

---

### Post by kronictokr on 2010-01-06
catalyst 9.12 is out , for 64 bit try this

BACK UP ANY IMPORTANT INFO!!!!!!!!!!!!!

BACK UP ANY IMPORTANT INFO!!!!!!!!!!!!!

[COLOR="black"][COLOR="Green"]**Install the fglrx Driver from ATI Catalyst 9.12 For Ubuntu 9.10 Karmic**[/COLOR][/COLOR]


We have to create a folder to enable the instalation process
          location  filename
            VVVV       VVV
create /usr/share/ati "ati"

to do this, enter in a terminal the following command

sudo nautilus

then click "file system" from the left side of the window, then double click the file "usr" and the same with "share". once inside the "share folder, right click on a blank space, click create file, name it "ati".  

leave the nautilus window open while you do the next step

download the 64bit driver from this link
VVVVVVVV
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-12-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-12-x86.x86_64.run)

now copy the downloaded file, or drag it into the file you created , (/usr/share/ati  <location reminder )still open in your nautilus window.

when you have placed the "ati-driver-installer-9-12-x86.x86_64.run" file into /usr/share/ati , close your nautilus window, and type the next command into a terminal.

sudo sh /usr/share/ati/ati-driver-installer-9-12-x86.x86_64.run --buildpkg Ubuntu/karmic

this will take a couple minutes as it gathers the proper pakages for your ati gpu. it will create debs and a change log , that will install with the following method

sudo dpkg -i *

there will be missing dependancies, go to SYSTEM>>>SYNAPTICS , and select edit top left , scroll down to and click on fix broken pakages. the click on apply, and lastly click on reload.

now go back to your terminal (to ensure ALL neded pakages are installed, and correctly follow this process exactly)
so, like i was saying, in your terminal, enter the following commands

sudo dpkg -i *

sudo aticonfig --initial

sudo sh /usr/share/ati/ati-driver-installer-9-12-x86.x86_64.run --buildpkg Ubuntu/karmic


sudo dpkg -i *

sudo aticonfig --initial

sudo reboot

MAKE SURE TO COMPLETE ALL THE STEPS BEFORE YOU REBOOT!!

AFTER YOU REBOOT
vvvvvv
to confirm , in a terminal type

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200
OpenGL version string: 3.2.9232

if you get errors, 
do this again, but i suggest you get it right the first time

sudo sh /usr/share/ati/ati-driver-installer-9-12-x86.x86_64.run --buildpkg Ubuntu/karmic

sudo dpkg -i *

sudo aticonfig --initial

sudo reboot



references
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_910_linux.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_910_linux.pdf)

---

### Post by Laysan_A on 2010-03-01
So, michaelFTW, did it work?

I ask because I also have a 3200 - though mine is integrated (and also because the thread's not marked as solved).

---

