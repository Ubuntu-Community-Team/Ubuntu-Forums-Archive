---
title: "BCM43xx Install - how I got it to work."
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by paul5082 on 2006-10-29
Steps I used to enable BCM43xx network adapter:

1) 	Installed ndiswrapper.
2) 	Installed "Windows Wireless Drivers"*****

This didn't resolve the issue, but those are needed to complete the process.

3) 	I found this useful link:  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper) 		and followed these steps:

4) 	Edited the /etc/modprobe.d/ndiswrapper as follows:

	alias eth1 ndiswrapper

	# alias wlan0 ndiswrapper - changed to above for test (This was the original line)

5)	Run  "echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist" (without the quotes)
	to add bcm43xx to the blacklist to avoid starting on boot.

6) 	Next, as per the article, run the following 3 lines:

			sudo rmmod bcm43xx
			sudo rmmod ndiswrapper
			sudo modprobe ndiswrapper

I didn't use the fwcutter program this time, and make sure to install all of the ndiswrapper components, as they don't all seem to install. Use Synaptics package manager to search for ndiswrapper.  The "Windows Wireless Drivers" module is now called "ndisgtk."

I rebooted the computer, and the BCM4306 wireless is working! Of course, I had to default temporarily to hard-wire network to get it to work, but it was worth the effort.

***** You will need the bcm43xx wireless drivers in order to use the windows wireless utility.  I did this by extracting the Dell drivers from their cd and saved them to a bcmwireless folder and copied it to my home folder.  The files needed are the bcm*.inf, bcm*.cat, bcm*.sys files. I used the bcmwl5a.inf to load with Windows Wireless Tool.

---

### Post by squibT on 2006-10-29
Now try setting it up with security :)

---

### Post by ubuntu-mike022465 on 2006-12-04
Has anybody got the bcm43xx-fwcutter working WITHOUT having to blacklist it, and WITHOUT having to use ndiswrapper?  I've got a broadcom 4306, and am not having any success running it at all.  Is there a step-by-step howto, and I do have Edgy on my Presario R3120CA working.  

  I had installed the latest Fedora Core, and their bcm43xx was working perfectly.  But I had to come back to Ubuntu, so I reinstalled Edgy, and am now at getting the wireless to work.  I don't want to have to resort to using ndiswrapper if possible, so a simple a-b-c for bcm43xx would be awesome.  

  And yes, I've searched, and everyone is recommending blacklisting, but there must be someone out there who's managed to tame this problem.

Bueller? Bueller? Anyone?  :P

M.

---

### Post by paul5082 on 2006-12-04
It worked fine and easy with Ubuntu 5.10, but this is the only way I could make it work with 6.06 or 6.10. I haven't seen much of anyone doing it without blacklisting the detected card.  This has worked fine, and is actually rather fast on my network. It also doesn't take much time. The link in the original post is very informative.  I shrank it down to the steps I used to get it working.

---

