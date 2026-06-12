---
title: "Network Settings lost after reboots Ubuntu 6.10"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by mukeshwani on 2007-04-04
Hi All,

I'm using Ubuntu 6.10 on an old Dell laptop (P3 550MHz with 512MB) and a wireless network card (TRENDnet).  

When I installed Ubuntu, if found my wireless card and installed drivers and the installation was smooth.  I then configured the Network Settings (System->Administration->Networking) with my wireless information (essid, domain, host-name, dns servers, etc). The laptop connected instantly to my wireless network and I was browsing and connecting to other computers just fine.  I saved the configuration as a network location called 'mbw' and applied it.

After rebooting or restarting (after installing updates), the network location is not set as 'mbw' and I have to open Network Settings and select 'mbw' and apply it.   It happens after every restart.

Any help will be appreciated.

Thanks,
Mukesh

---

### Post by rolando on 2007-04-08
I have found gnome networking to always be like this.

I now use nm-applet, it seems to remember everything.

Use synaptic to install it.

Hope it works.

:)

---

### Post by chibiace on 2007-04-08
I also highly recommend NetworkManager.

---

### Post by mukeshwani on 2007-04-12
Thanks for the suggestion.  I installed it, but it keeps saying 'No Network Connection'.  Even though the wireless card is working.

Is there any tutorial or documentation on how to get the front-end working.

-Mukesh

---

### Post by chibiace on 2007-04-12
yeah it probably wants the network cards commented out.

in a terminal:

sudo nano /etc/network/interfaces

add # before all the entries except the two that have to do with lo (loopback)
like so:
auto lo
iface lo inet loopback

#wlan0
#iface wlan0 inet dhcp

ctrl+x then y to save


and add for startup on login:

nm-applet --sm-disable

in System > Preferences > Sessions

---

