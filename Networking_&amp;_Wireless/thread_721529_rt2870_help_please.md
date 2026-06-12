---
title: "rt2870 help please"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by Kenjitamura on 2008-03-11
**This post could be related to an Ubuntu bug filed at**:   [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've decided to jump back onto the ubuntu community after a short affair with windows and if these problems keep up windows and me will probably run away together lol.  I have a Encore ENUWI-N wireless card that uses rt2870 drivers from ralink.  The drivers provided by the ralink site for linux don't work for me.  I'd like to use NDISWRAPPER but i can't get a hold of any windows 64 bit rt2870 drivers.  Their darn drivers come packaged in .exe file and unshield, unrar, and cabextract all fail to get the .sys and .inf files for me.  I have a laptop with windows installed but its 32-bit so when I try to load up the drivers I take from it and look at the log it says kernel is 64 bit drivers are 32 bit bad magic fail.  The card works flawlessly in windows.
Before I did a re install the linux proprietary drivers at least worked with my router when unencrypted but now there's nothing.  I've even F*ed my wired connection by switching between wicd and network manager so much that I can't get a connection.  I got this system 3 days ago and have spent about 24 hours total in increments of 6 or 7 working on this machine and now im about ready to dump ubuntu for windows.  (unrelated but other problem is with 9600 gt)

---

### Post by Kenjitamura on 2008-03-11
After some tweaking got WICD and (so far) unencrypted wireless working on the ENUWI-N.  I'd like to have WPA2, should i go for it?  BTW the card wasn't being detected by WICD because I had to place ra0 in the wireless interface box and then it wasn't connecting because I had to open up a terminal and type sudo iwconfig ra0 essid "(wouldn't you like to know)".  It was trying to connect to 11n-AP  by default for some reason.

---

### Post by Kenjitamura on 2008-03-11
All Solved.  Have Wireless N WPA2 network connected with the ENUWI-N.  Using the linux native drivers from ralink.

---

### Post by MattressVon on 2008-03-13
Can you tell me how you gfot this to work? I just bought EDIMAX EW-7718Un. I downloaded the rt2870 drivers and have absolutley no ide how to get them to install. I unzipped them with the install here option and tryed to follow the instructions in the readme file but I just don't know how to do anything they are asking me to do. I looked at the make file which looks like gibberish to me. I have googled and googled, and googled everything for two days now and found nothing that helps.

They ask to designate paths for stuff, where is that stuff and how do I do that? None of the directories look like what they are asking for and I cannot find anything anywhere that is called linux source. Can you please tell me how to do this in toddler speak. I've run this stuff before, but I know nothing about computers. Every step of this process has confused me. i tried ndiswrapper three times and it fails everytime. Another thread had a poster who said he would right a tutorial on how install the rt2870 driver. I have googled, and googled, and googled, and found nothing. 

Please can you tell me how you did this?

---

### Post by gibberish on 2008-04-16
I second MattressVon's request. I know some will treat this as heresy, but I have limited interest in the command line. I just want some simple way to load the driver, explained as if I'm the total idiot that I am. MattressVon, if you ever figured this out, could you let me know?

---

