---
title: "yet another broadcom saga begins"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by sunshineacid on 2008-06-07
preface - so im new to linux... lets just throw that out there.
im not afraid of the console, and not afraid to reinstall (ive done this about 6 times now =P)

I have an HP dv8309us laptop with broadcom 4318.
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I had this working on mint linux, but i wanted to switch to full blown ubuntu, as in a few weeks i will be attempting to build a mythbuntu box, and wanted to familiarize myself with a similar distro. (i know mint is also ubuntu based)
The steps to get it working in mint were fairly straight forward 
1: blacklist b43 b44 and bcm43xx
2: install ndiswrapper w/ newest drivers off hps site
3: remove all drivers except ndiswrapper
4: reboot.

granted it took me 2 days to figure that out, but whatever =)

Ubuntu is kicking my butt though.

I tried the exact same method that worked in mint... no dice
Ive tried hardy specific ndiswrapper instructions... no dice
Ive tried enabling the 43 fw cutter... no dice

strange thing is, when i use ndiswrapper - wireless networking ceases to be an option anymore. i have to killall NetworkManager and restart networking manually... not even rebooting will bring it back!

when i use b43, my wlan light comes on, but i still cant see any networks. (better than when i use ndiswrapper.. the light doesnt even come on)
when i try to connect manually:
Jun  7 13:50:30 jason-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun  7 13:51:37 jason-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun  7 13:51:37 jason-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun  7 13:51:37 jason-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu

like i said, im a noob, so i have no idea what that means, except "your wireless is screwed"

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

please advise... i really dont want to admit defeat in ubuntu and go back to mint... the support here seems so much better.

---

### Post by sunshineacid on 2008-06-16
then again, maybe not =P

---

### Post by Ayuthia on 2008-06-16
> **sunshineacid said:**
> preface - so im new to linux... lets just throw that out there.
im not afraid of the console, and not afraid to reinstall (ive done this about 6 times now =P)

I have an HP dv8309us laptop with broadcom 4318.
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I had this working on mint linux, but i wanted to switch to full blown ubuntu, as in a few weeks i will be attempting to build a mythbuntu box, and wanted to familiarize myself with a similar distro. (i know mint is also ubuntu based)
The steps to get it working in mint were fairly straight forward 
1: blacklist b43 b44 and bcm43xx
2: install ndiswrapper w/ newest drivers off hps site
3: remove all drivers except ndiswrapper
4: reboot.

granted it took me 2 days to figure that out, but whatever =)

Ubuntu is kicking my butt though.

I tried the exact same method that worked in mint... no dice
Ive tried hardy specific ndiswrapper instructions... no dice
Ive tried enabling the 43 fw cutter... no dice

strange thing is, when i use ndiswrapper - wireless networking ceases to be an option anymore. i have to killall NetworkManager and restart networking manually... not even rebooting will bring it back!

when i use b43, my wlan light comes on, but i still cant see any networks. (better than when i use ndiswrapper.. the light doesnt even come on)
when i try to connect manually:
Jun  7 13:50:30 jason-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun  7 13:51:37 jason-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun  7 13:51:37 jason-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun  7 13:51:37 jason-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu

like i said, im a noob, so i have no idea what that means, except "your wireless is screwed"

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

please advise... i really dont want to admit defeat in ubuntu and go back to mint... the support here seems so much better.

Can you post your lshw -C network?

---

