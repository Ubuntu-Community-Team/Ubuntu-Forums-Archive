---
title: "Linksys Ralink RT2500 Wireless Problems"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by GMU_DodgyHodgy on 2007-03-05
Afternoon All:

Another wireless issue.  I have poured through these boards and tried several fixes all to no avail.  As mentioned - My wireless card is a supported card so I have no issues - I believe with my card.  however, I can never connect with my wireless home network using a Linksys router (WPA-Personal encryption).  I have tried configuring the interfaces file, the wpa_supplicant file.  I tried fining the network-manager-gnome applet but I get a message that it cannot be found.  I am running Ubuntu 6.10 (Edgy) on a dual boot Windows XP professional box.  

I have been through so many different avenues - I think I want to start from the beginning and have one of the more knowledgeable members help me through this. 

Any help will be appreciated.

---

### Post by Spelley on 2007-03-08
WPA is causing your problems. The RT2500 driver built into edgy doesn't support it. You would need to disable it at the router level (and, obviously, in WindowsXP). I believe network manager also does not work with the rt2500 driver.

Of course, WPA is a good thing, so you may want to do a search in these forms for RT2500 and see if there are good instructions to use the ndiswrapper as a driver instead of the one built into edgy.

So... if you can stand to lose WPA, just go into ADMINISTRATION/ NETWORKING and configure everything there for your wireless card (which is probably called RA0).

good luck.

---

### Post by rclark68137 on 2007-03-09
I'm a noob, so I don't know if this will help you or not.  But I went through all the same frustrations that you've been through, trying to get my wireless adapter to work with WPA2.

I finally got my Linksys WUSB54G V4 to work in Edgy Eft (6.10) using WPA2 and AES.

I wrote up a "How To" here:   [http://moonintheroom.blogspot.com/]("http://moonintheroom.blogspot.com/")

Maybe it will help!

---

