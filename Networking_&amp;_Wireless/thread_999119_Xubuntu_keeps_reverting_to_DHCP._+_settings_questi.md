---
title: "Xubuntu keeps reverting to DHCP. + settings question"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by Rogue Jedi X on 2008-12-01
I'm behind a router and have a static IP. However, Xubuntu won't remember this as it keeps reverting to DHCP. Every time I log in I have to right click the networking icon, click "Edit Connections..." and do my thing.
I end up at the "IPv4 Settings" tab of the profile called "Auto eth0".

On another note, when I set my static IP (IP, Subnet, Gateway, DNS1 and 2), certain programs get issues. Urban Terror for example, is unable to retrieve the server list, while it has no problems doing so when in DHCP mode. I suspect the DNS settings, but I have the same setting in my Windows XP partition and I have no networking issues there.

Any ideas?

---

### Post by albandy on 2008-12-01
To fix this issue try editing your /etc/network/interfaces manually
(backup it first)

the dns problem is because when you are using static address you have to edit your /etc/resolv.conf and add the nameservers  manually.

/etc/resolv.conf contents:

search yourdomain.extension
nameserver dns_ip_1
nameserver dns_ip_2

---

### Post by Rogue Jedi X on 2008-12-01
I've edited it and /etc/resolv.conf already contains the proper DNS servers. Now it's exactly the same. What I forgot to mention before is that it's strange how firefox resolves the websites just fine, while others have problems getting server lists and such.

---

### Post by albandy on 2008-12-01
Are you using wifi or cable lan?
if cable lan edit /etc/network/interfaces like this but modifying addresses for your network:

auto lo
iface eth0 inet static
address 192.168.0.111
netmask 255.255.255.0
gateway 192.168.0.1


if you're getting problems with updates and package downloading from ubuntu servers, change to other mirror.

I'm in spain and usually ubuntu mirror servers are slow and or unreacheable, so I use french ones and works perfect.

---

### Post by Rogue Jedi X on 2008-12-01
I've set /etc/network/interfaces following your example, I can browse fine and all the other programs, apt-get included, work fine. I suppose the Urban Terror and Quake master server issues are game related. I'll sniff around on their forums a bit. Thanks for your help!

---

### Post by albandy on 2008-12-01
decrease your mtu size, try doing this before start the connection to the server:

sudo ifconfig eth0 mtu 1000

---

### Post by Rogue Jedi X on 2008-12-01
I have decreased the MTU size, as you suggested, but still no dice. Funny thing is, while both of these games seems to be having problems contacting the master server, XQF is having no problems whatsoever.
And I believe I forgot to answer your previous question: I'm on a wired connection.

---

### Post by flynch on 2008-12-26
> **Rogue Jedi X said:**
> I have decreased the MTU size, as you suggested, but still no dice. Funny thing is, while both of these games seems to be having problems contacting the master server, XQF is having no problems whatsoever.
And I believe I forgot to answer your previous question: I'm on a wired connection.

I'm having a similar issue, though I'm using wifi here. 
I've set the static interface information in /etc/network/interfaces yet when the machine boots it appears to get a dhcp address... then if I do sudo '/etc/init.d/networking restart' from a console the network restarts with the correct static address. 
I'm quite puzzled as to why this is happening and would really appreciate any theories or suggestions.

---

### Post by flynch on 2008-12-26
as an fyi I managed to resolve this issue (static ip on wifi getting old dhcp address. I executed the following commands:

> 
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 <STATIC_IP> netmask 255.255.255.0 up

sudo route add default gw <GATEWAY_IP>
sudo iwconfig wlan0 essid <MY_ESSID>
sudo iwconfig wlan0 mode Managed


obviously you'll need to replace STATIC_IP, GATEWAY_IP and MY_ESSID with the relevant values for your system. 
Upon reboot the machine successfully obtained its static address. :)

---

