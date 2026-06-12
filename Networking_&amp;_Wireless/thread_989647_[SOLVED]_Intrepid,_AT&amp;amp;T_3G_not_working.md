---
title: "[SOLVED] Intrepid, AT&amp;amp;T 3G not working"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by wallcrawler78 on 2008-11-21
Hey party people.  I have an EEE-pc (1000h) loaded with ubuntu intrepid.  I just purchase the USBconnect Quicksilver3G adapter.  When I reboot with the adapter connected it doesn't appear to show up in connection manager automatically or anything.  It actually shows up as a CDrom for some reason, well at least the icon would suggest as much.  If I go thru the wizard and add a AT&T connection, it doesn't appear to do anything because I cant pick that connection like i can a wifi or hardwired connection.

Any help would be much appreciated.  I also attached my dmesg output incase that might help.

I have read that for others, it was as simple as pluging in, presto!  For me, not so much.

Cheers!:guitar:

---

### Post by lswb on 2008-11-21
Some of these devices have 2 (or more) USB modes or interfaces built in. The one that identifies as a CD actually has (get ready for it) WINDOWS drivers on it, so it can be used on a windows system without needing an installation CD. Then after the drivers are installed, it switches to or uses the modem/3G interface. This website may have a solution for your device, or help get you started on finding one:

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

---

### Post by wallcrawler78 on 2008-11-23
Thanks for the info.  I downloaded and installed the .deb.  Now if I can just figure out how to use the damn thing.  There doesnt seem to be that much documentation on how to use the thing...  to bad I cant just plug the thing into my windows PC, put it in the correct mode, then plug it into my Linux box.... I figure it probably is PC by PC basis.

Anyone have any idea how to use the USB_modeswitch application?  Argh...  It might not matter anyways since it is not supported by the app it doesnt look like.

Perhaps if i can figure out how to monitor the drivers in windows and create a profile which will work with USB-ModeSwitch...  Any advice would be much appreciated.

---

### Post by wallcrawler78 on 2008-11-23
I installed ReZero from this site..
ttps://launchpad.net/~martijn/+archive

Now the ZeroCD doesnt show up.  but network over 3G still doesnt show up as an option...

---

### Post by wallcrawler78 on 2008-11-23
Ok, so after installing rezero and HSO connect and HSO link beta drivers I seem to get a connection (see attached screen shot).  But, I dont actually seem to be on the Internet.  If i try to go somewhere in firefox I get nowhere.  And connection manager doesnt show anything being connected. Any Suggestions?

---

### Post by lswb on 2008-11-23
I'm not sure it affects intrepid, but in hardy Network Manager doesn't recognize ppp or other connections that it did not initiate itself, and causes some applications like firefox and evolution to start in offline mode. From firefox menu, see File/Work Offline and uncheck the box. 

If this is the problem, you can solve it for Firefox by opening about:config and setting toolkit.networkmanager.disable to TRUE.

---

### Post by wallcrawler78 on 2008-11-23
Well, it appears to be registering some form of signal using HSOconnect.  But it doesnt want to connect.  It will try to connect, freeze, then re-launch.  I connected the modem to a windows machine and it ran like a champ.  I am about at my whits end on this one... I am so close, but I am not sure how to trouble shoot it from here.  Any advice would be much appreciated.

I tried the Offline/online modes suggested in the prior posting, but that didnt seem to do it either.

---

### Post by wallcrawler78 on 2008-11-26
Just an update.  I installed "gcom" and ran it.  It comes up as saying "Can't open GlobeTrotter /dev/modem."  See attached screen shot showing HSOconnect as well as the terminal output.

---

### Post by lswb on 2008-11-26
I'm speculating here, but my guess is that your gcom program may work if you can specify the correct device instead of /dev/modem. Do you know what device is created when you plug in your quicksilver adapter? it might be something like /dev/ttyACMO or /dev/USB0 or something else in the /dev directory. You can try a few things to find out if you don't know: after plugging in the adapter, run the command "dmesg" in a terminal. A page or 3 of text will scroll by but at the end may be some lines indicating a new device was installed or registered. 

Another thing you can do, is before plugging in, open a terminal and run the command "ls /dev >before" Then plug in the device, wait a few seconds, and run "ls /dev >after" After that run the command "diff before after" and see what new devices were created when the adapter was plugged in. There may be more than one, post them here please, I'd like to see them for future reference.

In you gcom program, see if it will let you specify a device to use instead of /dev/modem and substitute the device name you discovered above. If it has no such configuration option, you can make a symlink to it with the name /dev/modem like so, again in a terminal:

sudo ln -s /dev/name-to-try /dev/modem

and try the gcom program again.

Good luck, hope you can get it going and add to the knowledge base as well!

---

### Post by Pharscape on 2008-11-28
Hi All,

Just to let you know - Quicksilver uses a slighly different AT command for the Internet connection than the other devices from Option. I have been researching this and will post a new version of HSOconnect to support Quicksilver (hopefully over the weekend) on [www.pharscape.org](www.pharscape.org). I am also starting a support page for this device with the details of the differences as I find them.

This means that the connect.sh script that is supplied with the driver will also need modification.

Cheers,
Paul

---

### Post by wallcrawler78 on 2008-11-28
Hey thanks!  I will try out the above so we can capture the output.  I am going to reload my eee-pc this weekend so it will be a fresh start.  As soon as the new HSOconnect comes out, I will give that a try.  If there is anything I can do to help, let me know.

I will document each step so that from a clean install it makes sense.  I have installed so many apps and tweaks, that i would not want to lead anyone down a rabbits hole.

Thanks to everyone for your support!

Dan

---

### Post by wallcrawler78 on 2008-12-02
Ok, i reloaded Ubuntu.  I installed Rezero using the repository I found on Launch pad.Then I installed the updated HSOconnect and HSOlink.  I had to plug in my At&t settings, Presto! It works!!!

The At&t settings can easily be found by adding a wifi connection in network manager.  then clicking edit to view the defualt settings.

Thanks again to Paul at Pharscape!  Without your support we would all be lost!

Dan

---

