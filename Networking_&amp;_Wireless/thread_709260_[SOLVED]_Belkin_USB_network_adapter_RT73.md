---
title: "[SOLVED] Belkin USB network adapter RT73"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by carterrocks on 2008-02-27
Okay I've tried ALOT of tuts but I can't come up with a way to get the adapter to work!  Most of the tuts are aimed at a chipset which is not my own, mine uses RT73.
Interestingly, I removed network-manager and plugged in my adapter and it started picking up networks, I couldn't connect to them but...
Anyways I NEED help!!!!!  I'm so stressed over this I even changed OS trying to get it to work (fedora- I couldn't even get it to work on that!  I also didn't like it, looked like a cheap version of ubuntu)
HELP HELP HELP!!!!!

---

### Post by james_vanb on 2008-02-27
I'm using xubuntu 7.10 Gutsy - Using Belkin Wireless g Network Adapter with the rt73 Driver.  Have posted this solution in a couple of threads.  Give it a shot - It worked for me.

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands (If not using Xubuntu, substitute commands as appropriate):

sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb

I'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (mousepad for Xubuntu - gedit for Ubuntu) as follows:

sudo mousepad /etc/modprobe.d/blacklist

add rt2500usb and rt73usb to end of list, save and close.

REBOOT

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin".
Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following :

sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf

Insert the wireless adapter.

Now issue the following commands:

sudo depmod -a
sudo modprobe ndiswrapper

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows:

sudo mousepad /etc/modules

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

sudo ndiswrapper -m

Reboot

You should now have a connection. Roaming mode works sporadically, so I manually configure. Left click on the network manager at the upper right corner and enter manual configuration. Open wifi properties. Untick "enable roaming". Next to Network name, you should be able to click on the arrow and a drop down will show available networks, click on yours. Set Password type to WPA personal. Set Configuration to Automatic configuration (DHCP). I don't use WEP yet, but if you do, you may have to enter your password in Network password.

Good Luck!!

---

### Post by carterrocks on 2008-02-28
> **james_vanb said:**
> I'm using xubuntu 7.10 Gutsy - Using Belkin Wireless g Network Adapter with the rt73 Driver.  Have posted this solution in a couple of threads.  Give it a shot - It worked for me.

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands (If not using Xubuntu, substitute commands as appropriate):

sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb

'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (My default is mousepad) as follows:

sudo mousepad /etc/modprobe.d/blacklist

add rt2500usb and rt73usb to end of list, save and close.

REBOOT

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin".
Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following :

sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf

Insert the wireless adapter.

Now issue the following commands:

sudo depmod -a
sudo modprobe ndiswrapper

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows:

sudo mousepad /etc/modules

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

sudo ndiswrapper -m

Reboot

You should now have a connection. Roaming mode works sporadically, so I manually configure. Left click on the network manager at the upper right corner and enter manual configuration. Open wifi properties. Untick "enable roaming". Next to Network name, you should be able to click on the arrow and a drop down will show available networks, click on yours. Set Password type to WPA personal. Set Configuration to Automatic configuration (DHCP). I don't use WEP yet, but if you do, you may have to enter your password in Network password.

Good Luck!!

It didn't work but thanks.  More help please

---

### Post by james_vanb on 2008-02-28
Sorry it didn't work for you.  What do you get when you run ndiswrapper -l?

---

### Post by carterrocks on 2008-03-03
> **james_vanb said:**
> Sorry it didn't work for you.  What do you get when you run ndiswrapper -l?

I can't get to the computer with Ubuntu on at the moment.  What should I be getting and how does this help?

---

### Post by james_vanb on 2008-03-03
This will tell you if rt73 has loaded at all.  If nothing listed, then driver never loaded.  Some problem in process you're using.

if you get the following:

rt73 : driver installed
        device (050D:705A) present (alternate driver: rt2500usb)

Driver loaded and is conflicting with rt2500usb.  Not blacklisted, etc.

or, you may get this:

rt73 : driver installed
        device (050D:705A) present (alternate driver: rt73usb)

If not working, then your driver is conflicting with rt73usb (An experimental driver that doesn't work yet).  Not blacklisted, etc.

A way of trying to figure out why your's isn't working.

There is a possibility that your driver has been associated with one that conflicts during your previous efforts.

Possible solutions, uninstall rt 73, rt2500usb and rt73usb with usb adapter unplugged and trying again.  Or, uninstall ndiswrapper and try again.  or, clean install and try again.

---

### Post by Keltenbleich on 2008-03-11
Dear Carterrocks,

I have installed ubuntu on two pcs a few days ago. (Ex Windows XP)

I use a USB dongle (Conceptronic C54RU with a rt73 driver) to access a wireless network shared by a secondr pc. The second pc is doing fine, as it is directly connected to the router through a RJ-45 switch)

Since I have installed Ubuntu, I have problems with pc number one (the one with USB dongle).

The internet connection only lasts a few minutes, then I have to unplug and replug the USB dongle to get the connection back.

As the rt73 driver is not supported by LINUX it should not function at all in the first place...but it does, at least for a couple of minutes. Do you have an idea why this is so?

tks+rgds
Keltenbleich

---

### Post by allergic1 on 2008-03-16
Have you seen this site? It lists the rt73 as supported. Maybe it will help to use the version here.

---

### Post by allergic1 on 2008-03-16
Well, how about this site then ;)

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

---

### Post by nattyrosco on 2008-03-17
> Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands (If not using Xubuntu, substitute commands as appropriate):

sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb

'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (My default is mousepad) as follows:

sudo mousepad /etc/modprobe.d/blacklist

add rt2500usb and rt73usb to end of list, save and close.

REBOOT

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin".
Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following :

sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf

Insert the wireless adapter.

Now issue the following commands:

sudo depmod -a
sudo modprobe ndiswrapper

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows:

sudo mousepad /etc/modules

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

sudo ndiswrapper -m

Reboot

Sorrry to say that dongle insertion freezes my system...
I thought it was the depmod command, but actually is the point of connect.
Anyone else see this before / have any ideas?

Quite frustrated.
Thanks in advance.

---

### Post by eldragon on 2008-03-17
the serialmonkey driver is in constant development, i had the best result with a rt73 chipset with their latest builds from the cvs repository.

building the driver and installing it is just plain easy, ive already done it under gutsy and now under hardy alpha6. both times succesfully having a working wireless connection. i trend to update the driver constantly and each time i get better results.

so, here it goes:

first of all, blacklist rt73usb from loading. to do this:
```

sudo gedit /etc/modprobe.d/blacklist

```

and append to the end of the file "blacklist rt73usb" without the quotes


then in your home dir do: 
```

~$ wget http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz
~$ tar -xvzf rt73-cvs-daily.tar.gz

```

which will unpack the latest sourcecode from the serialmonkey driver

now you ought to make sure you got everything needed to build the module, so to do this, you have to:
```

$ sudo apt-get install build-essential linux-headers-`uname -r`

```

then

```

$cd rt73[tab]/Module

```
note that you have to hit the tab key where [tab]

and you have to build the module:
```

$ make
$ strip -S rt73.ko
$ sudo make install
$ sudo rmmod rt73usb
$ sudo modprobe rt73

```

some explaining: 
make: builds the module
strip -S etcetera: removes some extra debugging stuff you wont be needing.
sudo make install, installs the module
sudo rmmod rt73usb, removes from memory the old module that doesnt work like it should
sudo modprobe rt73, loads our new module.

after this, you should have to do 
```

sudo ifconfig wlanX up

```
where X is a number, start from 0 and start moving upwards. this depends on how much tinkering youve been doing before modprobing.

next step is to install rutilt, which is a graphical interface to manage wireless hotspots.
```

$ sudo apt-get install rutilt

```

this program should be run preceded with sudo, otherwise it just wont save profiles, or anything.
under gutsy, its quite buggy, newer versions get better. the one in hardy didnt give any troubles.

now everytime you reboot, you start rutilt with 
```

$ sudo rutilt &

```
and use it to configure your network, or pick a profile. the & at the end, leaves the process running after you shutdown the terminal.

i hope its been clear enough.

---

### Post by james_vanb on 2008-03-18
Check out this thread:

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=365060&highlight=wireless+usb+freezes](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=365060&highlight=wireless+usb+freezes)

Seems to be a new problem involving various usb adapters.

---

### Post by james_vanb on 2008-03-18
Check out this thread:

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=365060&highlight=wireless+usb+freezes](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=365060&highlight=wireless+usb+freezes)

Seems to be a new problem involving various usb adapters.

Sorry for repeat.

---

### Post by nattyrosco on 2008-03-18
Thanks for the reply and advice.

eldragon, in following your inst., hit a snag at about the point of rutilt.

> natty@natty-desktop:~/rt73-cvs-2008031805/Module$ sudo rmmod rt73usb
ERROR: Module rt73usb does not exist in /proc/modules
natty@natty-desktop:~/rt73-cvs-2008031805/Module$ sudo modprobe rt73
natty@natty-desktop:~/rt73-cvs-2008031805/Module$ sudo ifconfig wlan0 up
natty@natty-desktop:~/rt73-cvs-2008031805/Module$ sudo apt-get install rutilt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package rutilt
natty@natty-desktop:~/rt73-cvs-2008031805/Module$ 


synaptic is a no-go

Do you see anything I have missed?

---

### Post by eldragon on 2008-03-18
> **nattyrosco said:**
> Thanks for the reply and advice.

eldragon, in following your inst., hit a snag at about the point of rutilt.



synaptic is a no-go

Do you see anything I have missed?


rutilt is in the universe repositories, so you should enable them on system --> software sources

then do 
```
 sudo apt-get update 
```

and try to install it again.

anyway, you could always try the command line iwconfig util to setup your wireless, at this point you should already have a working wireless adapter.
do 
```

$ man iwconfig

```
to learn how to :) a bit more gruesome, but it should work ;)

---

### Post by nattyrosco on 2008-03-18
Thanks eldragon.

Still no go on rutilt.

I'm using feisty... is this why?

I certainly appreciate your help and insight, however.
I've been struggling, and would like for this bad boy to function... but at any rate I feel like i've gotten closer.

---

### Post by nattyrosco on 2008-03-19
eldragon, You are awesome!

I updated to gutsy overnight, found utilt, and now I'm SMILIN!

Not only was your solution accurate, but to offer the code rationale was elegant and informative for a greenhorn like myself.  It is much kinder to tell someone why they do something as you show them.  Thank You Thank You Thank You!

anyone reading this in the future should know to stop here for this is the solution!

I spent a lot of time screwing up and following useless threads, but if you have a Belkin G USB Wireless adapter, rt73 drivers, and Gutsy... stop looking because THIS SOLUTION WORKS!

Thanks again!:guitar:

---

### Post by eldragon on 2008-03-19
> **nattyrosco said:**
> eldragon, You are awesome!

I updated to gutsy overnight, found utilt, and now I'm SMILIN!


thanks :) i didnt know you had feisty, glad it works

> **nattyrosco said:**
> 
Not only was your solution accurate, but to offer the code rationale was elegant and informative for a greenhorn like myself.  It is much kinder to tell someone why they do something as you show them.  Thank You Thank You Thank You!

thanks again :D

> **nattyrosco said:**
> 
anyone reading this in the future should know to stop here for this is the solution!

I spent a lot of time screwing up and following useless threads, but if you have a Belkin G USB Wireless adapter, rt73 drivers, and Gutsy... stop looking because THIS SOLUTION WORKS!

Thanks again!:guitar:

this might not be so true. there are dozens of different adapters based on this chipset, and other ralink chipsets that use the same drivers, some might have problems with these drivers. and some might not, there are great chances this will get your wireless up and running since the drivers in question are in constant development / review. anyway, im glad it helped :)

and i must certainly add that most stuff i wrote here, are usually snippets / recompilations of other howtos on getting these drivers up and running :D

---

### Post by Stryde on 2008-04-10
Hey,
 Finally, a tutorial that even my grandparents could understand. It worked perfectly on my Belkin Wireless G USB Network Adapter. You are my hero. My only suggestion that instead of ```
sudo mousepad....
```

I would use
```
sudo gedit....
```

gedit is on the ubuntu I use and mousepad isnt >.< so I would suppose that gedit is the way to go :)

anyways, great tutorial, you are my hero :guitar: 5:KS 's

Stryde

---

### Post by james_vanb on 2008-04-12
Stryde,

Glad info in this post helped you.

Mousepad is the default text editor for Xubuntu.  Gedit is the default for Ubuntu.  I've edited appropriately for clarity per your recommendation.

Thanks for the input.

---

### Post by guildofghostwriters on 2008-05-10
I followed this guide and got my rt73 chipset usb dongle working fine in Hardy with rutilt (apart from being unable to remember profiles unless I run it from terminal as root) but lately it's been acting strangely and I'm posting here hoping you have ideas about how I can find out what's going wrong. Sometimes it just fails to connect to the router. There's a windows pc upstairs connecting to the same router (with the same dongle - and I've tried swapping them over to make sure) so I'm pretty sure it's not the dongle or router. Today I watched the terminal output to see what was happening and (forgive my ignorance here - I'm not well versed in the 21st century) it looked like it was making repeated attempts to connect to xx.xx.xx.2 and when that didn't work it said something along the lines of 'no leases - sleeping' and that was that, no connection. The thing is, the windows pc was already using xx.xx.xx.2. Shouldn't it then attempt to connect to an available ip? I switched off the windows pc, rebooted the hardy pc and the router, and now rutilt has connected to xx.xx.xx.2. This is what is currently in interfaces (although when I checked it before reboot it only had the first two lines):

auto lo
iface lo inet loopback



iface wlan0 inet dhcp
wireless-key <my hex key> 
wireless-essid <my essid> 

auto wlan0

I always run rutilt from terminal with:

sudo rutilt -dp default

I'd appreciate any help you can give, or let me know if I should take this problem elsewhere.

Cheers!

---

### Post by james_vanb on 2008-05-10
guildofghostwriters;

Responding to this post with Belkin Wireless USB Rt73 - Using default wireless manager - no problems - not familiar with rutilt - have you tried default wireless manager?  Maybe a configuration issue with retult?  Found this on retult config:

[http://ubuntuforums.org/showthread.php?t=554089&highlight=rutilt](http://ubuntuforums.org/showthread.php?t=554089&highlight=rutilt)

Hope it helps.  Sorry for delay in response.

---

### Post by guildofghostwriters on 2008-05-11
Thanks for replying - no need to apologise at all.

Yesterday I did --purge remove rutilt and reinstalled network manager but it was, if anything, slightly worse. I got rid of nm and reinstalled rutilt because that did work perfectly until recently but that is as bad.

I'll try the how to you linked - thanks - and see how I get on. Cheers!

---

### Post by guildofghostwriters on 2008-05-11
So far, touch wood, that seems to have done the trick. I've only rebooted once so I can't say whether that's it solved forever but it connected first attempt so it's looking good. Thanks again.

---

