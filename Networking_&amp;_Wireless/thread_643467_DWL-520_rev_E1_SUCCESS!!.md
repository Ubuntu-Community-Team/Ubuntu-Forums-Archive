---
title: "DWL-520 rev E1 SUCCESS!!"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by hwertz on 2007-12-17
I undertook upgrading my parent's computer to Ubuntu 7.10.  So, everything worked right off the bat other than the infamous DWL-520 rev E1.  

     hostap_pci gives the well-known errors about no PRI f/w and so on.

     ndiswrapper seemed to just mysteriously not work -- it indicated a succesfull load, but no eth or wlan device showed up.

     So I read considerable posts about using prism2_srec, tried it out, and it didn't work.  I'd get various variants of NICID showing as 0x8000, PDA  read failures, and a few others.  I seemed in short to get nearly every possible firmware-related error that hostap can possibly produce.

     HERE"S THE "SECRET":  something (I'm assuming network-manager) kicks the card enough that playing around with prism2_srec from a terminal just gives virtually every error message hostap can produce.. it saids the NICID is 0x8000, can't read PDA, MAC 0 enable failure, etc. etc.  Trying out prism2_srec from FAILSAFE mode, on the other hand, worked great. :popcorn:

     So.. step-by-step.  Note you WILL need a network connection to get this going, so unfortunately you'll need an ethernet cable or borrow (in my case) temporarily plug in a spare USB wireless dongle (in my case, a zd1211, which worked right off the bat... I just decided not to use it permanently due to desk clutter and lack of USB ports.)

     1. Get Latest-prism.tar.bz2 or if you prefer the individual firmwares (pm010102.hex and rf010804.hex).  I don't remember exactly where I got these, google is your friend :) (or, just look through older ubuntuforums posts.)

     2. install hostap-utils.  You need prism2_srec

     3.  I extracted Latest-prism into /lib/firmware/Latest-prism.  I assume if I put them under /lib/firmware/2.6.22-etc with the other firmwares that they'll be removed next time I upgrade the kernel, so I didn't put them there.

     4.  I put the following into /etc/rc.local:

```
/usr/sbin/prism2_srec -gs wlan0 /lib/firmware/Latest-prism/primary-RAM/pm010102.hex
/usr/sbin/prism2_srec -gp wlan0 /lib/firmware/Latest-prism/primary-RAM/pm010102.hex
/usr/sbin/prism2_srec -rp wlan0 /lib/firmware/Latest-prism/secondary-RAM/rf010804.hex
```

     Based on reading far too many old hostap and ubuntu threads, the theory of operation is that the "-gs" line loads the primary firmware.  But, in a chicken and the egg type situation, without primary firmware, prism2_srec cannot retrieve some important info like the network card address and some other info so it's set to all 00s.  The -gp line loads the primary firmware AGAIN, but it can retrieve the network card address etc. and patch it into the firmware.  The -rp line loads the secondary firmware, at which point the card is fully operational.

     I suppose there could be a race condition -- if the network-manager (or whatever bothers the card) starts up before prism2_srec's complete, I imagine it'd end up failing with the various NICID, PDA, etc. errors I got trying to do it from a terminal.  I ran this on a Duron 1100 with 384MB of RAM.  I would assume a race condition would show up on a very fast system (particularly one with a fast hard disk) rather than on a lower end system -- if it was network-manager causing the problem,  the machine would have to load up X and the whole desktop in the second or so it takes the prism2_srecs to run.

     Rock on! :guitar:

---

### Post by josephdaniel on 2007-12-23
Thankssssssss a lot. You can't imagine how long I have been struggling with this card. I tried every single solution posted anywhere on the internet but none worked. I had already extended a cable to use wired lan instead of wireless. I lost hope it would ever work. I have been trying with this card since ubuntu 5.04. 

Thank you very much once more.

---

### Post by hwertz on 2007-12-23
No problem!  I really don't like having to buy new hardware if I don't have to :) and I was glad I got it to work... 

[COLOR="Sienna"]**Edit: disregard the below, the manual network setup only worked like 1 out of 5 times or so.  I think the time between loading the firmware and trying to fire up the card is too short.  I didn't want to go back to NetworkManager's insisting on passwords, and skipped trying WICD since I already had a RTL8180-based USB stick lying about.  I pulled the PCI card and plugged in the stick.  To avoid clutter I just stuck it behind the monitor where it's out of the way.**[/COLOR]

As a followup, I ended up setting this machine's network-manager to "manual", put in my wireless network and WEP key, and set it to DHCP, so I could get autologin working... Otherwise, it'd skip the login & password, but ask for the keyring password like 3 seconds later :) .  (This isn't specific to this card, apparently network-manager just can't handle automatic network management with WEP, WPA, etc. without being given a password at some point.)

     network-manager simply writes this manual info into /etc/network/interfaces and it's handled at system startup.

     This, however, didn't work, because the /etc/network/interfaces stuff is done before rc.local is run.  dhcp runs before the card is setup, so it then  asks for an IP address for card "00:00:00:00:00:00" instead of the right network card address.  It turns out /etc/network/if-pre-up.d/hostap-utils actually does exactly what I put in rc.local (with a few extra sanity checks) once it's told where the firmware is.

     So, with things set to manual, I put in /etc/network/interfaces (in the section describing wlan0):
```

primary_fw /lib/firmware/Latest-prism/primary-RAM/pm010102.hex
secondary_fw /lib/firmware/Latest-primary/secondary-RAM/rf010804.hex

```

     I commented out the lines in rc.local; I don't know if I would have had to or not for sure.
     I assume if I set network-manager back to automatic, it'd probably clean out /etc/network/interfaces and I'd probably have to uncomment the lines in rc.local again.

     Rock on! :guitar:

---

### Post by lunchtimemama on 2007-12-28
Spectacular. Thank you very much.

---

### Post by jwkolberg on 2008-06-18
:)THANKS! works great! I've been struggling with this for months! 

DONT FORGET TO REBOOT, I thought for a second it didn't work, but just needed to reboot.

---

