---
title: "ndiswrapper and ndisgtk"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by zipteye on 2010-11-24
Still fighting to get my Belkin Wireless USB peice of junk to work with ubuntu.
 
Found where ndiswrapper is, but dont know how to use it, or it isnt set up.
 
Attached a screen shot.

---

### Post by kerry_s on 2010-11-24
ndisgtk is a graphical app, since your in the terminal run "ndisgtk" to start it or find it in the menus & click on it to launch. you then just point it to the windows drivers & it does the rest.

---

### Post by zipteye on 2010-11-24
It says it's not installed.
Need to do: sudo apt-get install ndisgtk
That fails though.
 
(No net connection)

---

### Post by zipteye on 2010-11-24
Heres what it showed me...

---

### Post by kerry_s on 2010-11-24
you can't connect via hard line? it's the easiest way to get what you need.

---

### Post by zipteye on 2010-11-24
It would involve carrying the whole computer into the back bedroom to hard line it into the cable modem.
Blech...

---

### Post by ironic.demise on 2010-11-24
NDISWRAPPER is on the Ubuntu live cd in /pool/main/n
Install the ndiswrapper .deb files from there.
 
use```
 ndiswrapper -i "path to your driver"
then
 sudo modprobe ndiswrapper
```

---

### Post by zipteye on 2010-11-24
Ok, got that done.
ndiswrapper and ndisgtk
 
Heres some of the system info that I show, attached screen shot.

---

### Post by anewguy on 2010-11-24
Indeed, ndiswrapper and ndisgtk are both on the livecd in the /pool/main/n folder.  There is an order to installation, however:

go to /pool/main/n/ndiswrapper and double-click on the ndiswrapper common file first and let it install.

in the same /pool/main/n/ndiswrapper folder, double-click on the ndiswrapper utilities and let them install.

Now go back to /pool/main/n/ndisgtk, double-click on the file there and let it install.

Next you need the Windows XP (XP *ONLY*) drivers for your adapter - the .inf and .sys files.  I normally tell people to copy these to your ubuntu desktop.  Please also note that they must match the "type" of ubuntu - if you are using 64-bit ubuntu, the Windows XP drivers must be 64-bit; similarly if you are using "normal" 32-bit ubuntu, the Windows XP drivers must be the 32-bit drivers.

Go to System/Administration/Windows Wireless Drivers - this starts up ndisgtk.

click on the "new" and point it to the .inf file for your driver (on your desktop if you put them there).

It should install and show your device ready.  If not, stop there and do the following and post the results back here:

iwconfig

lsusb

Remember the following as well:

in network manager, the "Enable Wireless" must be enabled

if you are connecting to a network that is hidden (e.g., not broadcasting it's ESSID) you must use the network manager "connect to hidden network" to set it up.  

if you use encryption, it must match, and the password/passphrase must match

if the router is using MAC filtering, and if you have not connected to the router with this adapter yet, you must put the adapters' MAC in the routers MAC table.

Dave ;)

---

### Post by ironic.demise on 2010-11-24
I've never had a repercussion from installing in revers-order...
Guess I'm lucky.

---

### Post by zipteye on 2010-11-24
Ok.
There was only an .inf file on the Belkin CD. The .sys was an executable.
Installed ndiswrapper and ndisgtk.
 
iwconfig shows:
lo  no wireless extensions
eth0  no wirless extensions
 
lsusb shows:
 
Bus 001 Device 002: ID 050d:945a  Belkin Components

---

### Post by ironic.demise on 2010-11-24
> **zipteye said:**
> Ok.
There was only an .inf file on the Belkin CD. The .sys was an executable.
Installed ndiswrapper and ndisgtk.
 
iwconfig shows:
lo  no wireless extensions
eth0  no wirless extensions
 
lsusb shows:
 
Bus 001 Device 002: ID 050d:945a  Belkin Components

Firstly, the sys and inf should be in the same directory.
secondly, You ONLY ndiswrapper the .inf
thirdly,
```
sudo modprobe ndiswrapper
```
to load it and enable wirelsss.

---

### Post by anewguy on 2010-11-24
You don't have to modprobe ndiswrapper if you use ndisgtk.

You must use BOTH files - the .inf file is a "descriptor" file and the .sys file is the actual guts of the driver.

If you followed my instructions, put both files on the desktop, ran ndisgtk, selected new and pointed it to your .inf file, it should have picked up your .sys automatically as long as you followed what I said.

Please look in ndisgtk (again, System/Administration/Windows Wireless Drivers) and tell us what, if anything shows.  If nothing, do exactly what I told you to do - put the .inf AND the .sys files on your desktop, then in ndisgtk select new and point it to your .inf file.

If that doesn't work, then chances are you have one of the mismatches I mentioned.  In particular, the driver MUST be Windows XP drivers.

Dave ;)

---

### Post by anewguy on 2010-11-24
> **ironic.demise said:**
> I've never had a repercussion from installing in revers-order...
Guess I'm lucky.

Yeah, actually you are lucky.  There are dependencies at work here - the utilities depend on common, ndisgtk depends on common.  At least, that's how it used to work if you tried to install these via the package manager.  I haven't had anyone use the package manager to do so in quite a while, so maybe they've changed the dependecies that used to be there.  It used to be that it quite literally would not install utilities before common and the same for ndisgtk - it would give you error messages instead.

Also, just FYI - if you use ndisgtk, you don't need to do a modprobe on ndiswrapper.  You also don't do the install command to ndiswrapper (sudo ndiswrapper -i xxxxxx.inf).  That is all part of the manual procedures for running ndiswrapper, including depmod -a, adding to modules, etc..  Ndisgtk takes care of all of that for you.

Dave ;)

---

### Post by zipteye on 2010-11-24
Well, I'm running Win 7, but the belkin CD says drivers for XP, Vista, and Win 7.
 
Driver is installed.
 
I dont see any Network Manager on the GUI side of things...
 
USB wirelesss still not working.
 
Even did the sudo modprobe ndiswrapper.
 
I did use ndisgtk though.
 
 
Some config file that I need to change?

---

### Post by anewguy on 2010-11-24
What does ndisgtk show?  Does it show an active device?

In a terminal window (Applications/Accessories/Terminal) type:

sudo ndiswrapper -l <press enter> That's a lower case "L" for "list".  This will tell ndiswrapper to list any devices it is aware of, even bad ones.  If anything is returned on this list post it back here in a reply.

Network Manager is on the top bar of you ubuntu desktop. It should look like a little dot with little curves going up from it (it's supposed to look like radio waves).

Also, what did you do originally with ndiswrapper, etc., before with this adapter?  Anything you did before probably needs to be reversed before we can go forward and make it work.

Dave

---

### Post by zipteye on 2010-11-24
First of all, there is no Radio wave looking icon at the top of the desktop. There's only an icon with two computer. If I click on that it says wired network, and VPN.
 
sudo -l ndiswrapper shows:
net8192su: driver installed
 
I used ndisgtk to install the .sys file.
 
Day before yesterday I reconfigure /ect/modules, and /etc/udev/rules./70-persistent-net.rules.
Both according to some other article to try to get the wireless usb working.
 
/etc/module shows:
lp
rtl8187
#net8192su
 
 
then the other file shows:
 
[FONT=Batang]# This file maintains persistent names for network interfaces.[/FONT]
[FONT=Batang]# See udev(7) for syntax.[/FONT]
[FONT=Batang]#[/FONT]
[FONT=Batang]# Entries are automatically added by the 75-persistent-net-generator.rules[/FONT]
[FONT=Batang]# file; however you are also free to add your own entries.[/FONT]
 
[FONT=Batang]# PCI device 0x10ec:0x8136 (r8169)[/FONT]
[FONT=Batang]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="78:e7:d1:89:89:3d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"[/FONT]
 
[FONT=Batang]#USB device 0x050d:0x705e (rtl8187)[/FONT]
[FONT=Batang]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:a1:cc:21:94", ATTR{type}=="1", KERNEL=="wlan", NAME="wlan0"[/FONT]
[FONT=Batang][/FONT] 
[FONT=Batang][/FONT] 
[FONT=Batang]The 00:24:a1:cc:21:94 is the MAC of the cable modem/router[/FONT]

---

### Post by anewguy on 2010-11-25
I don't know what the other post was trying to tell you, but at least 1 thing was in error - I still need to check the rest.

Notice that ndiswrapper shows net8192su as installed.  I can only assume that when you say you used the .sys file to install it that you mean you used the .inf file, with the .sys file being in the same folder -> you don't specify the .sys file it just HAS TO BE in the same folder as the .inf file.

Notice that what the post you were following had you do was:

load module rtl8187

ignore loading net8192su -> this is the same driver you are trying to load via ndiswrapper.  I've checked my 10.10 default installation, and I don't have a net8192su module to begin with, so I would assume you probably didn't either, so why they had you do this is beyond me at this point.

I don't understand putting your router MAC in the rules either - that may just be something I don't know.  But I would suspect MAYBE it meant your wireless adapter MAC.  I would need to research that to find out.

Your network manager is the 2 computer thing (apparently different on my 10.10).  You need to RIGHT CLICK on that icon to check for the "Enable Wireless".

Please post the link to the article you were following.


Dave ;)

---

### Post by zipteye on 2010-11-25
Okay, heres the other tutorial:
[http://linuxsoftwareblog.com/?p=30](http://linuxsoftwareblog.com/?p=30)
 
I meant the .inf file
I pulled it off the Ubuntu DVD that I made. Ubuntu 10.10 (supposed to be)
So, the .sys (which was an executable) was in the same folder on the DVD as the .inf file. Does that count?
 
When I right click on the computers icon it doesnt list "Enable Wireless"
I believe it says "Enable Network" or "Enable Networking".
 
Heres what I have for the cable modem that has wireless capabilities:
Name (or I guess it would be the SSID) -- MOTOROLA-C2194
MAC -- 0024A1CC2194
Gateway MAC -- 0023A2FFF3ED
 
I've tried both the MAC and the Gateway MAC in 70-persistent-net.rules
ATTR{address}=="00:23:a2:ff:f3:ed", for example.
 
Of course I have a WPA password, but I wont post it here.
Using the WPA Personal option.
 
I'm the one that put the net8192su in /etc/modules
I also tried using rtl8192, in place of rtl8187
 
Stupid wireless USB thing is: Bus 001 Device 002: ID 050d:945a Belkin Components.
lsusb shows net8192su installed.
 
I'm a bit obsessive, and this is taking away lots of time that i should be studying and doing school work (college), but i can't let it go until it's fixed. Dag-nab it!

---

### Post by anewguy on 2010-11-25
Okay, I've looked at that thread.  I don't know if you have the same version of the adapter as the writer there had - the same "named" adapter can have more than 1 version, and each version can have it's own chip type.  Your driver file is completely different that you are trying to use with ndiswrapper, so if you want to try what the link says:

- do the following in a terminal window:

sudo ndiswrapper -e net8192su <press enter>

sudo ndiswrapper -l <press enter) Lower case "L" for "List".
This should now return nothing.

- change your modules file to:

lp
rtl8187

do NOT include ndiswrapper here as we want to not use it at this time to match the other thread


- change your 70-persistent-net.rules line:

# USB device 0x050d:0x705e (rtl8187) SUBSYSTEM==”net”, ACTION==”add”, DRIVERS==”?*”, ATTR{address}==”00:1c:df:37:c2:7d”, ATTR{type}==”1&#8243;, KERNEL==”wlan*”, NAME=”wlan0&#8243;

and put the MAC of your ADAPTER, not the ROUTER in the ATTR(address) information.


- make sure your /etc/network/interfaces file matches what is mentioned in the thread, and with no mention of wlan0:

auto lo 

iface lo inet loopback 


Now, for some reason your 10.10 network manager icon doesn't match mine, but none the less, "Enable Wireless" *IS* what we are looking for - if it's not there it means the system does not know of any working wireless devices.

At any rate, leaving your adapter plugged in of course, now is the time to reboot.

After the reboot is done, right-click network manager again and see if "Enable Wireless" is there - if not, post back.

If it is there, be sure it is enabled.

At this point, I would "Edit Network Connections" in network manager and delete any know definitions of your network so we are starting from scratch there.

Of course, wouldn't want you encryption key posted here or in an email - it doesn't matter to me as long as you match it.

If this doesn't work, then I would suspect you actually need a different driver than the one mentioned in the link.  If so, we'll have some work to do.

Dave ;)

---

### Post by anewguy on 2010-11-25
I just did some web searching based on the USB manufacturer and product it listed for your device (the "050d:945a").  This comes back as the F7D1101 and this is not the same as the device used in the link you provided.

I suspect following that link will not work, but we'll find out as soon as you complete my previous post.

I think we will need to use ndiswrapper and ndisgtk, but we need to reset some things first.

Post back after you try my above post, which should match you to the link you provided.

Dave ;)

---

### Post by zipteye on 2010-11-25
[SIZE=3]Hey, I got it working for that model!

I wiped the drive partition and reinstalled ubuntu from the live disk.
Reboot
Re inserted the Ubuntu disk after login.
Found the ndiswrapper and ndisgtk files, then double clicked them to install them.
Ejected disk.
Reboot.

Inserted the Belkin Drivers disk, and I used the the WINXP2K folder drivers. Although I'm not sure it matters as the .inf file is named the same as the Win 7 one.

Made a temporary folder on my desktop (driver) and copied the .inf and .sys files to it.
Opened terminal
cd to Desktop/driver
ndiswrapper -i  [the .inf file]

Edited /etc/modules to:
lp
ndiswrapper
rtl8189

I left    /etc/udev/rules.d/70-persistent-net.rules   alone.
Did not add any entry about wlan*

[/SIZE][SIZE=3]Ejected Belkin disk

[/SIZE][SIZE=3] Reboot

Works!

Phew...


[/SIZE]

---

### Post by anewguy on 2010-11-26
Glad you could reinstall - that actually makes things the easiest to work with.  It also helps that the rules weren't touched - smart move not to do anything there at all.  The driver file name didn't matter - it's the XP driver that is what ndiswrapper works with.

Glad you got it working!!

dave ;)

EDIT:  For future reference, and for anyone else reading this looking at a similar problem, for the following you did in command line:

```
Opened terminal
cd to Desktop/driver
ndiswrapper -i [the .inf file]

Edited /etc/modules to:
lp
ndiswrapper
rtl8189

```

you could have done just doing the "new" in ndisgtk (System/Administration/Windows Wireless drivers).  As the GUI'd front-end to ndiswrapper, ndisgtk takes away all of the extra typing and editing of other files.  In other words, it makes it simpler and quite a bit more fool proof.  One incorrectly typed character in ndiswrapper and it will look like it worked when it didn't, and the novice can spend hours trying to figure out why.  If you intend to use the command line anyway, then there is no need to install ndisgtk.

- ndiswrapper common and utilities:  allows using Windows XP wireless drivers in Linux

- ndisgtk:  the graphical front-end to ndiswrapper that saves what can be a lot of typing

Another thing you should note:

- adding modules to the /etc/modules tells Ubuntu what NATIVE kernel modules to load.  If you are using ndiswrapper, the module name you supplied to ndiswrapper is a WINDOWS NATIVE module, not Ubuntu.  You do not put those names in modules - that's what ndiswrapper is for.  Soooooooo........based on what you have done - asked ndiswrapper to load a Windows module for your wireless, and then asked Ubuntu to load a native kernel module apparently for your wireless (rtl8189), you aren't really sure which is actually working for you.  The easiest way to fix this is to re-edit the modules file and remove the rtl8189 and reboot.  If your wireless still works then leave things alone.  However, if your wireless doesn't work after the reboot:
[list][*]add the rtl8189 back in the modules file and remove ndiswrapper from the file 
[*]Via System/Administration/Windows Wireless Drivers, remove the existing device (if it doesn't show there use command line ndiswrapper - post back if you need instructions)
[*]Reboot[/list]
If your wireless works now it means it is working off the native rtl8189 driver and you don't need to use ndiswrapper.

Dave

---

