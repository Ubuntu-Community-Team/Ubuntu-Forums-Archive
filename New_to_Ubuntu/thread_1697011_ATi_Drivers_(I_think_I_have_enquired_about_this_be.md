---
title: "ATi Drivers (I think I have enquired about this before!)"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by Bugsy_malone 666 on 2011-02-28
Ok so I have on an off been running my Ubuntu machine and I seem to have hit a minor snag with the ATi Video Drivers.

My Machine is an AMD Athlon 7750 Dual Core with an ATi HD4650 graphics card.

Now initially I went through and looked at windows propriety drivers and it said look heres some tried and tested ATi ones, do you want to use these, I then installed and that knackered up the displays! So I reset the graphics to use basic default type drivers as the ATi provided ones arent working.

Someone on the previous thread where I broke it mentioned about some sort of manual download and installation of drivers, could someone point out where/how?

The reason I know I need the proper drivers rather than just running my current default is because it wont even handle Extra Visual Effects under the appearance control panel, it goes looking for drivers and says it could not be enabled! Now I have a little Lenovo laptop which has some intel graphics I think and it works fine on that and its not anywhere as near the performance level of the graphics of this PC!

So any guide advice would be much appreciated!

---

### Post by seawolf167 on 2011-02-28
Here you go, [ATI HD 4640 drivers download page]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")

Download the file, then run the .run

---

### Post by Bugsy_malone 666 on 2011-03-01
Ah direct from ATI!

Cheers bud, I have set it downloading lets see if it fixes it :) I'll report back later :)

---

### Post by mastablasta on 2011-03-01
besure to purge previous bad drivers before installing new ones.
otherwise any reason why the ones in the hardware drivers menu don't work? you did install them through there?
 
Another option is to use newer Ubuntu version (unless you already use 10.10).

---

### Post by Bugsy_malone 666 on 2011-03-01
> **mastablasta said:**
> besure to purge previous bad drivers before installing new ones.
otherwise any reason why the ones in the hardware drivers menu don't work? you did install them through there?
 
Another option is to use newer Ubuntu version (unless you already use 10.10).

Not entirely sure how to purge the drivers?

Its taken me a little while to understand what I was doing but eventually I got the ATi drivers loaded and ATi catalyst would run, however screen resolution would be lower than that of my monitors (I have 2 differnt size displays).

So first up I turned mirror/clone off then adjusted the resolutions to match my monitors capabilities and catalyst told me I would need to restart, so press ok, press restart and it didnt work.

Now I tried various different things here, first I tried using 'monitors' like normal to adjust the displays but that wouldnt let me because catalyst had control, so a few reboots later I still had a mirror display, so went through Catalyst admin, changed the settings and rebooted, it then went through its works loaded up and came up with a similar problem to something I posted on here before where the mouse would get locked into a smallish area on my left screen and my menus are all on the right screen, so power button off, the dialog box comes up on within the mouses locked area, select restart and try again. This time on boot up I select recovery mode, go into the display thing and select reset to default config, then reboot.

So machine boots, back into mirror'd mode, no ATi drivers as catalyst wouldnt work and told me so! Reinstall the drivers and try again, this time once I had gone through the catalyst contol panel and changed the settings to match my setup, did a reboot, ubuntu comes up briefly then it goes black and the monitors flicker on and off as if trying to determine the resolution or something eventually it comes up with an error and an option to go back low graphics mode, however in low graphics mode catalyst is disabled and I cant adjust the display/dont know enough as to if there is anything else I should be doing.

So basically I end up with nothing really working! If I had 1 monitor I probably wouldnt have any issues, its almost as if the problem lies with have 2 screens and 2 lots of resolution.

At this stage I am guessing there must be a way to completely uninstall the ATi drivers, then clear all data from previous installs and then start from scratch and see if it will work.

When linux works it works lovely (alot quicker to boot up) but when it breaks, I keep ending up back at windows coz that just works!!

---

### Post by mastablasta on 2011-03-02
> **Bugsy_malone 666 said:**
> Not entirely sure how to purge the drivers?
 

removing:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)
 
Info on opensoruce driver etc.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

