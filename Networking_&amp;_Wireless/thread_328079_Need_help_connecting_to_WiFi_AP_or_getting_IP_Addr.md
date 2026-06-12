---
title: "Need help connecting to WiFi AP or getting IP Address from router?"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by scaryant on 2006-12-30
Hi,

I've recently installed Ubuntu on my Toshiba Satellite Pro 4600 and managed to install the correct drivers for my 3Com USB dongle WiFi card (3CRUSB10075) however I'm having trouble with the last step, connecting to the access point. ](*,) I know the AP is working as my other laptop is connected to it now.

I've followed a lot of the troubleshooting tips from the [Ubuntu WiFi docs]("https://help.ubuntu.com/community/WifiDocs") but no joy. I reconfigured my router to broadcast the SSID and disabled WPA-PSK to try and make the connection easier while I test. The Channel is set to 5 and DHCP is enabled, addresses are 192.168.1.xxx and the subnet is 255.255.255.0. I also have the latest firmware installed on my router.

Any help would be greatly appreciated!! :)

Ok. I can see both my NIC's when I issue a *ifconfig -a* neither have an IP Address, my WiFi card has been given eth1. Of course I can see the device listed when I issue *lsusb* and I can see the WiFi modules (zd1211, zd1211rw) loaded under "usbcore" when I issue *lsmod*.

I can also see the WiFi AP when I issue an *iwlist scan*.

I can issue a *iwconfig eth1 essid MySSID ap 00:0F:CB:AB:91:BC commit* without any errors or warnings.

When I issue a *iwconfig* I get the following information about my WiFi NIC. One thing I noted is that link quality and signal level are present, does this mean I'm actually connected to the router, I would say yes but my USB key doesn't display any link/activity lights.

> eth1     802.11g zd1211 ESSID:"MySSID"
           Mode: Managed Frequency:2.462 Ghz Access Point: 00:0F:CB:AB:91:BC
           Bit Rate=1 Mb/s
           Encryption key: off 
           Link Quality=93/100 Signal level=92/100
           Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
           Tx excessive retries:0 Invalid misc:0 Missed beacon:0

When I issue a *ifup eth1* it begins the process and starts scanning (I think);
> Listening on LPF/eth1/00:0F:CB:C2:0E:CD
Sending on LPF/eth1/00:0F:CB:C2:0E:CD
Sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS recieved.
No working leases in persistent database - sleeping.

The contents of my interfaces config is (for eth1 only) I hard coded the rate as the bit rate listed when iwconfig is issued reports 1 Mb/s but this doesn't seem to make any difference anyway! That's another problem though I guess.
> iface eth1 inet dhcp
wireless-essid MySSID
wireless-rate 11M

---

### Post by scaryant on 2006-12-31
So I got this all working finally, I think the initial problem when trying to connect to my Open WiFi network (no WPA-PSK enabled) was I wasn't issuing a sudo with each command. 

I think this is essential to note, because if you for instance issue a *iwlist eth1 scan* I found the results returned didn't contain all the WiFi networks, when I used sudo with the same command I got a full list.

I used the following process and commands to connect to my open wifi network;
1. Determine you can see the WiFi network you intend to connect to
2. Configure the WiFi adapter with SSID, turn key off, set mode
3. Connect to WiFi Access Point

> 
sudo iwlist wlan0 scan

sudo iwconfig wlan0 essid MySSID

sudo iwconfig wlan0 key off

sudo iwconfig wlan0 mode managed

sudo dhclient

You can issue this on one line, but I did it step by step to ensure each command was accepted.

Once I had the connect to the Open network sorted out I used this [how to]("http://www.ubuntuforums.org/showthread.php?t=288753&highlight=WPA-PSK") on setting up my 3Com USB WiFi card for WPA-PSK. The procedure is very straight forward providing you have the correct drivers I suppose.

Cheers

---

