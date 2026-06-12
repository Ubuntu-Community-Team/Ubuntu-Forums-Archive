---
title: "wireless: setup feisty fawn &amp; iMac"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by rutiezer on 2007-06-11



Trying to add wireless router to system setup that already has an iMac running OSX 10.4.9 through a Zoom series 0226 ADSL modem. 

What I've tried:
Added D-Link  model Dl-614+ Revision B 2.4GHz router to the setup and the iMac can access internet sites.

Changed ethernet cable that went from ADSL modem to iMac to go to WAN port of modem. Modem has four  ports. Added ethernet cable to go from one of the router ports to the iMac. The iMac can access internet sites with the added router.

Brought up browser on iMac to [http://192.168.0.1/](http://192.168.0.1/)  with 
From Home, clicked Wireless tab and set 
  SSID = Lipsey
  checked off 
      Auto Scan
      WEP open system 64 bit and entered 10 hex characters
 Clicked Apply


From Home, clicked DHCP tab and set
    DHCP Server enabled
    default of starting and ending IP addresses of 192.168.0.100  and 192.168.0.199, respectively
    lease time of 1 week
Clicked Apply and router restarted

Another try ran the Wizard setting
SSID = Lipsey
Channel = 7
WEP enabled, 64 bit and entered 10 hex characters

Current Firmware Version: 3.44
Firmware Date: 16 Nov 2005l
See emulator at
[http://support.dlink.com/products/view.asp?productid=DI%2D614%2B%5FrevB](http://support.dlink.com/products/view.asp?productid=DI%2D614%2B%5FrevB)
Not quite the same as what I see.
The Wizard is the same.
Wireless tab somewhat different for the emulator, but I think this is not significant.


Under Performance tab on router I see default values:
Beacon interval, DTIM interval Basic Rates, TX Rates, Short Preamble, SSID Broadcast enabled, Antenna transmit power, Antenna Selection, 4X mode enabled.

On desktop computer with wireless card and Ubuntu, (1) clicked  system -> administration -> networking -> wireless connection. Clicked properties and set the ESSID = Lipsey. Set the key to hex, entered the WEP key as on the iMac. Can't see the plaintext as it is entered. Set config to DHCP, marked "enable the connection" and clicked OK.

Noted that network proxy is set to direct internet connection. Is this OK?

Started a browser and could not connect to internet.

Took computer to office of ISP. They told me wireless card not working, wireless router not working. Replaced router with the one described above. Took computer to place that had wireless and tried connecting to Internet using the steps described at (1) above  and succeeded. I think this verifies that wireless card is working. 

When I change the ESSID of the router, Ubuntu computer with wireless picks up the new ESSID.  Properties shows other ESSIDs.

What am I missing?

Sorry for the long-windedness, but tried to put in details so someone can follow what I did.

Thanks.

---

### Post by airtonix on 2007-06-15
dont use the manual config

turn roaming back on for all devices

let the network-notification-tray-widget handle your wifi connections.

the icon will let you choose an available network by clicking one that is listed in the dropdown menu beneath the system-tray-network-icon

i had a dell laptop with broadcom wifi...to get it working properly i had to set everything to roaming.

i was connecting to an airport device(the airport-admin will provide wep keys for non-AFP devices), the macosx core duos were able to see my : smb, ssh. nfs, http, ftp shares that existed on my laptop.


if you want to force ethernet cable usage : disable wifi by left clicking systray-netowrk-widget-icon and select "disable wireless"

hope this helps

---

