---
title: "Feisty 7.04 (19-4-07) wpa_supplicant.conf"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by christo_lac on 2007-05-03
I want to connect to our corporate network with Ubuntu Feisty 7.04 (19-4-2007) using wpa_supplicant. I have read a few “How to’s” and I see I need the append the wpa_supplicant.config file. I cannot find such a file on my system and none of the help files actually describe where to find the file or how to create it. I have a Atmel (driver at97_usb) card that works fine with Linux out of the box. I detect the SSID’s with 100% link and signal quality even with nm-applet. Note this is a fresh install and nothing was changed. I bought the card from radiolabs with Win, Linux and Mac support out of the box

1.	How do I create the wpa_supplicant.conf file and where must the file be stored?
2.	Do I have to uninstall network manager etc?
3.	Do I have to install anything else before I start with the conf file

Can anybody help with the configuration? My card is referred to as “wlan0” in iwconfig and the driver is at97_usb

The following information on our network was taken from Windows XP. The X is numbers that I cannot show.

SSID				:XXXXXX
MODE				:INFRASTRUCTURE
ENCRYPTION			:ON
SERVER AUTH			:NONE
RADIO 				:ON
AP AUTH				:WPA/EAS
TRANSFERE RATE			:AUTO
GROUP/PAIRWISE CIPHER	                     :TKIP/EAS
AUTH KEY MANAGEMENT	                                           :PRE SHARED KEY

MAC ADRESS			:OO.OD.2F.01.88.D3
IP ASDRESS				172.XX.X.146
SUBNET MASK			255.255.255.0
DEFAULT GATEWAY			172.XX.XX.1
DHCP SERVER			172.XX.XX.2
DNS SERVER				172.XX.XX.2
				172.XX.XX.3
WINS SERVER			172.XX.XX.2

---

