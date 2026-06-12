---
title: "Auto-connect with ndiswrapper"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by Zarate on 2008-08-23
Hello people,

This might have been asked/answered somewhere else, but as usual the amount of information is HUGE. I hope i'm not just adding more noise.

PROBLEM: Ubuntu Hardy, Acer TravelMate 2200 laptop and wireless card (chip INPROCOMM IPN 2220).

My solution:

- Get [Windows driver]("ftp://ftp.work.acer-euro.com/notebook/travelmate_2200/driver/80211bg.zip") from [Acer]("http://support.acer-euro.com/drivers/notebook/tm_2200.html"). Download and uncompress. 
- Install ndiswrapper via Synaptic: ndisgtk, ndiswrapper-common, ndiswrapper-utils
- Go to System > Administration > Windows Wireless Drivers > Install new driver. Browse to the folder where the Acer driver is and select Win2k > neti2220.inf file. Close.

At this point I wasn't getting ANY network automatically and it's where the fun begins. I realized that doing a *manual* attempt to connect to any network via "Connect to other Wireless network" somehow triggered  the search and all of the sudden the networks where there for me. Tried to connect to mine and was connected without problems. Great! Well, sort of. After reboot it wasn't automatically connecting to the last network :( Again, starting a manual attempt to connect was doing the trick, soooooooo this is what i've done to workaround the problem:

- sudo gedit /etc/rc.local

Add this *BEFORE* the "exit 0" line:

/sbin/iwconfig wlan0 essid your_wireless_network

SOLVED! now the search is triggered during the boot and i'm automatically connected.

Please note that this is not solving the bug, it's just a workaround and probably not the most elegant. I'm happy to hear other solutions.

I've got this information from different places:

- [Find out the hardware you have]("http://ubuntu.wordpress.com/2007/02/18/find-hardware-specs-details-on-your-computer/").
- [WLan via Ndiswrapper]("http://ubuntuforums.org/showthread.php?t=31926")
- [NetworkManager finds wireless network, does not connect]("https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/85468")

Hope this helps,

Juan

---

