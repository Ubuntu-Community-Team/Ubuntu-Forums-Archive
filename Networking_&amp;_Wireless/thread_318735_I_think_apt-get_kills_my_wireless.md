---
title: "I think apt-get kills my wireless"
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by DirtDawg on 2006-12-14
Using the sticky how-to I got my linksys wireless-g running, but I have noticed the signal is sometimes lost. After watching it for a couple days, I believe it has something to do with synaptic and apt-get. Whenever I use one of these, after the download and install are complete, I lose signal until I unplug and replug the wireless from the usb. I have also noticed I sometimes lose signal when attempting to watch some streaming video.

I am fairly clueless when it comes to wireless networks or networks in general, any suggestions would be welcome.

Thanks

---

### Post by mono1001 on 2007-11-19
i think i have the same problem with 7.10.  When i boot and log in i can (automagically) connect to my wireless network and get an address via dhcp but cannot ping anything other than myself for about 3 minutes.  And then i can get all connections perfectly, until some strange event happens that destroys my connection.  I think it might be related to apt-get as well because i recently had an error installing an update, so i left the apt-get updater in my "system tray" for 2 days.  during this time i never lost my connection.  Now when i say that this strange event "destroys" my connection i mean that i still have a valid ip address, the KNetworkmanager systray app claims that i am still connected, but i cannot ping anything other than myself.  I have an edimax pci card 802.11g (which uses the rt61pci kernel module).  I have tried unloading the module and loading it again, taking the interface down and then up again and neither work.  The system won't even recognize my wireless card after that.  so i have resorted to setting apt-get to not check for updates daily, but it just happened again...as i was trying to load some random youtube video.  this is really weird...does anyone have a clue?

---

