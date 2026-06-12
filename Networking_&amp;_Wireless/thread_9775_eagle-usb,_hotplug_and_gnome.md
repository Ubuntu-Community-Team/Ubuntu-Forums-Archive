---
title: "eagle-usb, hotplug and gnome"
date: 2005-01-01
forum: Networking &amp; Wireless
---

### Post by Bart Van on 2005-01-01
After a lot of time spent wrestling with the eagle-usb driver for my wretched ADSL modem (USB Sagem Fast 800), maybe it's time to put down some of my experiences for those coming after me...

Essentially, I encountered two problems (it took me some time to relate them to eagle-usb):
1. bootup didn't get past hotplug unless I unplugged my modem first
2. gnome did very strange things for no apparent reason: panel and menus didn't appear anymore at startup, nautilus didn't launch, freezing, etc.

This happened using the .deb packages for eagle-usb from the ubuntu repositories.

The solution for me was:
- uninstall completely the .deb packages```
sudo apt-get remove --purge eagle-usb*
```- install **manually** the [eagle-usb-2.0.0.tar.bz2](http://baud123.free.fr/eagle-usb/eagle-usb-2.0.0/eagle-usb-2.0.0.tar.bz2)  driver, making sure **not** to connect at boot (to resolve dependencies I had to install the gcc and linux-headers packages first) - see [eagle-usb.org](http://eagle-usb.org) for more info
- I also installed [hotplug version 0.0.20040329-16](http://packages.debian.org/testing/admin/hotplug) from debian testing, I'm not sure if this is necessary but now that I got everything working, I'm not going to downgrade again.
- always use startadsl **with the option -s**; so to (re)start my connection I do ```
sudo stopadsl
sudo eaglectrl -w
sudo startadsl -s
``` using a tiny script I made that I launch with a nice button on the gnome-panel...

Well, maybe, hopefully, this information can save someone the various days of googling, fiddling and rebooting it took me before I got here - with a nice, shining, free Ubuntu Warty-desktop fully functional in front of me, yihoo  :D

(I haven't the slightest idea if this is necessary, good, bad, or relevant, but to be complete: along the way I also installed gamin...)

---

### Post by samaki on 2005-02-16
Well i'm wresling with my SAGEM modem as well. 

Thanks for you suggestions. You suggested the following: 
to resolve dependencies I had to install the gcc and linux-headers packages first. 

How does this work? How can i install the gcc en the linux-headers packages. Where can i find them?

The following is, how could i manually install the eagle-usb package? How does this work.

I think i dont need to tell you i'm a newbei for linux.

perhaps you could help me.

Samaki

---

### Post by Bart Van on 2005-02-16
[list]
[*]To install packages, use Synaptic (somewhere in the menu - I'm not at my Ubuntu-machine right now).  Do a search for "gcc" and for "linux-headers", and install the appropriate version. That is, if you are connected with your ubuntu-machine of course - which probably is not the case.

[*]If not, find out the appropriate versions first (see next paragraph) while in Ubuntu, then download the necessary packages from some other operating system/machine (search around in [http://cpan.cybercomm.nl/pub2/ubuntu/pool/](http://cpan.cybercomm.nl/pub2/ubuntu/pool/) for instance), and then copy them from wherever they were onto your ubuntu-system.  Then install them one by one with, in a terminal: ```
sudo dpkg -i filename.deb
```

[*]Now what is the appropriate version for gcc and linux-header? 
To know what gcc-version to install, in a terminal type ```
sudo cat /proc/version
```
You should see something like "gcc-3.3" in the output, that's the gcc you should install.
For the linux-header-version, in a terminal type```
sudo uname -r
``` which will give you the right number.
(This is also explained in the [eagle-usb-2.1.1 wiki](http://dev.eagle-usb.org/wakka.php?wiki=EagleUsb211) .

[*]To install the eagle-usb driver manually, download it first (latest version is eagle-usb-2.1.1.tar.bz2) from [baud123](http://baud123.free.fr/eagle-usb/eagle-usb-2.1.0/eagle-usb-2.1.1.tar.bz2)  or from [sourceforge](http://sourceforge.net/project/showfiles.php?group_id=81588&package_id=83540&release_id=304321) . Download the file for instance in your /home/yourname/ folder.

[*]Move the driver to /opt and install it: in a terminal window type ```
sudo mv /home/yourname/eagle-usb* /opt
cd /opt
sudo tar jxvf ./eagle-usb-2.1.1.tar.bz2
```
This will create a subfolder in /opt; cd into this subfolder```

cd eagle-usb-2.1.1
```
And install the driver:```

sudo ./configure
sudo make uninstall
sudo make clean
sudo make
sudo make install
sudo eagleconfig
```
Answer the questions, I chose NOT to connect at startup (gave me problems), but you can always try "yes".
To connect type ```
sudo startadsl -s
```
You should be connected. 
To disconnect, type ```
sudo stopadsl
```
In case of trouble, look carefully at the output from "sudo ./configure" which should give you some hints...

[*]If something doesn't work, try tweaking around and restart the process from "sudo eagleconfig" (be sure to cd to /opt/eagle-usb-2.1.1 first), or from "sudo ./configure".

[*]There's more info at [http://dev.eagle-usb.org/wakka.php?wiki=EagleUsb211](http://dev.eagle-usb.org/wakka.php?wiki=EagleUsb211), or in general on [the eagle-usb website](http://www.eagle-usb.org/)  (mostly in French, but there are forums in other languages)
[/list]

You can also try to install the debian-packages for the eagle-usb-driver instead of installing it manually; download them from [http://download.gna.org/eagleusb/eagle-usb-2.0.0/](http://download.gna.org/eagleusb/eagle-usb-2.0.0/) (all three that end with .deb), and install them with ```
sudo dpkg -i filename.deb
``` This will not save you the trouble of finding and installing gcc and linux-headers **first** however, because you will need them anyway.

Don't forget: I'm far from an expert myself and not at my Ubuntu-machine now, so use at your own risk ;)

Good luck.

---

### Post by MttJocy on 2005-04-05
I am having a similar issue, excluding the gnome exhibiting unusual behaviour but the boot problems and although my modem get sync just fine it fails to connect, having tried all the ideas mentioned here without sucess im really at a loss as to what to do here, I am still quite new to linux and am having no luck with this.

---

### Post by Bart Van on 2005-04-06
[QUOTE=MttJocy]I am having a similar issue, excluding the gnome exhibiting unusual behaviour but the boot problems and although my modem get sync just fine it fails to connect, having tried all the ideas mentioned here without sucess im really at a loss as to what to do here, I am still quite new to linux and am having no luck with this.[/QUOTE]
 The latest hotplug (for Warty) seems to work just fine for me (I updated a few days ago...).

(Except for an ALSA sound issue which is solved here: [http://ubuntuforums.org/showthread.php?p=45436#post45436](http://ubuntuforums.org/showthread.php?p=45436#post45436))

---

### Post by MttJocy on 2005-04-06
Where is the download for this and how do I install it on ubuntu bearing in mind package manager download is not possible as I have no connection method under ubuntu I am writing this under mandrake which is what I want to get rid of, I am as I say kinda new to this so step by step versions would be what I would need to figure it out :???: 

Thanks for your fast reply so far, I really want to get ubuntu up and running :D

[EDIT] Sorry I found the link in another of your posts and got it installed but it did not work for me :(

[EDIT2] This post is out of date I bought an ethernet modem/router sorry for wasting time :/

---

### Post by Avatar on 2005-04-15
FIRST OF ALL: REALLY REALLY REALLY THANK YOU!!!!
finally I could connect with my aethra starmodem due to your advices Bart Van

Really it's a strange thing..

I installed the drivers on my notebook but I can't on my desktop..

and the two ubuntu i've on each pc are very very similar!!!

the problem I've got is that the modem can do the syncro and seems to be ok.. but when I try to connect the light 'data' blinks twice then it stops.. and I got the responso 'Unable to connect' Oo

I tried to move the modem to the notekoob, from which I am writing right now, and all went ok!!!

any ideas?

---

### Post by Bart Van on 2005-04-15
[QUOTE=Avatar]FIRST OF ALL: REALLY REALLY REALLY THANK YOU!!!!
finally I could connect with my aethra starmodem due to your advices Bart Van

Really it's a strange thing..

I installed the drivers on my notebook but I can't on my desktop..

and the two ubuntu i've on each pc are very very similar!!!

the problem I've got is that the modem can do the syncro and seems to be ok.. but when I try to connect the light 'data' blinks twice then it stops.. and I got the responso 'Unable to connect' Oo

I tried to move the modem to the notekoob, from which I am writing right now, and all went ok!!!

any ideas?[/QUOTE]
 Nice to know I could be of some help :)

However, "1 cup of Ubuntu" is not enough to help you further, I'm afraid.

Maybe you can try the eagle-adsl forum on [http://forum.eagle-usb.org/](http://forum.eagle-usb.org/), it's mainly in French but there's a special section "for English speaking"...

Good luck! 
(And keep trying, as far as I'm concerned Ubuntu is by far the best Linux distribution available.)

---

### Post by Avatar on 2005-04-19
I've already opened a good topic in that forum but I couldn't get any help form it.. You know, no answers at all..

so.. I'll keep on trying since I've found a solution, if you get any info about my problem write here ;) I will do the same!

---

