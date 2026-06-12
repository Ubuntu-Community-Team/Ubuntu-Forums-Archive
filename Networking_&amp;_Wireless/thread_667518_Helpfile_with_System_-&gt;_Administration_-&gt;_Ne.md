---
title: "Helpfile with System -&gt; Administration -&gt; Network"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by mvdberg112 on 2008-01-14
Running Ubuntu 7.10 Gipsy Gibbon

From System -> Administration -> Network the following program is run:
[INDENT]gksu network-admin[/INDENT]
The help of this tool is quite limited, so I had a hard time finding out some of the stuff. No offense to the author,who has done a good job putting the current documentation together.

Whoever it helps, here is my own addition to the help file. It goes into section 3.1 of the original manual. 
Since I am partialy a newbie on Linux, can somebody tell how to publish this in such a way that the widest number of people can profit from it and that it might be added to future distributions of Ubuntu or any Linux flavor?

Configuring the wireless network
(in addition to the current information in 3.1, not in stead of)
3.1
[SIZE="5"]3.1.1 Configuration options for Wireless Connections with the Network[/SIZE]
The Wireless Connection will show an instance for every IEEE 802.11 Wireless Ethernet interface, sometimes called Wifi. Wireless Ethernet allows for Access Points (AP) to be configured and connected to a wired infrastructure, so that Stations (STA) can connect to such AP and be connected that way to the larger infrastructure.
If the network interface is an IEEE 802.11 wireless interface the following option will be available for configuration:
***The 'Enable roaming mode' option***
 The Network Manager supports Roaming mode. This allows you to connect to any available wireless network in range. 
 When checked, this option will select automatically, a connection will be slected from any wireless network in range. One can select a preferred network from the Network Manager icon in the taskbar. This icon only alows the to select the preferred network, when 'Enable roaming mode' is checked.
 When cleared, a connection will be attempted to the wireless network as configured by ESSID and Encryption key. 
 It is important to realize that the settings on the Stations need to be same as on the AP in order to connect.
*** Wireless Settings - Network name (ESSID)***
 Fill in the name of wireless network that has been configured in the AP that one wants to connect to. If this is left blank, the Station will atempt to connect to any network in range that publishes it self.
 Every IEEE 802.11 network needs to have name, to make them distinct from other wireless networks. If multiple APs have the same network name, they are considered to form one wireless network and they should be all connected to the same IP subnetwork. 
[B]
* Password type and Network Password*[/B]
This option sets the encryption type of the connection and needs to be exactly the same way configured as the AP. At the moment three encryptions are supported WEP key, WPA Personal and WPA2 Personal. For WEP one can enter either the hexidecimal key or the ascii value. 
*Network type WEP key (hexideciamal)*
Network type: select WEP key (hexidecimal)
Network password: Valid values for WEP Hexadecimal need to be 10 or 26 digits long (2 for each byte) and are for example: BEEB1, 00AF45BEEB00AF45BEEBCAFE12.
The WEP keys configured in this tool are always key 1. Some networks might allow configure up to four keys. This tool uses only the first key.
*WEP key (ascii)*
Network type: select WEP key (ascii)
Network password: Valid values for WEP Ascii need to be 5 or 13 charactrer and are for example: beep1, BEEP1, pappa, green, beepcafe12345, EnCouRaGeMent, inconceivalbe
Note that the WEP key is case sensitive and that so BEEP1, beep1 and Beep1 are different keys.
Ascii keys can be translated into Hexidecimal keys by use of an Ascii table, which are abundently available on the internet.
Again, the WEP keys configured in this tool are always key 1. Some networks might allow configure up to four keys. This tool uses only the first key.

***WPA Personal and WPA2 Personal***
Network type: select WPA Personal or WPA2 Personal, depending on the setting of the AP infrastructure.
Network Password: Both WPA Personal and WPA2 Personal use a shared key, which is the same on both the AP and the Station. Valid keys are:

***Connection Settings***
The connection settings can be set to 'Automatic configuration (DHCP)', 'Static IP Address' and 'Local Zeroconf network (IPv4 LL)' and these settings work the same as for the other (wired) network types.
[B]
*Using nm-applet to configure wireless connection*[/B]
When the option 'Enable roaming mode' is checked, an icon in the taskbar will appear and change into a icon that shows the signal strenght. One can use this icon to modify some options of the automatically selected wireless connection.
***Disable or (re-)Enable Wireless***
Right click on the icon in the task and select 'Enable Wireless'. This will toggle the wireless network between enabled and disabled. When a checkmark is placed before 'Enable Wireless', the wireless network is enabled.
***Disable or Enable Networking*** 
Right click on the Network Manager icon in the task bar. A check mark before 'Enable Networking' means that networking is enabled. 
Selecting this option when 'Enable Networking' is checked, will disable networking and will un-configure all the network interfaces. All the network interfaces will be brought down and the instances in Network Settings, will show 'The network interface is not configured'. 
Selecting this option when 'Enable Networking' is unchecked, will enable networking and configure all the network interfaces with the previous settings. Alternatively, one can re-enable and re-configure the interfaces with the Network Settings, reachable by System -> Administration -> Network.

***Information about current configuration and status***
Right click on the Network Manager icon in the task bar, and select 'Connection information'.

***Modify settings when roaming is enabled***
When roaming is enabled (see above), the wireless network will be automatically selected from the available networks. One can modify and adapt the settings of the Station to match the AP, by clicking on the icon. The following options are available:
 - a list of available networks - select one to connect to
 - Connect to Other Wireless Networks
 - Create New Wireless Network
 - Manual configuration
Refer the manual of the aplet for more details on the configuration with that applet.

Sources:
[https://help.ubuntu.com/7.10/internet/C/wireless-connecting.html](https://help.ubuntu.com/7.10/internet/C/wireless-connecting.html)


This info is copyright free - which means that I give away the right to distribute it under the GNU licens: 
	  Permission is granted to copy, distribute and/or modify this
	  document under the terms of the GNU Free Documentation
	  License (GFDL), Version 1.1 or any later version published
	  by the Free Software Foundation with no Invariant Sections,
	  no Front-Cover Texts, and no Back-Cover Texts.

---

