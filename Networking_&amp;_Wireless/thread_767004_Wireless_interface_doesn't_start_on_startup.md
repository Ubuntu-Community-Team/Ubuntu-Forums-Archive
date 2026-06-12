---
title: "Wireless interface doesn't start on startup"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by justin_acklin on 2008-04-25
Ubuntu 8.04LTS.  Intel PM965 chipset.  Setup the wireless with the gnome network admin program.  Works fine, but when I restart, I have to go back in and re-load the settings for it to work.  Or, I can go to a prompt and :

sudo ifdown wlan0
sudo ifup wlan0

At which point it works fine.  Is there some other less crude and more automated way to do this?? I was thinking of just putting those commands in my /etc/rc.local and just eating the extra 10 seconds on boot time but I'd really rather just fix the problem outright.  I thought maybe I need to add "-w" to the wpa_supplicant command line but I cannot for the love of god figure out which script is the one actually starting wpa_supplicant.

---

### Post by justin_acklin on 2008-04-25
bump...nobody has any ideas??

---

### Post by DrCoolSanta on 2008-04-25
In the network manager, after you make the changes, click on the save icon and give it a name, see if this helps.
Also try doing a 
sudo /etc/init.d/networking restart
foes this get you the wrong settings?
Also check the settings in /etc/network/interfaces, does this show the right settings? It should since ifcown and ifup fix it but still try . . .

---

### Post by Iowan on 2008-04-26
> **DrCoolSanta said:**
> 
Also check the settings in /etc/network/interfaces, does this show the right settings?

One of the right settings would be an **auto wlan0** line.

---

### Post by justin_acklin on 2008-04-27
Running
sudo /etc/init.d/network restart

Brings the wlan0 interface up fine:

justin@justin-ubuntu:~$ sudo /etc/init.d/networking restart
[sudo] password for justin: 
 * Reconfiguring network interfaces...                                                                                                              There is already a pid file /var/run/dhclient.wlan0.pid with pid 6324
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1d:e0:83:ca:7f
Sending on   LPF/wlan0/00:1d:e0:83:ca:7f
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1d:e0:83:ca:7f
Sending on   LPF/wlan0/00:1d:e0:83:ca:7f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPOFFER of 192.168.0.106 from 192.168.0.1
DHCPREQUEST of 192.168.0.106 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.106 from 192.168.0.1
bound to 192.168.0.106 -- renewal in 284270 seconds.
                                                                                                                                             [ OK ]


And my /etc/network/interfaces file looks fine:
auto lo
iface lo inet loopback



iface wlan0 inet dhcp
wpa-psk biglongencryptedkeyhere
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid marvin5

auto wlan0



I saw in another thread someone suggesting adding pre-up sleep 20 to the interfaces file.  I will try that next.  Any other suggestions?

---

### Post by kevdog on 2008-04-27
So do the following (or make the following changes):

iface wlan0 inet dhcp
pre-up wlan0 ifconfig down

wpa-psk biglongencryptedkeyhere
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid marvin5

pre-up sleep 20
pre-up wlan0 ifconfig up

---

### Post by justin_acklin on 2008-04-27
I am not at home so can't try that but will when I get home.  I just noticed a new problem though.  I used the network-admin program to connect to the wireless network at my girlfriend's house and it's replaced the /etc/network/interfaces file.  Is there a way to put the settings for both networks in that file and never use the network-admin program?  Cause if I put the settings you recommended in, next time I go to my gf's house I will lose them, won't I?

---

