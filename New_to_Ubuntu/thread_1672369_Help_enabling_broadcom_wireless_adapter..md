---
title: "Help enabling broadcom wireless adapter."
date: 2011-01-20
forum: New to Ubuntu
---

### Post by skaldicpoet9 on 2011-01-20
Hey everyone, I just got a Compaq Presario that has the Broadcom 4318 wireless adapter. I have had the same problem in the past trying to enable this driver but am unable to get it activated using the previous methods I had used. 

I tried installing Ndiswrapper but couldn't find the bcm43xx inf file to load so I uninstalled that and activated the restricted broadcom driver found in System/Administration/Restricted Drivers but when I restart the computer there is still no wireless networks interface. What is the best way to get this driver activated?

---

### Post by skaldicpoet9 on 2011-01-20
I just tried this old fix that someone referred me to when I was encountering problems before: [http://ubuntuforums.org/showthread.php?t=507505&highlight=Gateway+mx3215](http://ubuntuforums.org/showthread.php?t=507505&highlight=Gateway+mx3215) but that didn't work either. Man, is it me or is Broadcom really prevalent in laptops? Just about every time I have installed Linux on any laptop I have had, I always get this problem. Anyways, if anyone can point me in the right direction I would be much obliged.

---

### Post by klossor on 2011-01-20
I've had similar problems with broadcom pieces, and to be honest I'm just not bothered with the repeated hassles that come with them. I'm sure it's a problem that can be solved, my route was a £15 mini wifi dongle (edimax in this case) with an atheros chipset, problem solved ;)

---

### Post by Bucky Ball on 2011-01-20
You should have no issue with these cards now. Plug in an ethernet cable and get online. Get updates (you are probably missing the firmware). Then System>Administration>Additional Drivers. Enable the Broadcom driver. 

These cards install in a few clicks nowadays (generally). AVOID ndiswrapper unless it is the absolute last resort.

---

### Post by skaldicpoet9 on 2011-01-20
I did enable the Broadcom driver from System>Administration>Additional Drivers but when I restarted my computer the driver is no longer listed in the Additional Drives dialogue and the dialogue states that I have no proprietary drivers installed. 

What happened to it? I checked the Synaptic Package Manager and I have firmware-b43-installer and b43-fwcutter checked, as well as bcmwl-kernel-source too. I don't know what happened, I just rebooted the computer after activating the b43 driver and after boot it isn't even listed anymore.

---

### Post by wep940 on 2011-01-20
As already noted, ndiswrapper and it's GUI'd front-end ndisgtk can be used successfully with these adapters, however it should only be used as a last resort now.  Not because ndiswrapper/ndisgtk have anything wrong with them, but rather that there are now native and restricted drivers for most of these adapters.
 
As mentioned, connect your PC directly to your router with a hard-wire connection.  Then:
[LIST]
[*]in a terminal window type "sudo apt-get update <press enter> and wait for this to finish
[*]go to System/Administration/Additional Drivers and look for one for Broadcom.  Be sure to enable it.  Some of this make take a little time as some downloads from the net are probable.
[*]physically disconnect the hard-wire cable to your router
[*]right-click  on the network manager icon and be sure "Enable Wireless" is enabled.
[*]left-click on the network manager icon and look for wireless networks
[*]if your router does not broadcast the network name (SSID) you must left-click on the network manager icon and select "Connect To Hidden Network".
[*]if encryption is enabled on the router, you must match the type and the password/passphrase
[/LIST]

---

### Post by skaldicpoet9 on 2011-01-20
When I go to System/Administration/Additional Drivers the Broadcom driver is no longer listed, that is what I was asking in my previous post, the listing has disappeared after I tried activating it. I rebooted the computer after clicking to activate the Broadcom driver and the next time I looked in System/Administration/Additional Drivers the listing for the driver was no longer there. I don't know if I messed something up somehow by trying the various Broadcom "fixes" that I was using.

---

### Post by Bucky Ball on 2011-01-20
I would suggest uninstalling everything ndiswrapper if you have it installed and trying again. ndiswrapper can interfere with the correct config of the new Broadcom drivers.

---

### Post by skaldicpoet9 on 2011-01-20
I have already completely uninstalled the ndiswrapper files, I just checked in the synaptic manager. The only other thing I installed was the compat wireless drivers but I did a make uninstall on those and deleted the folder after they failed to correct the problem.

---

### Post by skaldicpoet9 on 2011-01-21
I ended up reinstalling Ubuntu because I couldn't for the life of me figure out how to get the Broadcom driver listing back in the restricted drivers list. After I reinstalled, the Broadcom driver was listed once again and it was simply a matter of configuring my wifi connection. Thanks for the help everyone. :D

---

### Post by wep940 on 2011-02-07
Just FYI - if you followed instructions for ndiswrapper, or you ran ndisgtk, the other drivers were blacklisted.  So, when you just deleted ndiswrapper it didn't revert the blacklist file to the old state, so the drivers you wanted were still blacklisted.

---

