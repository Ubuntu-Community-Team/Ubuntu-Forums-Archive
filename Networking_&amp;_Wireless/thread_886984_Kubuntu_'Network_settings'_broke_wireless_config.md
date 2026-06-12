---
title: "Kubuntu 'Network settings' broke wireless config"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by elyse on 2008-08-11
I'm setting up a new Linux Certified laptop with Kubuntu 8.04 installed. It came with the wireless working perfectly.

Today I loaded all possible updates, and everything still worked.

Set the hosts file and hostname, and everything still worked after a reboot, but KDE still was reporting the default name that the machine came with. 

I went into system settings/network settings, changed the host name,  and made NO other changes, and rebooted, and wireless was dead on reboot. It looks like Network Settings trashed the settings files.

Network settings recognizes eth0 and wlan0, but will not configure wlan0. In particular, it will not accept and save the hexadecimal wep.

knetwork-manager claimed to be finding my essid using wlan0, but would not offer the option of switching to that network.

ifconfig reports wlan0 and wmaster0 and eth0

lshw -C network only reports wmaster0 and eth0, not wlan0

/etc/network/interfaces looks like:
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iwconfig reports:
lo no wireless extensions.

 eth0 no wireless extensions.
 
 wmaster0 no wireless extensions.
 
 wlan0 IEEE 802.11g ESSID:""
 Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
 Retry min limit:7 RTS thr:off Fragment thr=2346 B
 Power Management:off
 Link Quality:0 Signal level:0 Noise level:0
 Tx excessive retries:0 Invalid misc: 0 Missed beacon:0

iwlist scan:
lo Interface doesn't support scanning.
 
 eth0 Interface doesn't support scanning.
 
 wmaster0 Interface doesn't support scanning.
 
 wlan0 Scan completed :
 Cell 01 - Address: 00:13:10:E3:09:CA
 ESSID:"draptors"
 Mode:Master
 Channel:6
 Frequency:2.437 GHz
 Quality=61/100 Signal level=-71 dBm Noise level=-127 dBm
 Encryption key:on
 Bit Rates::1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
 48 Mb/s; 54 Mb/s
 Extra:tsf=000000a032bf377c


 Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
 Tx excessive retries:0 Invalid misc:0 Missed beacon:0

I have been using and administering unixish systems since 1985. Could someone point me to the files that need to be edited?

---

### Post by caljohnsmith on 2008-08-11
Before I offer other ideas, after you tried changing the host name with Network Manager, have you by chance checked your /etc/hosts and /etc/hostname and make sure the host name for your computer still agrees exactly in those two files? I mention that because I've had problems using Network Manager to change my computer's host name; Network Manager didn't change both those files, and it leads to the classic case where you can't use "sudo" after that.

---

### Post by elyse on 2008-08-11
sudo was working.

I tried manually filling in /etc/network/interfaces with values for wmaster0, which did not work, and for wlan0, which did. 

Oddly, after running /etc/init.d/networking restart, the wireless was showing bars and I could ping my dns servers and [www.google.com](www.google.com) and [www.slashdot.org](www.slashdot.org), but the Konqueror browser could not get to the websites. Another reboot seems to have fixed things.

I suspect there are still inconsistencies in my config files, but I don't know where to look for them. At least I have network connectivity back.

---

