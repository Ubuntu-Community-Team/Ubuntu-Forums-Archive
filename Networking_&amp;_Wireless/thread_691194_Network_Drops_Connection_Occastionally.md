---
title: "Network Drops Connection Occastionally"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by Hyperkill on 2008-02-08
A while back I was having trouble with the network manager applet not working for me and so I did not have access to the internet.  I decided to go out and buy a newer and better network card and settled on a D-Link.  Upon getting my new card NM-Applet still could not connect to my wireless network.  So, I decided to use ndiswrapper, something which I have never done before.  Now, whenever I reboot my computer I have to issue the following commands to get online...

```

sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 key restricted 910d349a0db11bb0067bdc3a04
sudo iwconfig wlan0 essid TonyDebbie
sudo dhclient wlan0

```

I threw them into a bash script called runnetwork.sh and now I just type "sudo sh runnetwork.sh" into the terminal when I reboot.  Every once in a while, especially when I'm downloading a lot of data really quickly, I will lose my connection.  When I run my script again I cannot connect to my network and have to reboot to fix the connection.  The terminal says the following after I try my script again after I lose my connection...

```

Listening on LPF/wlan0/00:1b:11:65:82:34
Sending on   LPF/wlan0/00:1b:11:65:82:34
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67

```

It will just keep repeating DHCPREQUEST on wlan0 to 255.255.255.255 port 67 over and over again.  What I'm hoping to accomplish is the following:

1.  Have my computer automatically connect to the internet on boot without having to run my script (not very important).

2.  Fix the problem where the network drops the connection during high traffic usage (important)

3.  Get back online without having to reboot all the time (very important)

I really appreciate any help that is provided to me.  I will be checking this post often to try out suggested advice and give feedback.

---

### Post by Hyperkill on 2008-02-09
Nobody has any ideas?

---

### Post by Hyperkill on 2008-02-10
Still nobody?

---

### Post by quill7111 on 2008-02-15
This sounds similar to a problem I'm having with the network manager GUI dropping the connection and not being able to reconnect without a reboot. I'd love to hear a solution as well...

---

