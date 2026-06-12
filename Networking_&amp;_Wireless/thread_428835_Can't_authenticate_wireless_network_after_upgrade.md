---
title: "Can't authenticate wireless network after upgrade"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by jordanm on 2007-04-30
I upgraded from Edgy to Feisty and can no longer connect to my wireless network. Feisty is able to detect some local WiFi networks (including my own), but I can't actually connect. When I click the Network icon, then select my local network a display pops up asking for Authentication. When I enter my WEP Hex key, it fails to authenticate regardless of what type of password/hex/ascii I choose and whether I choose open or shared.

Everytime I enter my password (regardless of the options I choose), the window goes away for a couple minutes then pops up again and asks for a password again.

Any ideas? My wireless worked on Edgy with the same wireless network and the same password. Now that I upgraded, I can't seem to authenticate and connect to my network. Any help is appreciated, as I currently have no internet at home and can only use the internet at work.

Thanks, Jordan

---

### Post by jordanm on 2007-05-01
Bump. If anyone can help I would greatly appreciate it.

---

### Post by reauthor on 2007-05-01
what is writing in /var/log/syslog?
can you write here your /etc/network/Interfaces

---

### Post by jordanm on 2007-05-04
/etc/network/interfaces:
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp

Back when I was using edgy I also had (wireless-ley commented out):
iface eth1 inet dhcp
wireless-essid Ohferreal Nannies
wireless-key **************
adress 192.168.0.120
netmask 255.255.255.0
gateway 192.168.0.1


Now I pulled that out though, since I no longer have an eth1 on feisty. Fiesty seems to have replaced my eth1 with wlan0 and wmaster0, which are not present in /etc/network/interfaces, but are present in the 'Networking' GUI with the description "Roaming mode enabled".

What's weird is that I can see Ohferreal Nannies and other WiFi networks now. Just when I connect to my network, the authentication window pops up and fails regardless of what type of key/password mode I select, eventhough I am using the same and correct key that worked on edgy.

Any ideas?

---

### Post by jordanm on 2007-05-04
I'd like to post /var/log/syslog, but its tough since I don't have internet access on this machine. The last couple of lines are:

localhost kernel: [9004.029881] WEP decrypt failed (IC)
localhost kernel: [9004.029893] wlan0: RX WEP frame,decrpyt failed

There are also lots of lines regarding avahi-autoipd, including some lines that "fopen() failed: Permission denied

Also lots of lines about ^Iwpa_supplicant(5728), including that "No keys have been configured - skip key clearing)

Let me know if you have any ideas. If you can't do anything without more of /var/log/syslog, then I can try to save it to a disk and copy and paste it into this machine.

---

