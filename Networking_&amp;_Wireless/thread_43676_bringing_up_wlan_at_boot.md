---
title: "bringing up wlan at boot"
date: 2005-06-22
forum: Networking &amp; Wireless
---

### Post by darrell on 2005-06-22
Hi,

I'm using ndiswrapper with an Edimax PCI card (realtek chipset) and connecting at boot to a US robotics wireless AP (model USR2249).

My interface wlan0 is configured through dhcp.  the dhcp server is another ubuntu box running on the wired side of my network (NOT using the ap's dhcp facility)

I'm using a 128 bit WEP key and have locked down the wireless AP to "shared key only" I am also using the AP's MAC filter to only allow connections from specifc wireless cards.

Here is the /etc/network/interfaces section for the wlan card on my wireless client:

iface wlan0 inet dhcp
name Wireless LAN card
wireless_essid ********
wireless_channel 8
wireless_key restricted *******************
wireless_mode Managed
auto wlan0

The problem is, that it takes almost 5 minutes for the client to obtain an IP address. I have observed the process in verbose mode, (set -x in the relevent scripts) and the insertion of the ndiswrapper module and the application of the iwconfig options (above) fly through. it then takes nearly 5 minutes of dhcp requests before a reply is recieved (I have increased the dhcp client timeout to 5 minutes to confirm that it does eventually work).

Is it taking all this time to negotiate the WEP shared key? or does the ndiswrapper module need a bit of time to "warm up" (!!!). The strange thing is, that after boot, I can ifdown, and even rmmod ndiswrapper, and still a subsequent ifup almost instantly reconnects and gets an IP address. 

My gut feeling is that the initial iwconfig commands post boot (as detailed in the interfaces file extract above) are the cause - it seems that they are "remembered" afterwards, even when the actual wlan0 interface is taken down. Only a reboot causes it to start from the beginning again.

Any thoughts, anyone?

cheers,
Darrell

ps The USR AP is a buggy piece of ****. The web interface doesn't work properly, forcing me to boot a windows box just to configure it. Thinking of upgrading all my wireless kit to 54Mbps stuff.

---

