---
title: "Network-Manager killing University wifi connection"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by VMan on 2008-03-08
So this is a weird problem.  I discovered that Network-manager is the problem.  I was playing with a live CD and noticed that it allowed me to connect to the University's wifi network.  With an updated installation on a HD, the computer would not connect to the network:confused:

Solution:  I had an extra HD laying around (upgraded the computer recently); I installed 7.10 (64bit) to the hard drive.  I had wifi network connectivity.  :)
I then upgraded all available packages.  No network connectivity](*,)
I then reinstalled (completely wiped and formatted HD) again.  This time during the updates, I refused to let network-manager update.  =;  I now have an updated system (well almost completely updated) with working wifi:KS  

My big question is:  I did all of this with a spare HD.  I would like to remove the problematic network-manager package from the installation I really use (my big super duper HD) and replace it with the version that is initially installed.  Where can I get that package?  How can I "extract" it from an installation CD if there is no where to download it?

---

### Post by gilf on 2008-03-09
Well, I'll take a stab at it.

I was able to install ndiswrapper directly from the LiveCD by simply selecting it in the Synaptic Package manager (after I'd turned off networking -- otherwise it would have searched the internet for upgrades, and I wanted to load off the CD).

So, if Network Manager is also available on the UBuntu CD you should be able to both uninstall the old version, and reinstall a fresh version via Synaptic -- as long as the liveCD is in the drive. Of course you are NOT in a liveCD session when you do this -- but working from your installed system.

To test out whether this works. boot from your external HD first and try to uninstall, then reinstall it there using the method above. If you can do that with Synaptic and a LiveCD in the drive successfully, then you can feel confidant doing it on your main HD.

Looks like the apps related to NM are:

network-manager
network-manager-gnome
libnm-glib0
libnm-util0

Hope this helps.

---

### Post by kevdog on 2008-03-09
Sorry to chime in here b/c slightly off topic -- or you could dump NWM altogether and go for WICD.  Very well supported here in the forums and seems to solve many flaky NWM issues.

NWM -- a updated version is slated to be released with Hardy.  It might possibly be better, however for now I'm left standing recommending either WICD or a manual connection through the command line or put in the rc.local file.

---

