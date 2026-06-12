---
title: "Proposed wireless tutorial idea"
date: 2007-09-26
forum: Networking &amp; Wireless
---

### Post by uputer on 2007-09-26
Wiki or Tutorial for:

1)pci wireless card and automatic (dhcp) connection
2)usb adapter and dhcp connection
3)pci wireless card and static ip
4)usb adapter and static ip

* attempt the above based on 1) WEP and 2) WPA
* four GUI interface choices based on using 1) kwiki 2) knetwork manager 3) wlassistant 4) manual config and so on...(is #2 the same as #4???!?)

I would choose the Linksys adapter and card (WUSB54G and WMP54G respectively) since those are commonplace and relatively cheap if not the most popular wireless hardware.  It probably needs blacklisting or ndiswrapper but so far I fail to find any recent wireless devices that work out of the box with Feisty.  There are claims that some do but also instances in the forums of the exact same devices NOT working out of the box (and either no solution or an ongoing project of attempts).  

List device pci card with chipset and driver used and usb adapter with chipset and driver used and then instructions and steps taken.  

Doing the above would illustrate each connection option and provide details on potential outcomes and explanations for subsequent wireless connections.

This is not to promote Linksys at all but choose a card and usb to show the steps which probably only need minor modifications based on the chipset and driver and whether or not there are linux drivers or a need for ndiswrapper.   If there are linux drivers, there may be posts in which the steps taken in those posts can substitute for steps here.  The main point of this particular post and proposed tutorial is to include further options such as WPA and static IP into the mix.  The only options I've noticed is using dhcp and WEP.

---

### Post by spd106 on 2007-09-26
It's a good idea, but I feel there's already a great deal of information in the wiki on this subject. In fact the problem is that there's too much information spread across too many pages. I've counted at least four.

[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
[https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting](https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting)
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
[https://help.ubuntu.com/community/WifiDocs/WLANHowTo](https://help.ubuntu.com/community/WifiDocs/WLANHowTo)

I admit that these were built with the best of intentions, but as each version of Ubuntu has been released they have grown rather haphazardly. No doubt they will all change again when Ubuntu 7.10 is released next month.

Writing an excellent tutorial won't achieve its full potential if no-one can find it amongst the multiple other pages on the same subject.

If you or anyone else want to spend time cleaning up, merging and updating, please go ahead. I recommend that you visit the documentation team's wiki pages first and maybe join their mailing list too.
[https://wiki.ubuntu.com/DocumentationTeam/](https://wiki.ubuntu.com/DocumentationTeam/)

---

