---
title: "Network-Manager problem with WPC54G v.1.2"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by DRob123 on 2006-09-01
I have my WPC54G card (Broadcom BCM 4306 rev 03) working fine and able to connect to WEP encrypted wireless networks or open wireless networks just fine.  I used the wl_apsta.o driver along with the bcm43xx-fwcutter to get the card to work.   After that I installed the network-manager in order to get WPA to work (my wireless network uses WPA).   Everything was going really well. I  de-activated and unchecked "Enable this connection" for ETH0 since I wasn't going to be using my ethernet card anymore.   The Network-Manager saw my wireless card, and let me connect to WPA encrypted networks, showed the signal strength (in bars up at the top) and it all worked well....until I rebooted.

After rebooting the Network Manager applet is up in the upper right corner, but shows "No network connection" and I'm back to only being able to use WEP networks or open wireless networks :(  

Any ideas why this was working until I rebooted?   Thanks for any help!  Oh, this is on Dapper also, with all updates done.  I had tried using ndiswrapper at one point for this card, but that didn't go well :)


DR

---

### Post by DRob123 on 2006-09-02
I tried blacklisting the ndiswrapper too as some places have suggested, but that doesn't seem to have made any difference :(    Anyone have any ideas?


DR

---

### Post by JackTheKnife on 2006-09-04
I have this same problem.

Just installed Ubuntu 6.06 and try to connect to the Internet using wifi Linksys WPC54g card. 

First what I figured out it was that card doesn't work with clear Dapper instalation. Tried to use this:

[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

I went through that installation and finally Ubuntu can use wifi card, but I have still problems to get to the Internet.

After reboot network icon shows that everything is OK (strenght 100%, etc), but DHCP doesn't resolve settings. Event when I put static IP after reboot I need to go to System->Administrator->Networking and do something with wifi card (for ex. deactive and active again or change some numners at static IP) to get connected to the Internet. ](*,) 

Any idea what is wrong? Thanks

---

