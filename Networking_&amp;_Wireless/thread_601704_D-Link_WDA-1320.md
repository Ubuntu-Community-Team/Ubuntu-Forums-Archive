---
title: "D-Link WDA-1320"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by g4c9z on 2007-11-03
I just bought a D-Link WDA-1320 wireless PCI card, and I'm using Ubuntu 7.04.  Some people said it works right away, but it doesn't seem to for me, unless I'm doing something wrong.

The network interface (I'm assuming ath0 is the right one) seems to have no problems according to the ifconfig command.  I went to Administration -> Network to create a new connection for it, and it recognized a bunch of wireless networks in my area.  I selected the one from my ISP and entered the WEP password they provided.  A message came up saying "configuring interfaces" or something, but Firefox browsing wasn't working.

For a short period of time, the internet did work before I configured anything (though slowly).  I'm guessing this was because my card picked up an unencrypted wireless network from a nearby computer temporarily.  It seems to indicate the card/driver does work and that the problem is configuring my connection.

I can connect to the Internet with Windows, after entering only the WEP password, using the Windows driver on the CD accompanying the wireless card.  Though my ISP did provide an ADSL username and password, I didn't have to enter them in Windows, so I assume that means the protocol is DHCP, which is what I entered in Ubuntu's network manager.  I'm also assuming that since I only had to enter the WEP in Windows, and the ISP didn't provide any WPA password, I don't need to enable WPA.  Is that true?

Does anyone have any suggestions or hints?  Do I need to install the madwifi driver?  (I assume it's already there since the Internet was working briefly.)  Would it help to use the ndisdriver instead?  (The chart here:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

doesn't mention that I need to.)  I also have a PPPOE connection on my ethernet card set up to connect at startup, from my old internet connection; could that conflict with the wireless card?

Thanks for reading.

---

### Post by Lambert on 2007-11-04
Do you know if your wep settings are open or restricted? If it's a restricted setting then there is a simple setting that needs to be configured.

Open a terminal and run the following commands

```

sudo iwconfig ath0 key restricted

sudo iwpriv ath0 authmode 2

sudo iwconfig ath0 essid ______

sudo dhclient ath0

```

In the blank insert your routers essid.

---

### Post by g4c9z on 2007-11-05
Well, I started my computer in Ubuntu today and suddenly the internet worked.  The speed and the fact that I configured the network manager to use my the ESSID from my ISP seems to indicate that it's really using my router.  Since I didn't change anything, my best guess is that the router needed to be unplugged and plugged back in or that the ISP was experiencing problems, which was happening when I was using Windows too.

Thanks for your help and suggestion, anyway.  If you don't hear back from me again, you can assume it's working.

---

