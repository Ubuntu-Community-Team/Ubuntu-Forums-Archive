---
title: "Get your wireless network going"
date: 2005-12-03
forum: Networking &amp; Wireless
---

### Post by HokeyFry on 2005-12-03
OK since I know what people go through to get this crap working, I am going to post what I did to get my wireless internet working.

#################################################

1. First, go into Synaptic Package Manager, and search for "ndiswrapper-utils"

2. Install it.

3. Go into Terminal and go to the directory where the .inf file and .sys file(s) are for the driver. (I had the CD for mine, but if you don't have one, research how to find your driver.)

4. Type in "sudo ndiswrapper -i driver.inf", where "driver" is the name of the .inf file.
(example: My .inf file was called "netwg111.inf". Yours will probably be different unless you have a Netgear WG111 usb or laptop card.)

5. Type in "sudo modprobe ndiswrapper"

6. Type in "sudo ndiswrapper -m"

7. Go into Networking (System > Administration > Networking

8. There should be a choice that says "Wireless Connection". It should also say that it is inactive.

9. Click "Wireless Connection" and then click properties.

10. Click "Enable this connection" and fill out the information accordingly. Make sure that you have the correct network name filled out. The Key type will normally be Hexadecimal. Make sure if you have a security key (WEP key) to enter it in the aptly named box: "WEP key". My network is configured with DHCP, so I chose DHCP as mine. If your network is not configured with DHCP, select "Static IP Address" and fill out the information accordingly.

11. Internet should work at this point. If it doesn't, you probably don't have something configured right. Go back and check everything.

12. To make this enable itself every time you boot up, open a terminal and type in "sudo gedit /etc/modules".

13. Add "ndiswrapper" to the bottom of all the text. There! Wireless should be configured an ready to go!

******************************************************************************
Edit: Monday, February 6
******************************************************************************

14. Since you now should have a working wireless computer, you will want an easy way to monitor your connection. Use Synaptic to download Wifi-Radar, an excellent tool to monitor and connect to various wireless networks.

Wifi-Radar Screenshot

[IMG]http://www.hantslug.org.uk/images/wifiradar.png[/IMG]

******************************************************************************

---

