---
title: "Wireless D-LINK DWA 130 Problems"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by CRISM on 2008-05-29
Below, I give a few details on the present state of my wireless woes. But my main question today is this: Has anyone been successful in getting the DWA-130 dongle to work with the 32-bit version of 8.04 (Hardy). If so, I will continue reading posts and trying solutions. But right now, it appears that ndiswrapper and my version of the drivers are locking up my system. I'd like to know there is hope before spending a lot of time on this.

Current status: 
I successfully installed ndiswrapper using Synaptic Package Manager, and then used the .inf and .sys files from my DWA-130 driver CD to install the drivers. I followed instructions found in the forums for accomplishing these tasks, and blacklisted the b43 and b43legacy drivers as instructed. When I enter the command: ndiswrapper -l in a terminal, it reports that the netmw245 driver is loaded and that device 07D1:3B11 is present. This is the correct code for my DWA-130 device...so far so good.

But at this point, the system "freezes". While a few things still work, for the most part I can't start programs or other terminal windows. And if I try iwlist scan, even more things stop working. I try Cntrl-Alt-Backspace to restart the desktop, but even that doesn't go to completion and I have to Cnrtl-Alt-Del to do a complete re-boot.

---

### Post by gyzer on 2008-05-29
I've got a DWA-130 installed in hardy and it works flawlessly. I didn't set it up via the command line version of ndiswrapper, but rather the gui front end, ndisgtk,  for ndiswrapper in hardy. I just loaded up the .inf file and it worked perfectly.
 
Are you using the .sys and .inf files off the driver cd for the DWA-130?

---

### Post by CRISM on 2008-06-01
Yes, I'm using the driver CD for those files and they seem to load in OK. I'll try using the ndisgtk for set up and see if it makes any difference. Thanks for the reply. At least I know it works for somebody!

---

### Post by krash182 on 2009-03-04
I am having the same problem  as soon as I attempt to enable my wireless My modem light flashes and then my computer totally locks up.  the only way to get back is to unplug my stick and shut down by pulling the plug on the computer.  Real good way to mess up my hardware and os.  I installed the drivers using the Windows Wireless Drivers in Start/System/Administration/Windows Wireless Drivers and by installing the drivers with wine. into the C:/Windows/USB Devices  listed in another forum. I am running Ubuntu 8.04 on a 32 bit HP and the DWA-130 1a Drivers from the D-link web site.

---

### Post by krash182 on 2009-03-04
additional information,  If I restart with my d-link stick still plugged in, I can not reboot. it will not start.

---

### Post by krash182 on 2009-03-04
update success,  removed drivers from supported system, reinstalled with beta drivers on d-link website.  set up wireless as listed in other forums then removed stick rebooted then when stick reinstalled in base with the rebooted window, connection was made.  must still remove stick when I need to shut down and keep it out until it has booted but I can now get wireless access.

---

### Post by krash182 on 2009-03-04
had it connected so updated system, lost everything and now back to square one.  lock ups and all.  beta drivers not working this time. oops

---

### Post by tanha on 2009-04-28
> **gyzer said:**
> I've got a DWA-130 installed in hardy and it works flawlessly. I didn't set it up via the command line version of ndiswrapper, but rather the gui front end, ndisgtk,  for ndiswrapper in hardy. I just loaded up the .inf file and it worked perfectly.
 
Are you using the .sys and .inf files off the driver cd for the DWA-130?

Are you using x86 or x86_64? Are you using it in 802.11g or 802.11n mode?

---

