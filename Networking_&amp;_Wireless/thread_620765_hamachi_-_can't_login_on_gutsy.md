---
title: "hamachi - can't login on gutsy"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by Blind Tiger on 2007-11-23
** Note:  this thread has been solved. **

Howdy --  I completed a successful install of Hamachi and gHamachi on Fiesty.  But recently, after my upgrade to Gutsy, I decided to start Hamachi only to find that I cannot login and my network is not visible.  The gui starts up with full color, then goes b/w, and when I attempt to power up, it replies after a few seconds that it "cannot login".  Any help would be greatly appreciated.

Also, is Samba an adequate alternative to Hamachi?  Or is there another cross platform VPN that would rival Hamachi?

UPDATE
After a long break from using hamachi, I gave it another try.  Turns out my command to go-online was using incorrect syntax due to a space in the name of my hamachi network.  After figuring that out, I was able to run ghamachi from the command line using gksudo without error.  From there, it's just a matter of joining the network and entering the password.  File browsing is achieved by entering the smb://address (see this thread [http://ubuntuforums.org/showthread.php?t=603761]("http://ubuntuforums.org/showthread.php?t=603761")) as a location in nautilus or as a url in firefox.

---

