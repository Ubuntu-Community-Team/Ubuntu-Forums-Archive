---
title: "Can this be Done? Wired and Wirless in Same home using same modem but separate"
date: 2015-03-05
forum: Networking &amp; Wireless
---

### Post by mcapaldo on 2015-03-05
I have a Cable modem for my internet on my wired gigabit network for my computers.    I use DHCP for the Roku and HD Home Run Prime 3 to get ip's for those 2 boxes on same gigabit network.
All but one PC uses Ubuntu.  My DVR is Win 7 Media Center.    All static IP's.

now I can get a 2nd nic in the win 7 MC PC and plug the Home Run Prime directly into that.  And set Roku as wireless only.  

Now I was toying with setting up a wirless router to run the Roku, a few tablets, and occasional access for the smart phones.   Would have it secured.

I would shut down DHCP on wired gigabit router.  And just have DHCP on the wireless router.

Can I have 2 networks (wired and wirless) in house sharing same cable modem but deny wirless access to wired PC's and vice versa?  Will I leave my whole system vulnerable to attack/hack?

Please advise....Thanks in advance.

---

### Post by tgalati4 on 2015-03-05
If you have modified the firmware of your router (using dd-wrt or openwrt) it's possible to run two subnets on your router.  Most stock, consumer routers will only support one network.  To get the second subnet, you would need a second router set up correctly with a gateway and route statement to link the two subnets together.

Your security vulnerabilities are the same either way.  If your cable modem gets attacked, then it doesn't matter how the rest of the network is set up.  I would check the firmware version of the modem and try to update it.  That might fix some security holes.  Then upgrade the firmware on your router(s).

For blocking access to specific PC's, you can use IP-blocking or MAC address filtering, whatever your router supports.

---

