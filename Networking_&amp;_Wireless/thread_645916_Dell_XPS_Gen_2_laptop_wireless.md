---
title: "Dell XPS Gen 2 laptop wireless"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by rushtone on 2007-12-20
Hi.  I'm trying to get wireless networking going on this Dell XPS Gen 2 laptop with Gutsy installed.

david@moran:~$ lspci | grep -i network
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)

Word is that this card uses the ipw2200 driver:

david@moran:~$ dmesg | grep ipw2200
[   12.932000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   12.932000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   13.008000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   13.420000] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
[   31.568000] ipw2200: Failed to send ASSOCIATE: Already sending a command.
[   54.892000] ipw2200: Firmware error detected.  Restarting.

So that's there, but looks like it may have a problem.

Under System > Administration > Network, when "Enable roaming mode" is checked, everything in the window is just grayed out.  Can't figure out how to have it scan for available networks (there's an AP in the same room).

WiFi LED is not lit, and Fn+F2 doesn't change that.

What now?

David

---

### Post by dgcaste on 2008-05-29
this is an older post but it looks like you haven't found a resolution. I recommend you reinstall/refresh the ieee80211 libraries (with care to COMPLETELY remove the old ones, the INSTALL file in them has some good scripts that do this) and recompiling the ipw2200 module, and downloading the most recent firmware.

[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

I have an inspiron 9300 modded with an xps gen 2 BIOS for the 7800gtx, which works great in ubuntu with the glx driver :-D

---

### Post by cjsimon on 2008-05-30
I have a new Dell XPS M1330 laptop puchased in February of 2008, factory preloaded with Ubuntu 7.10. The computer bios that dates back to February of 2008 created ongoing wireless connectivity failures. The machine could connect to an encryted wireless network for a unpredictable amount of time and then would simple loose the connection and this disconnect could not be resolved unless the mchine was restarted and and restarted as an admin. The  XPS top panel WiFi light would just quickly blink and not reconnect.

I tried the nsdiswrapper and this turned out to cause more problems than fix, because Dell fine tunes the wireless driver to work out of the box and the ndiswrapper is designed as a work around for wireless devices that have no native driver predefined (for Linux). With a factory install of Ubuntu the drivers installed are tested and designed to work and emulation work-arounds like ndiswrapper that tap into using ms windows drivers in not a good idea in terms of predictable solution.

The fix was for Dell and turned out to simply be a machine bios upgrade. My Dell support tech helped find the right bios update on this page [http://linux.dell.com/repo/software/bios-hdrs/](http://linux.dell.com/repo/software/bios-hdrs/) and after the bios update the wireless disconnect problem was eradicated. Now wireless sessions stay active without failure.

So all is good with Ubuntu on My Dell XPS latop. One last note.... you have to make sure the wireless roaming (nm-applet seeting) is always left on to get predictable results with a configuration like mine.

---

### Post by bodselecta on 2008-06-22
cjsimon, what dell bios were you upgrading from?
I have the A08 version on a fairly decent spec xps 1530m and it looks like I have the latest. 
When I called dell tech they didn't seem that helpful, and told me to install the windows 1530_A08.exe to flash the bios, even though I already have that version.
I kept on asking whether that download was a newer version (maybe a minor version upgrade) but they didn't know and offered to transfer me to a support that I'd have to pay for!

My first week of owning the laptop the problem wasn't too severe, probably needing 1-3 reboots to get the card recognized.
This second week seems worse. The last 2 days I've needed to reboot maybe 7 or (though I'd have to do this from windows).
I'm worried that this will continue as it's the only thing that would stop me from using ubuntu.
 
:(

---

### Post by cjsimon on 2008-06-25
My Dell XPS 1330 with Ubuntu 7.10 factory installed was purchased in February of 2008 and its Bios would be from that time frame. The update was from May of 2008. This Bios update really fixed all of my wireless problems on this laptop. Funny thing is... Dell had a Canadian Linux support team in May... and by June it looks like they closed this support team down and off-shored the support to another country. That's sad because those Canadian Linux Dell support technicians were the sharpest support staff I've ever ecountered and the new off-shored team are a bunch of newbies.

This wireless configuration is issue is critical and seems to be keeping people from moving to Ubuntu. Just talked to a friend today who was struggling with the nsdiswrapper wireless driver stuff and was having no luck... of course he wasn't dedicating much time to the problem either.

---

### Post by cjsimon on 2008-06-27
Update from my last reply now that I updated to Ubuntu 8.04. Everything was running great with my May bios update from Dell on my Dell XPS M1330 laptop and then after a few recommended Ubunutu updates my wireless card was no longer detected at all. After attempting to get Dell to assist me - which they could not (since the Canadian support team is gone), and after Cononical would not return my email request for annual fee based support I just proceeded with the Ubuntu 8.04 update from 7.10. After this update my wireless configuration starting working at the first restart after the OS update.

---

