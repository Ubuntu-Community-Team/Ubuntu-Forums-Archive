---
title: "WMP54GS on Ubuntu 8.04 FIRMWARE ERROR!"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by Bascote on 2008-03-28
hey guys,

I just installed Ubuntu 8.04 on my 64 bit computer, BEAUTIFUL (on a second hard drive)

The thing is, I've had Ubuntu 7 on my little sister's computer ( I love not having to worry about viruses/spyware/adware/etc) but learning how to use the command line properly seems to end up making it just as big a headache!

Her computer has a WMP54GS card and all was working well with Ubuntu 7 but I figured I wanted to upgrade her to Ubuntu 8 (beta) and see if it had an easier feel for her.

Well when I boot up the computer I get a firmware error telling me to go to:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

So I tried going there and following instructions, and let me say, I'm not trying to float my boat but I think im fairly good with windows (being an IT Intern and all) but I'm almost completely lost trying to get this thing working.

I tried the first couple sets of steps for firmware 4.8 and 4.15 (just praying it would work even thougth I wasn't sure what I was doing!) and it did not work for me period.

I got a couple commands going but it turned up with a lot of errors.

If someone could tell me what exactly it is I am suppose to do I'd appreciate it much! God willing I'll be able to figure this out with some help and learn something from it.

**KEEP IN MIND SHE IS NOT CONNECTED TO THE INTERNET, EVERYTHING TO DOWNLOAD I DOWNLOAD ON MY COMPUTER AND TRANSFER IT VIA USB DRIVE**

1) I log into the root account
2) Open terminal
Now I'm lost, what is it that I have to download and what do I do then? Please remember that because I have to transfer the packages to her computer I'll probably skip steps like wget for the packages (or anything else that needs internet connection) and I also extract the packages first and put them on the usb.

---

### Post by unknown03 on 2008-03-28
Hey, first of all:
Never, ever....ever-ever-ever-ever-ever-ever-ever-ever log into the root account.. use the command SUDO for your root privileged needs

second..I've had problems with my WMP54GS driver in both 7.10 and 8.04 beta.. but this post got me up and running [http://ubuntuforums.org/showthread.php?t=734003&highlight=rmmod+-r+ssb]("http://ubuntuforums.org/showthread.php?t=734003&highlight=rmmod+-r+ssb")

in a nutshell, your going to want to download the Windows drivers (WMP54GS.inf) ..install ndiswrapper and/or ndisgtk (which is on your 8.04 disk -- go to the Synaptec Package Manager and search for "ndis").. 3. install the drivers (ndisgtk will probably be the easiest for you -- make sure the wmp54gs.inf is in the same folder as the *.cat and *.sys file) and follow the steps on the link provided..

hope this helps!

---

### Post by Bascote on 2008-03-29
Thanks I've been trying similar things from other threads but I'm running into a problem with ndiswrapper..

My sister upgraded straight from the synaptic package manager (not from the cd) and no matter what I've tried (I've tried the 7.1 cd) and I can't get it installed and whenever I try

apt-cdrom add

I get an error like it can't mount E:

I have the 8.04 cd but its for 64 bit, would that work on her computer which is NOT 64 bit?

---

### Post by unknown03 on 2008-03-29
I'm confused, what cant you install? ndiswrapper?

I'm not exactly sure if the 64bit cd even has 32-bit appz on it.. But I wouldnt waste my time with trying it unless someone else can confirm.. But no, 64-bit wont work on 32-bit..

try popping in the cd and enable all the repositories in the synaptec package manager.

open the terminal and type:

"sudo apt-get install ndiswrapper-common"

and 

"sudo apt-get install ndiswrapper-utils-1.9"

see if that will install it correctly..after which you want to install the windows drivers with ndiswrapper.. download the drivers that i have attached and extract them somewhere..

open the terminal and type:

"sudo ndiswrapper -i /location/of/drivers/WMP54GS.inf"
and
"sudo ndiswrapper -i /location/of/drivers/WMP54GSa.inf"

keep in mind everything is case sensitive

check to see if its installed by typing in the terminal:

"ndiswrapper -l"

if everything is well and present then youll want to blacklist the bcm43xx drivers by adding:

"blacklist bcm43xx" 

at the end of /etc/modprobe.d/blacklist

to open and edit it type in the terminal:

"sudo gedit /etc/modprobe.d/blacklist"

now after that is done, and provided everything is going smoothly without error, type in:

"sudo gedit /etc/init.d/wirelessfix.sh" and paste:

```
#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44
```

and save it... BTW, this isnt my work

after that, type in the terminal:

"cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh"
and
"sudo update-rc.d wirelessfix.sh defaults"

then restart your sisters computer, log back in, and update us on your venture :D

EDIT:
I included the .deb packages for you to install for ndiswrapper and ndisgtk

---

### Post by unknown03 on 2008-03-29
Also, I mention that way to get the drivers working because those are alot better than the bcm43xx-fwcutter (in my experience) ...but if that doesnt work for you then you can set it up rather simple..

download the files I provided.

Install "bcm43xx-fwcutter_20060108-6build1_i386.deb"

then extract "wl_apsta-3.130.20.0.o.tar.gz" someplace (preferably the Desktop)

open the Restricted Drivers (System -> Administration -> Restricted Drivers Manager)

and click the tick box to enable the wireless adapter..after which a window will come up, asking for the firmware, click browse and give the location of wl_apsta-3.130.20.0.o

then u should be seeing networks!

Keep in mind youll need to "unblacklist" the bcm43xx from /etc/modprobe.d/blacklist by deleting its entry and saving it..

---

