---
title: "Broadcom BCM4331 Ubuntu 12.04/Mac OSX Wireless issues"
date: 2013-10-26
forum: Networking &amp; Wireless
---

### Post by skyone_29 on 2013-10-26
I am new to the "Leniux" world and have jumped into the "deep-end" with Ubuntu.  The install was fine (dual-boot) on my 15" MacBook Pro (2011).  The only main issue that I'm having is getting my wireless adpater to work correctly.  After searching through google, youtube, and a plethora of other avenues I've come to plead for help!  

I can connect through the wired connection just fine.  I have read throught this thread ([http://ubuntuforums.org/showthread.php?t=2166944](http://ubuntuforums.org/showthread.php?t=2166944)) as he was experiencing the same issue.  I've attempted all the steps as he was directed in that thread to no avail.  Below are the results or each of those attempt.  Also attached is the wireless script that the other guy ran for reference as well.

Wireless chip set:
Broadcom Corporation BCM4331 802.11/a/b/g/n [14e4:4331]

Typed: sudo apt-get install linux-firmware-nonfree
Result: 
Reading package lists...Done
Building dependency tree
Reading state information...Done
E: Unable to locate package linux-firmware-nonfree

Typed: sudo apt-get update && sudo apt-get upgrade
Result:
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [1,505 B]         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                    
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]  
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                            
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]    
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release [1,505 B]                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                            
E: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

Typed: sudo apt-get install linux-firmware-nonfree
Result:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-firmware-nonfree

Typed: sudo modprobe -r b43 && sudo mobprobe b43
Result:
"Nothing"

I know this is a long thread and a lot of "info".  Just wanted to be able to provide as much info about the problem as possible.

---

### Post by skyone_29 on 2013-10-27
Well apparently something that I did worked.  When I got home, upon stratup of Ubuntu, the Additional Driver app immediately popped up with the necessary drivers.  This would lead me to belive that the fire wall at work was causing interference with the app and it's ability to aquire the necessary conections and drivers.

---

