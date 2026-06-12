---
title: "File editing required in 7.04 for Gigabyte GN-WBKG USB"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by dara on 2007-04-21
I've had good luck with Ubuntu 7.04 so far, and I quite like how easy it is to install the proprietary Nvidia drivers (which I require to watch HDTV).  However, I was disappointed to see I still have to edit /etc/network/interfaces in order to get my wireless USB device (Gigabyte GN-WBKG ) to work.  Network Manager is thus useless to me for now - maybe it will work on the next release.  Funny thing though - I have to use rausb1 instead of rausb0 which I used with 6.10.  (I found this out with sudo lshw - I don't think I moved the device though).

Anyway, here is the text I add to /etc/network/interfaces (after eliminating all but the first two lines in my case):

```

iface rausb1 inet dhcp
wireless-essid <your-essid>
wireless-key <your-wep-key>
auto rausb1

```(I got this from the thread [http://ubuntuforums.org/showthread.php?t=187201&highlight=dara](http://ubuntuforums.org/showthread.php?t=187201&highlight=dara)

Dara

---

