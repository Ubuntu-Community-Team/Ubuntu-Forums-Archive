---
title: "Help connecting wirelessly on startup"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by lmarr28 on 2007-12-31
I've seen several threads on this subject, but I haven't been able to find anyone with the same problem as me.  So, I apologize in advance if this has been covered before.

When I start up my computer (an IBM ThinkPad T41 - running Gutsy), it's not connected to any wireless network.  After I've verified that I have no wireless connection, I can go to [SYSTEM > ADMINISTRATION > NETWORK] and the check-box next to my wireless card is unchecked.  When I check the box, sometimes it will connect, but sometimes I have to go into the "Location" box at the top of the window and choose my "Home" profile before I actually get a connection.  The "Home" profile is configured to use DHCP, my SSID is _not_ hidden, and I'm using WPA-PSK.

I'm using the Wicd applet instead of Network Manager, since I was having a lot of trouble with Network Manager in the beginning.  Most of the time when I boot into the OS, the Wicd applet icon is either missing from the panel, or it shows "no connection" until I go through the steps that I outlined above.

It's really no big deal, since I can still manually connect...  It's just frustrating having to go through those steps every time I boot the computer.  What makes it even worse is that my wife is completely computer illiterate, and she hates having to call me over to get the network connection up and running every time she turns the computer on.  :)

Below is my configuration info.  If anyone has any suggestions, please let me know!

**_Network card:_**
Atheros AR5212 802.11abg NIC

**_/etc/network/interfaces:_**
iface ath0 inet static
address 192.168.1.198
netmask 255.255.255.0
gateway 192.168.1.1
wpa-psk <my psk>
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid <my ssid>

Thanks!

---

### Post by kegobeer on 2007-12-31
You might want to try the development madwifi drivers.  I have a DWA-643 (Atheros AR5418 ) Expresscard wifi card and I couldn't get it to work until I installed those drivers.  Here's the link:

[http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008](http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008)

You might also need to follow this guide:

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

Hope this helps.

---

### Post by lmarr28 on 2008-01-02
Thanks for the info!  I'll give it a shot.  :)

---

### Post by lmarr28 on 2008-01-02
I got it fixed!

I ended up installing Wicd v1.3.4.  It's still in testing (v1.3.1 is the current stable release that I was using before), but it works like a charm!  Every time I reboot, it connects automatically now!

---

