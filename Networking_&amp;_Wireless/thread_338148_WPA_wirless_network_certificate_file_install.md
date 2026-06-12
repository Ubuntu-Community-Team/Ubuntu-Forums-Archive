---
title: "WPA wirless network certificate file install?"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by neosnake on 2007-01-14
Hello everyone,

I'm new to Ubuntu and I'm now have a problem to get my wireless network working on my Asus laptop.
The machine has an intel 3945 wireless adapter and is functioning. 
The OS is Ubuntu 6.10 installed from CDrom.

The problem now  is that I can't connect to my company's wireless network. But it's working fine under Windows XP. I've read Wieman01's thread [HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc]("http://www.ubuntuforums.org/showthread.php?t=202834")  and UltraMathMan's post [HOWTO: ipw3945 connecting to a University Network (802.1x / PEAP)]("http://www.ubuntuforums.org/showthread.php?t=249654")
 and can't get it working.

The main problem is that my company is using an certificate authority file named cacert.crt( or cacert.cer or cacert.pem), under Windows I can install it by simply click it and do the next steps as prompted. But under linux I just don't know how to use the certificate file.

After messing with the /etc/network/interfaces file and wpasupplicant config file I finally got this error:
> Listening on LPF/eth1/00:13:02:02:2f:21
Sending on   LPF/eth1/00:13:02:02:2f:21
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'wlan0' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWAUTH]: No such device
WEXT auth param 7 value 0x0 - Failed to disable WPA in the driver.
ioctl[SIOCSIWAUTH]: No such device
WEXT auth param 5 value 0x0 - ioctl[SIOCSIWAUTH]: No such device
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAP]: No such device
ioctl[SIOCGIFFLAGS]: No such device
wpa_supplicant: ctrl_interface socket not found at /var/run/wpa_supplicant/wlan0...aborting!
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.


could anybody give me a hint?
Thank you!

---

### Post by katakaio on 2008-02-26
My knowledge of certificates is limited, but I may be able to help. If you have network manager installed, then loading the certificate file is very easy. I assume that your workplace has WPA Enterprise security implemented (if this isn't true, let me know). If so, then when you try to connect to the network, you have the option of loading a cert file. The following website outlines how I had to do it at work:
[http://www.cs.umn.edu/help/network/wireless-linux-wpa.php](http://www.cs.umn.edu/help/network/wireless-linux-wpa.php)
In your case, you would click on the browse button next to the CA cert file tab and navigate to the location of your cacert.pem file. If you don't get this dialog when connecting to the network, you can select "Manual configuration" from the network manager applet and choose "WPA Enterprise", which should give you the wizard pictured in the website.
Let us know if this works!

---

