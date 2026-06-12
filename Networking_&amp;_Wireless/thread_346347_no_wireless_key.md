---
title: "no wireless key"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by crunchyfox on 2007-01-25
ok so i have been working on this for a while.... 

i followed the directions i found here [https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29")

everything seems to be ok....i got no errors when installing the drivers .... my question is, i do not need a wireless-key to get online using my windows computer.... when i run the "sudo ifup wlan0" command this is what i get 

/ect/network/interfaces:19: option with empty value
ifup: could not read interface file "/ect/network/interfaces"

then it drops me back to #....ok so my interfaces file looks like this 

auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys
wireless-key1
auto wlan0

.... the router i connect to is called linksys - it is open to everyone and has no security on it
i have no access to it.... there is also another router i can connect to called netgear... wide open for all to use but i have no access to it .... i am able to connect to both with windows with out the need for a network key ... i search for a while for how to do this ....im stuck... 
sorry to be a pain ....  

thanks for all the help/patience

---

### Post by chili555 on 2007-01-25
sudo gedit /etc/network/interfaces

(note: It's /etc not /ect)

Remove the line: wireless-key1. Save and close.

sudo ifup wlan0

You may need to actually do sudo dhclient wlan0

---

### Post by crunchyfox on 2007-01-25
sudo ifup wlan0 returned 

/etc/network/interfaces:19: interface wlan0 declared allow-auto twice
ifup: couldn't read interfaces file "/etc/network/interfaces"

i also ran the sudo dhclient wlan0 command 

Listening on LPF/wlan0/00:12:17:97:43:c5
Sending on LPF/wlan0/00:12:17:97:43:c5
Sending on socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received
No working leases in persistent database - sleeping

then i get dropped back to #

---

### Post by spd106 on 2007-01-25
You should also remove the second "auto wlan0" line as well.

---

### Post by crunchyfox on 2007-01-25
removed that line and ran ifup again and everything is working !!!!


you guys are great!!!!

---

