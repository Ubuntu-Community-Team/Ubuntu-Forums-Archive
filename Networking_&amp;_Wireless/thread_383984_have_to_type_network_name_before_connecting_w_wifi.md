---
title: "have to type network name before connecting w/ wifi?"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by sit properly on 2007-03-13
Hi folks, 

Just upgraded from Dapper to Edgy. Wifi worked perfectly in Dapper, but in Edgy:

I have to know the name of the network to which I want to connect and type it in "settings for interface."  Once I've done that, it will connect, but will not recognize any other networks. I can see other networks with WifiRadar, but "Network Settings" will not detect them. 

Is there an alternate way to find available networks and connect to them? I will be traveling soon. Things could get pretty interesting if i don't figure this out. 

Thanks.

(using a Sony Vaio, C-series)

---

### Post by gradedcheese on 2007-03-14
I've seen this problem before but I have no idea what causes it.  The card still scans correctly but in the Networking tool, the scan results don't show up.  You can use NetworkManager instead, it provides a very pleasant interface for choosing networks and replacing the Networking tool and Network Monitor completely (the next Ubuntu uses it too).  However find and follow the NetworkManager installation guide (search the forums) for instructions as there are a couple extra steps to setting it up (it's not very hard at all though).

Additionally, if you are willing, you should learn how to operate your WiFi interface via the shell.  It's a great way to just have things work if the graphical tools are a problem.  Some basic commands:

Lets say your interface is named wlan0, this is how you scan:

```

iwlist wlan0 scan

```

you will see a list of APs and their SSIDs.  This is how you associate to one:

```

iwconfig wlan0 essid put_ssid_here

```

If needed, this is how you ask for a DHCP IP address from the router after associating:

```

sudo dhclient wlan0

```

To check your IP address (if any), you run:

```

ifconfig wlan0

```

---

### Post by jbmech006 on 2007-03-15
I lost my essid list when I upgraded to edgy as well. I know work arounds exist, but if someone has a fix for this that would be awesome

---

