---
title: "If I had a USB dongle for broadband, could I share it?"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by mikee55 on 2011-05-04
Hello, 
   Virgin Media supply my Broadband via a modem, connected to my router, it, wireless-ly feeds a Laptop and via LAN, my PC.
We want to use a USB dongle to have mobile Broadband on the Laptop, but when at home, could it feed 2 PCs and let me do away with Virgin and its Fibre Optics?

So if I plugged it into my PC, could I share Internet out through my LAN, to the Laptop via router?

Thank you

:(PS I don't like Natty Narwhal. Unity is not Gnome.:confused:

---

### Post by wolfen69 on 2011-05-04
I can't help you with your net connection, but if you want regular ubuntu, just log out, click your name, select ubuntu at the bottom and select classic ubuntu, then password. :)

---

### Post by gandaran on 2011-05-04
> So if I plugged it into my PC, could I share Internet out through my LAN, to the Laptop via router?
maybe I'm wrong but I think not, there is no sharing option in the mobile broadband setup like in wireless or ethernet.

maybe it would be better to buy a 3g router, I bought one on ebay for just 35 euros, it's connected to this desktop with ethernet cable and wireless for the netbook.

---

### Post by spiky001 on 2011-05-04
I have a 3 dongle on my pc which also has a wireless dongle, and wired eth0, the wirless dongle then shares internet with up 4 laptops I also have a eth0 hub so as to share via eth0  Hope this helps

---

### Post by cek on 2011-05-04
Yes you can share it easily.

However, I don't think you can share it out through your router.

I have a similar setup, I share the USB connection through my wired connection to several other computers in the house.  Each computer I have uses a static IP address, and sets the default gateway to the IP address of the host computer (the one with the USB connection).

It's trivially simple to set this up using firestarter as the firewall.  I've yet to find a replacement for firestarter that works as easily.

---

### Post by Dr. Nick on 2011-05-04
If I understand you right this should be easy, I have never used mobile broadband myself though.

Hook the mobile broadband up to your desktop and get internet working, Then right click the network icon or go to your network connections and on your wired connection tab select the auto eth0 and go to edit, go to IPv4 tab and change method to "shared to other computers". Hook up a cat5 cable between your desktops Ethernet card and one of the [COLOR="Black"]**LAN**[/COLOR] ports of your router and the router should act as a switch that you can connect to via wireless, If that doesn't work you can plug into the WAN port and it should get an IP from your desktop in the WAN section of your router and give out a wireless signal for the laptop

---

### Post by jcris on 2011-05-04
Dr. Nick is right, I been sharing a Sprint mobile broadband connection for over 2 years that way. Works like a charm.

1 - plug mobile broadband to main PC thats always on and get it connected. (I set to auto connect in case power goes out, will reconnect on its own).

2 - plug in network cable and run it to the router, click connection / Auto eth0 and set to share to other computers under the IPv4 tab.

3 - Drink beer and view porn from any pc in your house.

---

