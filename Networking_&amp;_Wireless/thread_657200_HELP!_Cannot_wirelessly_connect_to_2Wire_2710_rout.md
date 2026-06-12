---
title: "HELP! Cannot wirelessly connect to 2Wire 2710 router"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by Maricaibo on 2008-01-03
Fiesty Fawn, 2Wire 2710 router. VIA USB wireless card saw the all the wireless networks in my neighborhood. I selected my network, entered the WEP key but it will not connect to router. I CAN  connect to router (and Internet)  using my wired connection. 

The router works fine with CAT5 on both Linux and WinXP, and I have a WinXP wireless working, too- just can't connect wireless from Ubuntu.

And can someone tell me where all the wireless config files are located? I've been at this for days now and I am Stumped!

brass@Ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 802.11-a/b/g ESSID:""
Mode:Managed Frequency=2.437 GHz Access Point: Not-Associated
Bit Rate=54 Mb/s Sensitivity=0/255
Retry min limit:8 RTS thrff Fragment thrff
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

PLEASE HELP!

---

### Post by gordon_a_mackay on 2008-01-05
I tried to outsmart wireless for two weeks. Finally away from all my manuals and network diagrams, I was forced to do this at Grandma's house. Let the system do it for you!
Set all your cards to Roaming mode. Plug in a wire and make sure you can see the network.

Login to the 2WIRE and make sure that DHCP is enabled.
You should now see that the icon on the top panel for the network shows wired with a little circle filled in. You should also see several wireless access points (or at least yours). Your AP name is implied on the bottom of the 2WIRE. It will be WIREXXX where XXX is the last 3 digits of your serial number above the bar code.

If you get this far, click on the 2WIREXXX and a box will pop up.
Select WEP 64/128-bit Hex for the Wireless Security
Enter the code from the bottom of the 2WIRE (under the bar code).
Choose Open System for the Authentication and press Login to Network.

Ubuntu will turn off your wired connection, negotiate with the AP and connect.
I messed with this for a long time trying to outsmart Ubuntu.
In the end it was simpler than I thought. Hope this helps.

---

### Post by Maricaibo on 2008-01-07
No joy. I can see my network plus others on my block (bot via the Network GUI and in Terminal) but I cannot get an IP address, from mine or other unencrypted nets available.


Sigh...

---

