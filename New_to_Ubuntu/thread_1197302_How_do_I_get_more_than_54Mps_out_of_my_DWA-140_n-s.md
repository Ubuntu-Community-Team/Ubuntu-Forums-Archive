---
title: "How do I get more than 54Mps out of my DWA-140 n-series USB adapter"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by gvansickle1 on 2009-06-25
I have a D-Link DWA-140 USB adapter (ralink rt2870) running Jaunty 9.04 and am only getting 54Mb/s with "n" series router (getting 270 off XP). I'm bettin that the new driver (under the post below) would solve my problem but being very new to Ubuntu I'm also bettin that there are some details beyond what is provided 'sudo make', 'sudo make install', reboot and voila". Could anyone give me some additional info RE "sudo make" and "sudo make install"? Do I cd to a specific folder? What are the specific command lines I need to enter? Any switches to be used, etc? 

Although I'm new to Ubuntu I'm lovin it! I have a large family with multiple PCs (6) so I'm the IT department. Having tired of constantly having to rebuild Windows systems when a shop owner suggested I try Ubuntu I jump on it. After the first install I was hooked. I've already wiped W2K, XP and Vista Home off of the 6 systems at home and have installed and am now running Ubuntu 9.04 on 3, Xbuntu 8.10 on 1, Kubuntu 9.04 on 1 and Mythbuntu 9.04 on the 6th. Lovin it...:grin:
[B]
Re: Install linux drivers for ralink rt2870[/B] 			
 			 			 		   		 		 		 	Quote:
 	 	 		 			 				 					Originally Posted by **mizunoX** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7164669#post7164669") 				
 				[I]I'm having the same issue with a ralink 2870 and a fresh Jaunty install.
It finds the card and works without any additional driver compiling/installing however it maxes out at 54Mb/s. I achieved much higher with the same card and Intrepid (though I had to compile and install a driver as above)

-- EDIT -- I followed someone else's instructions to download the new ralink driver from their website: [http://www.ralinktech.com.tw/data/dr...A_V2.1.1.0.tgz]("http://www.ralinktech.com.tw/data/drivers/2009_0424_RT2870_Linux_STA_V2.1.1.0.tgz")
Extract to a folder, enter the folder and 'sudo make', 'sudo make install', reboot and voila. It's connecting to 5Ghz networks at 300Mb/s.[/I]

---

### Post by ptn107 on 2009-06-26
My desktop uses an Atheros AR2413 802.11bg NIC (rev 01) network card using the ath5k driver from the linux-backports-modules-2.6.28-13-generic  (jaunty) package.  It may be by design but network-manager shows 54 Mb/s, no matter what speed I'm actually at.

---

