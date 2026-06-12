---
title: "Odd wifi behavior"
date: 2005-05-03
forum: Networking &amp; Wireless
---

### Post by darthsabbath on 2005-05-03
My wifi card (broadcom chipset) has been acting a bit strange lately.  It will not connect on startup, but if I execute the command "ifconfig wlan0 essid MYESSID key open s:[MY KEY]", then "dhclient," it will connect. 

However, within a few moments, the connection will drop.  It's not the router, as Windows XP works fine on the laptop.

This only started a few days ago, and I've yet to determine the problem.

The networking applet is set to use DHCP, with my ESSID and a key of s:[MY KEY]. /etc/network/interfaces lists:

iface wlan0 inet dhcp
wireless_essid MYESSID
wireless_key s:[MYKEY]
wireless_mode managed
auto wlan0

I don't know of any configuration files to check. :-( Half considering wiping out the partition and starting from scratch, but that's the Windows way, and the whole reason I'm using Linux to begin with. :-P

If I need to post anything, please let me know, as I'm typing this on a Windows partition.

Thanks,
Phil

---

### Post by Psquared on 2005-05-05
Check out this thread. I don't have a Broadcom chip, but I do have wifi problems. Mine is related to the ipw2000 driver.

[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom)

---

### Post by darthsabbath on 2005-05-06
Just letting everyone know this problem has been taken care of.  Just did a clean reinstall of Ubuntu, as I had done something to my settings... no clue what. LOL :-)

Phil

---

