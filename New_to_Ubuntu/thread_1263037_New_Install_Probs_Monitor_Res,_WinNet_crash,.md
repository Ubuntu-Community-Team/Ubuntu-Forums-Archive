---
title: "New Install Probs: Monitor Res, WinNet crash,"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by The Glitchster on 2009-09-10
:( [Guess this was the wrong place to look for help, thanx for the one reply tho, it may help]
 
Have been poking around this site for a couple of days, but it's a bit like reading a road map through a microscope --- I need a "known, good, starting point".
 
Did a clean install of 9.04 (new HD):
Compaq Presario 5320: 1 Mb Ram / 16Mb nVideo "Ventra"
Envision EN-5100e LCD monitor
 
Hard cabled to Linksys BEFX41 Router --- also have Linksys WAP attached to router for another part of network --- latest firmware on both.
 
Installation went smoothly --- arrived at desktop, can access i'net, get updates, but not local win workgroup (yet).
 
Two problems after the install prevent me from going further:
 
1) When this station (Ubuntu) is online, via the Linksys Router, connectivity between other stations is disrupted, both the wired and the 8.11g segments. Have to disconnect this station then "win repair" affected (not all) stations. I suspect DHCP server (on Lynksys) geting currupted as most static IP stations survive.
 
This has precluded me from experimenting, much less trying to put the Ububtu box on my net, the ultimate goal.
 
2) The Envision monitor is stuck on 600 x 800, and listed as "Unknown". Sub windows open larger than the raster (cut off), and can be moved but not resized. If I had to guess, I'd say video leaving the card at 1024 x ?, monitor displaying at the lower res. (Worked fine at 1024 + under XP).
 
Initial boot, the pix was rolled 1/2 way down, but all there (ie horizontal retrace was in the middle of the screen). Rebooted, same. Pushed "Auto Config" on MONITOR, that worked.
 
Monitor controls, including underscan, do not "reveal" any more of the desktop, but not sure I'm seeing all the way to the "desktop edges".
 
Poking around the site, tried (whatever it means):
 
gk sudo displayconfig -gtk
sudo dpkg reconfigure xserver xorm (and some other stuff that seemed to fit)
 
No luck.
 
If I can get a good "picture" on a win network stable box, I'd be a happy camper, and will explore from there.
 
I obviously don't have a problem reinstalling from scratch :)
 
Any thoughts (or links) most welcome.
 
.../The Glitchster (a recovering MCSE)

---

### Post by zkriesse on 2009-09-10
Don't know if this will help you but it's Ububntu's site for the version's and the help/documentation surrounding them. [HelpUbuntu.com]("https://help.ubuntu.com/")

---

### Post by The Glitchster on 2009-09-10
> **Zachk18 said:**
> Don't know if this will help you but it's Ububntu's site for the version's and the help/documentation surrounding them. [HelpUbuntu.com]("https://help.ubuntu.com/")
I think I've ben there, but will give it another look.
 
.../Glitch

---

