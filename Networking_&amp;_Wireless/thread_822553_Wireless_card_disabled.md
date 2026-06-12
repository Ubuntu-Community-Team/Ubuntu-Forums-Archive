---
title: "Wireless card disabled?"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by Spunkbubble on 2008-06-08
Hi, I'm new to the whole linux experience, but looks really good. I have a higher spec PC running Vista (yeah rubbish I know) and Ubuntu 7.10 on another older PC.

Anyway, I have a Belkin 802.11g 54mbps network card, and am trying to use it to set up an internet connection, which will be vital for me if I'll be sticking with Ubuntu. I've done some checks, spent hours browsing tutorials and the like, and I think I've narrowed down the problem.

The system recognises the card, apparently the drivers are fine, I've tweaked my wireless settings for manual connection, but when I look at the information for the card, it's listed as disabled. I haven't done anything as far as I know to disable it, so is this a default setting? From what I gather it's hard if not impossible to enable it... or is this just talk? If there's a way to enable it, then I'm all ears since I think that's the problem, but bear in mind I'm a total noob, so keep it simple if possible please!

Also, I've tried installing Ndiswrapper. I downloaded it on my Vista, transferred it via USB memory stick, decompressed, extracted 'bcmwl5.inf', put it in my documents folder. The instructions on the website said to run "make distclean" but when I do, I get this:

```
make -C driver clean
make[1]: Entering directory '/home/myname/Desktop/ndiswrapper-1.53/driver'
rm -f *.o *.ko .*.cmd *.mod.c *.symvers modules.order *~ .\#*
rm -f *_exports.h win2lin_stubs.h
rm -rf .tmp_versions
make[1]: Leaving directory '/home/myname/Desktop/ndiswrapper-1.53/driver'
make -C utils clean
make[1]: Entering directory '/home/myname/Desktop/ndiswrapper-1.53/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory '/home/myname/Desktop/ndiswrapper-1.53/utils'
rm -f *~
rm -fr ndiswrapper-1.53 ndiswrapper-1.53.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory '/home/myname/Desktop/ndiswrapper-1.53/driver'
[COLOR="Red"]make[1]: *** No rule to make target 'distclean'. Stop.
make[1]: Leaving directory '/home/myname/Desktop/ndiswrapper-1.53/driver'
make: *** [distclean] Error 2[/COLOR]
```

No rule to make target 'distclean'? What have I done wrong here?
By the way since I don't have internet access on the other PC this is manually written, there may be typo's.

Thanks in advance for any help.

---

### Post by Spunkbubble on 2008-06-08
bump

---

### Post by Spunkbubble on 2008-06-08
bump

---

### Post by Spunkbubble on 2008-06-08
bumpety-bump

---

### Post by chili555 on 2008-06-08
> From what I gather it's hard if not impossible to enable it... or is this just talk?Quite untrue. There are at least three proven ways and you have started the hardest! Since you are started down the ndiswrapper route, let's see if we can salvage that.

Please open up System -> Administration -> Synaptic and go to Settings -> Repositories and drop the install CD in the tray and enable the CD as an installation source. Press Reload. Search Synaptic for 'ndis' and install ndiswrapper-common and ndiswrapper-utils.

Now proceed with any number of the 129,000 tutorials on how to ndiswrapper your Broadcom card.

Post back if you get stuck.

---

### Post by Spunkbubble on 2008-06-09
> **chili555 said:**
> Please open up System -> Administration -> Synaptic and go to Settings -> Repositories and drop the install CD in the tray and enable the CD as an installation source. Press Reload. Search Synaptic for 'ndis' and install ndiswrapper-common and ndiswrapper-utils.

Which CD is this? I transferred Ndiswrapper via USB key. The Belkin installation CD gives an error message saying: "E:Unable to locate any package files, perhaps this is not a Debian Disc". If you mean my original installation disc, that has been long since written over, although I could write a new one...

---

### Post by chili555 on 2008-06-09
> If you mean my original installation disc, that has been long since written over, although I could write a new one... That's the one I mean. It has many packages you might need on it. Please burn it to a CDR and mark it with a Sharpie: KEEP!

---

### Post by Spunkbubble on 2008-06-09
Ok thanks, will do :)

EDIT: By the way, do you (or does anyone) know a reliable source for 7.10? I could only come up with results for later versions on google.

---

### Post by chili555 on 2008-06-09
Right here: [http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)

Another way, if you feel it's easier, is to go here: [http://packages.ubuntu.com/search?keywords=ndis&searchon=names&suite=gutsy&section=all](http://packages.ubuntu.com/search?keywords=ndis&searchon=names&suite=gutsy&section=all) and download the .deb files I mentioned. If you have to use another machine to download them, transfer them to your Ubuntu machine. Install with:```
sudo dpkg -i <ndis-utils.etc.deb ndis-common.etc.deb
```Substitute the correct names here.

Once you have them installed, you can follow this: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Spunkbubble on 2008-06-10
Hmm now InfraRecorder is playing up... After I start burning I get the messages:

Cannot get next writable address for 'invisible' track.
This means we are checking recorded media.
This media cannot be written in streaming mode anymore.
If you would like to write to 'preformatted' RW media, try to blank the media first.
Started to write the disc in real write mode.
Input/Output error, read track info: scsi sendcmd: no error
Cannot get next writable address for 'invisible' track.
This means we are checking recorded media.
This media cannot be written in streaming mode anymore.
If you would like to write to 'preformatted' RW media, try to blank the media first.
Input/Output error, write_g1: scsi sendcmd: no error
Started to write track 1.
Input/Output error, write_g1: scsi sendcmd: no errorcdb: 2A 00 00 00 00 00 00 00 1F 00status: 0

The second link shows up as invalid when I follow it. Someone up there really doesn't want me to get internet access. Any suggestions?

---

### Post by chili555 on 2008-06-10
> Any suggestions? Yes. First the second link worked for me just now. Maybe the site was down for maintenance or otherwise when you tried. Please try again.

I am not familiar with InfraRecorder. It sounds like you are trying to write to a CDRW and you need to 'blank' or clear the CDRW first, before you write new data to it. Is there a tool to blank a CDRW in there somewhere? Then try the burn again.

---

### Post by james_vanb on 2008-06-10
Recently installed the same card.  Once you have ndiswrapper installed, try Step 3 and on in the following thread:

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=766560&highlight=bcmwl5.inf](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=766560&highlight=bcmwl5.inf)

Worked for me - Hope you have similar success.

---

### Post by Spunkbubble on 2008-06-10
Alright, I've successfully installed Ndiswrapper (I think - at least the ndiswrapper commands are being recognised now). I've followed the tutorial to the point where I need to enter "ndiswrapper -l" to confirm it's worked. However, the results that are supposed to be show are:

bcmwl5: driver installed
device (blah:blah) present

Instead I get the "bcmwl5: driver installed" but not the second part. Does this mean I have the correct drivers installed but it can't find the device?

James - thanks for the link, I've done step 3 and it seemed to work without any errors but I still came up with these results both before and after using it. I'm not really sure whether it's made a difference or not, but thanks :)

---

### Post by james_vanb on 2008-06-10
Driver looks to be installed.

You have to do Step 3 and the rest as follows from the link I gave you:

Step 3 (run in terminal)

sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

Step 4 (run in terminal)

sudo aptitude remove b43-fwcutter

Step 5 (run in terminal)

sudo gedit /etc/init.d/wirelessfix.sh

Step 6

Paste the followings in the opened file(wirelessfix.sh)and make sure you save it before continuing Step 7

#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

Step 7 (run in terminal)

Run this :

cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh

Step 8 (run in terminal)

finally run this:

sudo update-rc.d wirelessfix.sh defaults 

Step 9

Restart your machine and enjoy the freedom from those wires....

If you just did Step 3, continue with the rest.

---

### Post by Spunkbubble on 2008-06-10
Ok, did the remainder of the steps, no errors encountered, restarted, but still so internet, and still the same results when I run ndiswrapper -l.:-?

---

### Post by james_vanb on 2008-06-10
Your ndiswrapper -l is showing the driver installed.  If you have your router set with WEP, WPA, etc. turn the security settings off and see if you can connect.

---

### Post by Spunkbubble on 2008-06-10
Ok, I'll give that a try - but shouldn't I be able to at least see the network anyway?

---

### Post by james_vanb on 2008-06-10
Good point - I just reread your post.  It looks like you are using Gutsy (7.10) and not Hardy (8.40).  My apology.  The instructions I gave you above are for Hardy.  In Gutsy, you don't need to use ndiswrapper.  This card will work if you install b43-fwcutter through Synaptic, then go to System > Restricted Drivers and enable the driver.  You will probably need the Ubuntu install cd to do this as you don't have internet connection.  If this is the route you want to go, first uninstall ndiswrapper through Synaptic.  If you want to use ndiswrapper, process using the install cd for the Belkin is as follows:


Open terminal.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin".
Insert the install cd. Open and navigate to the driver file under XP. Copy all files (.inf and .sys and anything else) to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following :

sudo ndiswrapper -i /home/(your user name)/Belkin/bcmwl5.inf

Insert the wireless adapter.

Now issue the following commands:

sudo depmod -a
sudo modprobe ndiswrapper

These create the module. Now edit modules to load ndiswrapper when you boot as follows:

sudo gedit /etc/modules

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

sudo ndiswrapper -m

Reboot

If no connection, open terminal and type:

ndiswrapper -l

Blacklist whatever is listed as the Alternate as follows:

sudo gedit /etc/modprobe.d/blacklist

Reboot again, if still no connection, run ndiswrapper again and see if another Alternate is listed and blacklist that one.  Repeat as necessary.

You should now have a connection.

When I was using Gutsy, I just used the Restricted Driver, it was much easier.

---

### Post by Spunkbubble on 2008-06-10
Ok I tried using the commands, but they either returned no information, or told me something along the lines of 'you've already done this'. Ndiswrapper was already at the bottom of the aforementioned list. After rebooting, still no internet, and "ndiswrapper -l" still returns only "bcmwl5 : driver installed".

---

### Post by Spunkbubble on 2008-06-10
Update: Attempting the other method proved fruitless as well. b43-fwcutter couldn't be found on the disc nor on my entire system. Attempting to enable the driver wasn't possible, I'm guessing since it relies on b43-fwcutter.

---

### Post by james_vanb on 2008-06-10
Since the bcmwl5 driver is already loaded, you may have to remove it first and then reinstall:

```
sudo ndiswrapper -r bcmwl5
```

You may have to undo some of the Hardy fix I gave you:

```
sudo gedit /etc/init.d/wirelessfix.sh
```

Remove the followings in the opened file(wirelessfix.sh)and make sure you save it. 

#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

Reboot.

Then try the install.

As for b43-fwcutter, you may need an internet connection to download it.  Any chance you can use a wired connection?

---

### Post by Spunkbubble on 2008-06-10
A wired connection's not really a viable option, if it was, I wouldn't be bothering with wireless at all :) I'll try this out now. Is it possible to download fwcutter via Vista and transfer it?

---

### Post by Spunkbubble on 2008-06-10
Alrightey, had another crack at it, and found that attempting it again still gave me the response "module configuration already contains alias directive" from "sudo ndiswrapper -m". Ndiswrapper was already on the end of the list again too. After rebooting, still no luck with the connection.

---

### Post by james_vanb on 2008-06-10
Sorry to say that I don't have a computer with Gutsy on it anymore and can't test solutions for you.  Kind of working from memory.  A quick search found the following including instructions on how to load b43-fwcutter using a flash drive.  I suppose any removable media would work (CD, Floppy, etc.)

[http://forumubuntusoftware.info/viewtopic.php?f=7&t=1047](http://forumubuntusoftware.info/viewtopic.php?f=7&t=1047)

See also:

[http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation](http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation)

---

### Post by james_vanb on 2008-06-10
> **Spunkbubble said:**
> Alrightey, had another crack at it, and found that attempting it again still gave me the response "module configuration already contains alias directive" from "sudo ndiswrapper -m". Ndiswrapper was already on the end of the list again too. After rebooting, still no luck with the connection.

Sorry this isn't working for you.  As a last ditch effort, remove ndiswrapper - edit modules and edit out or remove ndiswrapper from end of list. Reboot and start fresh.

---

### Post by Spunkbubble on 2008-06-10
Ok, thanks. I think that's probably best, but it'll have to be tomorrow... or today? 02:18. Meh. To bed. I appreciate your efforts, hopefully I'll get this done sooner or later.

---

