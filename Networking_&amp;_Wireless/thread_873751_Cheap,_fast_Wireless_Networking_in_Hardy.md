---
title: "Cheap, fast Wireless Networking in Hardy"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by boomcat on 2008-07-29
This was ridiculously easy, cheap and fast, and it doesn&#8217;t even take up an expansion slot. No drivers, wrappers or cutters needed. The computer is a Dell with an all-Intel board and chipset, Pentium-D at 2-gHz and 1 Gig of RAM. I can&#8217;t vouch for all of the WEP, WPA, etc. options, but this got me on the air. You&#8217;ll need a working wired-network connection to begin this:

1) Buy an Azio AWU254 wireless USB adapter. Mine was $22.50
2) Connect the Azio to your computer
3) In a Terminal window, type ```
sudo lshw &#8211;C network
```
4) In the output text, look for the logical name, in a line that reads something like, &#8220;logical name: wlan0&#8221;. Make a note of it.
5) Download and install wicd. Here&#8217;s how:
```
http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html
```
6) Run wicd (found in Applications/Internet). Select the network you wish to join. In the text box marked &#8220;Wireless Interface&#8221;, enter &#8220;wlan0&#8221; (or whatever your text output said).
7) In wicd, enter your networking parameters: static IPs, DHCP, host, gateway, etc.
eight) Disconnect your wired network cable.
9) Your wireless networking should now be up and running.

This took me about five minutes last night. I have spent up to five days trying to get Broadcom PCI wireless cards to work, so this was an absolute revelation.

---

