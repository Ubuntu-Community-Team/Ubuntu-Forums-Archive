---
title: "6 question about  wifi network"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by the_bloods_city on 2008-05-09
first one: i change the mac address of my card but when i restart the pc it back to the original mac -what i can do about this thing ?

2# when i config my network manual  like put my ip and mask and getaway the wireless network Disappear from the list of the available networks 

3# i try the "wifi-radar" to solve the problem above but when iconnect to the network but when access to the internet and networkplaces it doesnt work (no internet and networkplaces )

4# my ip is 192.168.16.21 getaway 192.168.16.1   but the broadcast 192.168.16.255 is that ok or it should be 192.168.16.1

5# in the networkconfig box in the last tab there is 
127.0.0.1 local host
127.0.0.1 pc10 ----pc10=my pc name
........
....
did i have to change 127.0.0.1 in pc10 to my ip 192.168.16.21

#6 when i put `"ifconfig" in the terminal it give me my interface
and about wifi it give two (ath0 -- wifi0 )but ihave one wireless network is that ok or not

---

### Post by the_bloods_city on 2008-05-09
[SIZE="5"][COLOR="Red"]any body can answer me plz[/COLOR][/SIZE]
:confused::confused::confused:

---

### Post by the_bloods_city on 2008-05-09
[COLOR="Red"]***[I]_whers every body_*[/I]**[/COLOR]

---

### Post by wirelessmonkey on 2008-05-09
1) You'll need to create a script to set the MAC address during boot or network startup, there may be a way to add it to /etc/init.d/net, but I'm not sure.

2) By manual, do you mean through networkmanager, or via command line?

3) No clue, I don't use it.

4) Your broadcast address should be 192.168.16.255, which it appears to be.

5) This info is correct, don't make any changes.

---

### Post by .rdg on 2008-05-09
1) You could also set it in the interfaces configuration in /etc/network/interfaces file.

2) Setting the IP without associating with Access Point is not going to help you. Wifi is way different in its inner workings than ethernet.

3) I also don't use it

4) No errors here

5) No errors here either

6) I have two wireless devices in ifconfig: wmaster0 and wlan0, which is totally fine. I assumed (haven't read about that part of networking in ubuntu yet) the wmaster0 is some kind of virtual iface made by Network Manager.

---

