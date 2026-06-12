---
title: "Ubuntu 20.04 wifi roaming between 2 AP's"
date: 2023-01-12
forum: Networking &amp; Wireless
---

### Post by tkhobby on 2023-01-12
Newbee to forum. I have google and read man pages with no joyful solution.

I have a laptop with 20.04 and a Pi4 with 20.04 specific to run ROS (robot operating system) Upgrading Ubuntu newest not an option.
I have everything setup and working, but I can't get this 'roaming' working.

I connect to access point 'shed' then walking into 'house' the laptop or robot (Pi4) stays connected to shed.
If I switch manually to 'house' it connects but walking back to 'shed' the WiFi sticks to 'house' 

iwconfig errors out with sens command
I don't have a /etc/wpa_supplicant.conf instead /etc/wpa_supplicant/ action_wpa.sh  functions.sh  ifupdown.sh

How do I activate or adjust the handover/sens/ value?
Or how do I force it to connect to stronger signal? the bot loses tele-remote operation while a stronger signal is availible

Its like it waits to loos WiFi signal all together before it starts looking for another access point.

---

### Post by TheFu on 2023-01-13
Usually, if you want automatic switching, you'll want to use the same SSID for both networks, assuming they are part of the same network, use the same DHCP server.  
Many wifi clients have a setting to control how "sticky" a wifi client is with each AP.  If you don't sit right on the edge between both APs, this might not be any issue.  
If setting these things isn't possible with your wifi client controls, it would be easier to get a "mesh" AP setup with 2+ APs that are centrally managed.  Nearly all wifi AP vendors have mesh APs.  I'd look at what Ubiquiti has and perhaps Asus, since they have long support periods.

It might be possible to just put a Ubiquiti wifi AP outside the house, pointed at the shed, to get the coverage you desire too.  I haven't looked recently, but they used to offer outdoor APs that would cover a good acre of space including buildings.

Just throwing out some options.

---

### Post by tkhobby on 2023-01-14
Thanks for the interest. WIFi mesh has to great a lag for tele-remote control of robots. Signal sent from one wifi to next wifi to router and a long string wifi back to laptop. I its faster to have wire access points (WIFI) and control base/laptop wired to router.

So the router is one access point and second is in shed, both with same SSID's with same pass. even changed to different SSID's with same pass but problem persist. 
I am going to google what a DCHP server is and will attempt to find the one I am using.

---

