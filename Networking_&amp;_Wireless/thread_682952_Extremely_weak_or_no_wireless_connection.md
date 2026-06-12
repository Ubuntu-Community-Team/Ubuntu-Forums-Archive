---
title: "Extremely weak or no wireless connection"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by markhorrocks on 2008-01-30
I purchased a Linksys WUSB54GC wireless card today to use with my new Gutsy install. The card did work staright out of the box, no adjustments with security turned off the router (Linksys WRT54G). 

My Ubuntu laptop and Windows XP laptop are in the next room from the wireless router. Both report approx 78% signal strength (4 bars in Ubuntu). While the windows connection works flawlessly, the Ubuntu laptop has a gret deal of trouble connecting at all. Only on 2 occasions did it connect at all. On the first, I actually got a google query to return a page and then clicked another link but the connection dropped out seconds later. On the second occasion I could connect, it dropped out after loading only a page title. Subsequent attempts (around 50) result in no conenction at all while a windows machine close by has no problem and never drops out. The connection is a 1MB cable connection.
The windows machine uses a built in wireless adapter whille the Ubuntu machine uses the USB wireless card. This laptop previously ran XP with a PCMCIA wireless card with no problems. The PCMCIA card is not supported in Ubuntu.

Anything I can do to troubleshoot? The connection is dynamic DHCP.

---

### Post by Hightide on 2008-01-30
Hi markhorrocks

can you post output from 

lshw -C network

and have a look at Kevdogs wireless tutorial. It may help

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

regards

:)

---

### Post by Hightide on 2008-01-30
sorry system crashed and i have input twice

---

### Post by markhorrocks on 2008-01-30
after I run lshw -C network, under the wlan0 section it says 
*network DISABLED
description: wireless interface
physical id:3
logical name :wlan0
serial: 00:1d:7e:03:fe:9b
capabilities: internet physical wireless
cofiguration: broadcasy:yes multicast: yes wireless:802.11g

dhclient -r wlan0 reports
wmaster0 : unknown hardware address type 801
listening on 00:1d:7e:03:fe:9b
sending on 00:1d:7e:03:fe:9b
sending on Socket/fallback

wireless card is RT73 chipset and supposed to work out of the box, no NDISWRAPPER used, the network icon shows athe network (linksys) (wrt54g) and connects very occasionally and only briefly and slowly.

---

### Post by markhorrocks on 2008-01-31
Today I again ran Kevdog's tutorial ie.
sudo lshw -C network

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "linksys"
sudo iw config wlan0 mode managed
sudo dhclient wlan0

This time, it connected! It revieved a DHCPOFFER form 192.168.1.1. And there was a connection where the netork icon normally sits. The sad news it that it lasted about 15 seconds then dropped out and the network icon disappeared completely after the bars went empty. . Now if I run sudo dhclient wlan0 it says network not available (or similar, this all from memory!). Note that my windows laptop right next to my linux laptop retains a strong connection.

Now I reboot and the network icon is back
I start to issue Kevdogs caommands again but the network icon connects in the meantime.
I continue running kevdog's commands and get a connection
So I try to open a page in Firefox, get a title only, and the bars empty from all but one to none, then it  drops the connection again.

I am at my wits end with this. Driving me nuts. I suspected the card but Windows identifies this card immediately and it is less than 24 hours old.

---

