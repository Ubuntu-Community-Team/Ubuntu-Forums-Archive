---
title: "Howto: Asus WL138-g v1 marvell in Feisty Fawn AMD64 with WEP."
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by Jouke74 on 2007-04-23
Ok, this text is how to get this card going with WEP encryption and ndiswrapper under Feisty. Despite several attempts I have not been able to get it working with WPA. If other people have a good working solution then they can add their findings here if they feel like. 

1. Download the right 64bit windows drivers for this card. As reported on the ndiswrapper site the older WIFI_2712_64Bit.zip driver from Asus works well. The driver is difficult to obtain from internet. PM me in case you are really unable to obtain it. Other drivers may work, or may crash Ubuntu.

[ftp://dlsvr01.asus.com/pub/ASUS/lan/wifi-g/WIFI_V2712_64bit.zip](ftp://dlsvr01.asus.com/pub/ASUS/lan/wifi-g/WIFI_V2712_64bit.zip)

2. Download Ndiswrapper version 1.42 source, DO NOT install any ndiswrapper through Synaptic!!

3. Install the build essential package with Synaptic.

4. Extract the Ndiswrapper source to your home directory in subdir ndiswrapper-1.42. 
Also extract the 4 windows driver files (inf + sys) to this directory.

5. Open a terminal window, change to the ndiswrapper-1.42 subdir and copy/paste the following commands:
If you receive errors on any command, stop and figure out what's wrong. 

**su **
(and enter password, you're now root so be carefull).

**ln -s /usr/src/linux-2.6.20-15-general /lib/modules/2.6.20-15-general/build **
(creates a link for the ndiswrapper source to the kernel source) 
(check if Kernel headers have not been uninstalled, standard they are there in Ubuntu)

**make distclean**
(prepares build)

**make DISABLE_USB=1**
(builds)

**make DISABLE_USB=1 install**
(installs ndiswrapper)

**ndiswrapper -i mrvknt.inf**
(installs windows driver)

**ndiswrapper -l **
(check if driver is present, if card/driver is not present see ndiswrapper site for troubles) 
(the rest is of no use if you have this not working)

**depmod -a**
(should produce no errors)

**modprobe ndiswrapper**
(puts module in kernel)

**sudo gedit /etc/modules**
Add the line "ndiswrapper" without quotes to the modules file (this will have it run on startup).

6. Even with several attempts using gnome-network-manager (nm-applet) or wifiradar I could not get the wireless card to connect to my access point under WEP / WPA. It seems like some parameters from the program's are simply not getting through to the windows driver under ndiswrapper. 

7. Open synaptic and remove "network-manager" and "gnome-network-manager".
(has no other consequences for so far).

8. Under Preferences > sessions disable the network manager at startup (since it's gone).

9. Go to Administration > network.

Here are all your network connections.

Click on wlan0 (wireless card) and click properties.

Click on enable this connection (disable roaming).

Under wireless settings fill in your ESSID (network name) and WEP key type (I use hex here) and key itself.
I choose autoconfiguration with DHCP, otherwise manually configure your IP, gateway, DNS etc.

Close the network applet.

10. Right click on the top applet bar of gnome. Click on add to panel. Add the network-monitor to have some basic monitor for network flow (other options are possible here).

11. Important, reboot to have all changes take effect. After reboot your network should be getting connected.

Router: I set my router to "Open network with WEP HEX 128bits security and DHCP". I also set-up my router to accept only 2 MAC addresses. (to increase the security a bit, as this used to be WPA). I don't know how this works for all routers, so see your router manual for details.

Best wishes, JJ.

---

