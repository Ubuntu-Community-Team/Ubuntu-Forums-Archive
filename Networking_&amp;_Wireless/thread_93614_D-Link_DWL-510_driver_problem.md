---
title: "D-Link DWL-510 driver problem"
date: 2005-11-22
forum: Networking &amp; Wireless
---

### Post by crypticstatic on 2005-11-22
Hello all,

I have an older micron computer (p3 I beleive) and I just recently installed the D-link 510 (rev.b) wireless card into the system with a fresh install of ubuntu 5.10 and for the life of me I cannot get the wireless card working!

I followed all of the instruction for ndiswrapper and everything seems to go smoothly excpet that after i install the driver that came with the cd and run "ndiswrapper -l" it shows the driver is installed and hardware present. Although when I run "iwconfig" (sp?) it doesnt show any sign of a wireless card being installed.

So then I proceed to try and use the gui tool where the card is still NOT being detected, so then I continue to follow the ndiswrapper instructions and add the module to "/etc/modules" then reboot the system. 

This is where the biggest problem occurs, during the boot it actually detects the wireless card but then hangs up completely right after, it just stop right in the middle of the boot process.

I'd like to know,
1) what could i possibly be doing wrong and how to fix it

2) Is there a way to get back into the system to edit the /etc/modules file so that I wont have to completely reinstall ubuntu again?

3) is there another driver I should try for this card?

P.S. This particular card is known to be supported by ubuntu, I checked in advance :)

Thanks....

---

### Post by Lambert on 2005-11-22
> 2) Is there a way to get back into the system to edit the /etc/modules file so that I wont have to completely reinstall ubuntu again?

Get a livecd and boot into that. Then mount your harddrive and navigate to the file. You can open and modify it that way.

When you installed the drivers, did you do it from the cd or did you copy the driver on to your harddisk in a directory and do it from there?

It sounds like ndiswrapper is recognizing there was a driver installed and saying it's present but when the os actually calls on the device, there is no driver there to communicate with.

I would suggest to remove the driver. Copy the driver plus any other files that are in the driver folder on the disk. .sys .dll .inf etc... to a directory on your harddrive.
Then start over and reinstall the driver using the folder you copied to on the drive.

If you're not seeing anything when you run iwconfig then the driver isn't working properly. Maybe look into the vendors page to see if there is  another driver you can try.

I do show there is a realtek driver but not sure what's involed in getting it installed.

802.11b 	DWL-510 		PCI 	Realtek 	rtl8180 	green 	[http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/)


Card: D-Link DWL-510 
Chipset: Realtek RTL8180L 
pciid: 1186:3300 
Driver: Driver for RTL8180L from [http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180](http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180) 
Other: D-Link-provided drivers give huge system lags, system stops responding for full seconds at a time. The Realtek driver works well, but to make the driver recognize the card you must manually edit the file NET8180.INF and change all references to the pci-id 10ec:8180 into 1186:3300. Note that you much change 8180 to 3300 only when it appears near or next to 10ec, and leave it otherwise. See [http://www.xs4all.nl/~bsamwel/dwl-510-on-linux-2.6.html](http://www.xs4all.nl/~bsamwel/dwl-510-on-linux-2.6.html). 
Comment: 
There is not allways a true! I use D-Link drivers, and they works fine for me, better than Realtek drivers, [http://213.216.192.242/techdocs/V5.162.1030.2003.zip](http://213.216.192.242/techdocs/V5.162.1030.2003.zip) see [http://rtl8180.prv.pl](http://rtl8180.prv.pl)

---

### Post by crypticstatic on 2005-11-22
Just a quick update on this issue which I have now resolved.

After trying two different drivers and beating myself over the head trying to configure this card to my system I decided to go out and purchase a Linksys WMP54GS Wireless NIC and give that a try.

Well, after installing the card and running "ndiswrapper" as instructed it worked flawlesly! Thank goodness....  So I guess the d-link card just wasnt compatible with my system.....

Hope this info can help everyonne else in the future!

---

