---
title: "USB Wireless adaptor connected but internect stops after one successful link"
date: 2016-01-04
forum: Networking &amp; Wireless
---

### Post by erik38 on 2016-01-04
I've spent better part of 2 weekends browsing thru these and other forums but the problem is still not solved. I have Ubuntu 12.04 installed on two old PCs (a Dell box and an Asus box). I can connect the Engenius 9603 USB wireless adaptor to either PC and a connection to the router (or whatever it is that is out there) is made (wireless symbol appears in upper left task bar and shows connected). On the Dell, I can successfully navigate the internet with no problems. However, with the Asus, I can make it to one web site (have tried a few diff sites...) and then that is it, no further sites can be accessed, no further Google searches, etc. Yet the wireless status shows connected. 

One of the threads here, on this topic, showed how to download and run wireless-info, and I have attached the file from the Asus herein. I have looked it over but most of it I do not understand, and nothing red-flagged me. Running this on the Dell, I see mostly the same stuff. I can attach that one if anyone wants to compare (I haven't installed a txt file compare tool yet; I don't/won't use vi or any of its siblings - sorry). 

Some things I've tried from other threads:
1) gksudo gedit /etc/pm/power.d/wireless
 
(which created configuration file to override the default powermanagement behavior) and entered the following:
 #!/bin/sh
 /sbin/iwconfig wlan0 power off
 exit0

Then,
 gksudo gedit /etc/modprobe.d/iwlwifi.conf
 options iwlwifi 11n_disable=1

Outcome was no change.

2) Try disabling the eth0 wired interface.
ifconfig eth0 down

Outcome no change.

3) Checked  wpa_cli status
brik:~$ sudo wpa_cli status
Selected interface 'wlan0'
bssid=6c:f3:7f:3b:cb:32
ssid=L-Guest
id=0
mode=station
pairwise_cipher=NONE
group_cipher=NONE
key_mgmt=NONE
wpa_state=COMPLETED
ip_address=10.227.144.226

Well?

4) Tried  brik:~$ sudo dhclient wlan0   just gives up after awhile - see syslog:
Dec 19 14:47:44 brik1 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
keeps repeating.

I'm lost; would really appreciate some help.


Thank you.

---

### Post by erik38 on 2016-01-04
Adding the following as part of the "things I've tried":

Added the following to the /etc/network/interfaces file:
tomas1@brik1:/var/log$ sudo gedit /etc/network/interfaces
auto wlan0
iface wlan0 inet dhcp

>rfkill unblock all 

sudo /etc/init.d/networking restart
sudo rm /etc/udev/rules.d/70-persistent-net.rules
sudo reboot


sudo service networking restart
stop: Unknown instance: 
networking stop/waiting
syslog shows repeated dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8


sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces..

syslog:
Dec 19 14:24:04 brik1 avahi-autoipd(wlan0)[1969]: SIOCSIFFLAGS failed: Operation not permitted
Dec 19 14:24:04 brik1 avahi-autoipd(wlan0)[1969]: Callout STOP, address 169.254.8.102 on interface wlan0
Dec 19 14:24:04 brik1 avahi-daemon[738]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec 19 14:24:04 brik1 avahi-daemon[738]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.8.102.
Dec 19 14:24:04 brik1 avahi-daemon[738]: Withdrawing address record for 169.254.8.102 on wlan0.
Dec 19 14:24:04 brik1 avahi-autoipd(wlan0)[1970]: client: RTNETLINK answers: No such process
Dec 19 14:24:04 brik1 kernel: [  767.938081] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 19 14:24:05 brik1 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Dec 19 14:24:08 brik1 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4 (keeps repeating)


Outcomes were no change. Still drops internet access after the first web page download, regardless of web site visited. Seems very strange I think. 

Thank you again.

---

### Post by erik38 on 2016-01-09
HI again,

No views? Anyone have an idea to offer???

Thank you.

---

