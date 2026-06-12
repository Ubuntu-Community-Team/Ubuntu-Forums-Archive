---
title: "MA401 and Hostap"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by nwoolls on 2007-10-01
I've got an old MA401 card from Netgear. It's worked fine for some time using the Orinoco driver. Now I'd like to use the hostap driver instead, as that appears to be necessary in order to use prism2_srec to flash my firmware (I'm looking to get WPA support working).

My sticking point is, I'm unable to get the card working with the hostap driver. I have the hostap packages installed. I tried following instructions online, which involved blacklisting the Orinoco modules in /etc/modprobe.d/blacklist-hostap-utils and then replacing all instances of "orinoco" with "hostap" in the /etc/pcmcia/config file.

Once I do this and reboot, I no longer have an eth1, which was my wireless network interface. iwconfig also shows no wireless devices. If I simply remove the blacklisting, but leave the modified /etc/pcmcia/config file, my system goes back to using the Orinoco driver (odd, does /etc/pcmcia/config not play a roll here?) and I have my wireless, but still can't upgrade my firmware to utilize WPA.

Any help would be much appreciated. Thanks in advance!

---

