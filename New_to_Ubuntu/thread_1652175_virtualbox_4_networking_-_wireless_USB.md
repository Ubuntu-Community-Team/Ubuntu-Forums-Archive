---
title: "virtualbox 4 networking - wireless USB"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by wep940 on 2010-12-24
I just installed VirtualBox 4 - indeed things are a little different now - 1 download of VirtualBox itself, 1 download to ADD USB support.  Apparently no more PUEL versus OPEN source downloads.  I should add that I installed VirtualBox in Windows so I can try out several Linux distributions without blowing away a previous one.
 
I am confused though - I added a generic filter and a filter specifically for my USB wireless adapter (it is working in Windows itself), but I can't figure out how to get VirtualBox networking set up to use it.
 
The default, using NAT, does not reference my wireless, and also says "cable connected".  This results in ZoneAlarm showing the traffic but it never gets to my wireless interface.  I changed it to bridged - not really sure what the different options mean - selected my wireless adapter, and it doesn't even get to ZoneAlarm, as if no traffic is being detected at all.
 
So, I would appreciate any help anyone might be able to give me on this.  I looked at the brief help that comes with VirtualBox but it doesn't help me, and with no net connection I can't get to what I would assume would be the more detailed info in the online help.
 
Thank you for your help.

---

### Post by wep940 on 2010-12-29
This thread was sidetracked from my original question.
 
bump - my original question about getting USB wireless networking, Windows host, working with Linux guest. Linux guest shows the device but it never gets traffic. if I let default to NAT and the device it shows there (not mine) and with all of the defaults (like cable connected), traffic goes to in and out of ZoneAlarm (yes, I allowed the traffic, no I didn't do anything special if I was supposed to) but the traffic never gets to the USB wireless adapter.
 
EDIT:  Re-installed VirtualBox - noticed in the outline of what it was installing only bridged and vbox host showed as being installed under networking.  I also read online to set Zonealarm internet security level to medium.  Makes no difference.  Even shutdown Zonealarm and made no difference.
 
If only bridged and host are installed, I assume that even though it comes up by default with NAT that it might not work?  I know nothing about any of this or how to make it work.

---

### Post by wep940 on 2010-12-29
It just started working - I have no idea why.

---

### Post by wep940 on 2010-12-29
For some reason, after starting the VM, I have to do a "repair" on the Windows host wireless connection, then everything works.
 
I have to do this everytime.

---

