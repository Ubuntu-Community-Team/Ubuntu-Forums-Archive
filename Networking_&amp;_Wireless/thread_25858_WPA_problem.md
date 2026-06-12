---
title: "WPA problem"
date: 2005-04-11
forum: Networking &amp; Wireless
---

### Post by Mr_THX on 2005-04-11
My setup is an AP with WPA-PSK.  All wifi cards have been tested and worked in windows.

I used unsecured wireless just fine but when I changed my /etc/network/interfaces file and added the wpa_supplicant file to /etc it stopped working.

I have a feeling its the interfaces file that is the problem.  The guide says that its for DHCP but I dont think thats the case.

here is my interfaces file:

```
# Used by ifup(8) and ifdown(8). See the interfaces(5) manpage or
# /usr/share/doc/ifupdown/examples for more information.

iface wlan0 inet manual
pre-up ifconfig wlan0 up
up /root/ssidselect wlan0
post-down ifconfig wlan0 down
post-down killall -q wpasupplicant

auto wlan0

```

wpa_supplicant.conf
```

# Only WPA-PSK is used. Any valid cipher combination is accepted.
network={
	ssid="MYAP"
	proto=WPA
	key_mgmt=WPA-PSK
	pairwise=CCMP TKIP
	group=CCMP TKIP WEP104 WEP40
	psk=(256bit PSK)
	priority=2
}
```

I took out my SSID and PSK of course.

---

### Post by Mr_THX on 2005-04-11
I've tried editing the interfaces file using info from the man page but I am still unable to get WPA working.

---

### Post by Mr_THX on 2005-04-12
This is the error I get when I try to initialize the connection.

```
sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -d ndiswrapper

Line 269: Invalid PSK '9CharacterASCIIPSK'.
Line 269: failed to parse psk '9CharacterASCIIPSK'.
Line 271: WPA-PSK accepted for key management, but no PSK configured.
Line 271: failed to parse network block.
Failed to read configuration file '/etc/wpa_supplicant.conf'.

```

I changed my PSK to see if that was the problem and it doesnt work with my new nine character one.

---

### Post by luca_linux on 2005-04-12
Have you typed your PSK in quotes "" ?
Are there any other configurations in your wpa_supplicant.conf or just one?
I'm asking for this, since it's better to have just one configuration.

---

### Post by Mr_THX on 2005-04-12
Ok I changed it so its in quotes now and that seemed to get passed that problem.  Now there is a new problem.  Yes, this is my only configuration file.

```
sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -d ndiswrapper
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'default'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=4
eapol_version=1
ap_scan=1
fast_reauth=1
Priority group 2
   id=0 ssid='MYSSID'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Own MAC address: MYMACADDRESS
wpa_driver_hostap_set_wpa: enabled=1
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
Failed to enable WPA in the driver.
wpa_driver_hostap_set_wpa: enabled=0
ioctl[PRISM2_IOCTL_HOSTAPD]: No such device
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
Failed to disable WPA in the driver.
wpa_driver_hostap_set_drop_unencrypted: enabled=0
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
wpa_driver_hostap_set_countermeasures: enabled=0
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
rmdir[ctrl_interface]: No such file or directory
```

---

### Post by luca_linux on 2005-04-13
Are you sure that your device is interfaced as wlan0? And what wireless card have you got?

---

### Post by Mr_THX on 2005-04-13
Its a linksys WMP54g v4.  I am going to use the rt2500 drivers though so I can cut ndiswrapper and wpa_supplicant out of the mix.  Having troubles with them too though.

---

### Post by Yaniv on 2005-04-24
There's a guide for the rt2500 native drivers here: [http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo](http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo)

---

