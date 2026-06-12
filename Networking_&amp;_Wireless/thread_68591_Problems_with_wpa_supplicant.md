---
title: "Problems with wpa_supplicant"
date: 2005-09-23
forum: Networking &amp; Wireless
---

### Post by keithce on 2005-09-23
I am new to Ubuntu, but I have tried several times to switch over from windows but this time I am determined.

I have followed the HOWTO: Guides to install ndiswrapper which was successful except for not being able to have it automatically load on startup.

I have also followed the HOWTO: Automated WPA Encryption with ndiswrapper drivers however it is after making the conf file that I have run into trouble.

Here is my conf file:
```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1

network={
	ssid="Villanova"
#	mode=0
	key_mgmt=IEEE8021X
	eap=TTLS
	identity="username"
	password="password"
	anonymous_identity="anonymous"
	phase2="autheap=PAP"
#	ca_cert2:"/usr/share/ca-certificates/mozilla/Equifax_Secure_CA.crt"
}
```

And this is what happens when I run this command:
```
keith@kellio03:~$ sudo ifconfig wlan0 up && /usr/sbin/wpa_supplicant -w -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Line: 7 - start of a new network block
ssid - hexdump_ascii(len=9):
     56 69 6c 6c 61 6e 6f 76 61                        Villanova
key_mgmt: 0x8
eap methods - hexdump(len=2): 15 00
identity - hexdump_ascii(len=8):
     6b 65 6c 6c 69 6f 30 33                           kellio03
password - hexdump_ascii(len=11): [REMOVED]
Priority group 0
   id=0 ssid='Villanova'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWMODE]: Operation not permitted
Could not configure driver to use managed mode
SIOCSIFFLAGS: Permission denied
Could not set interface 'wlan0' UP
socket(PF_PACKET, SOCK_RAW): Operation not permitted
Waiting for interface..
```

I have tried searching and reading through other people's threads but I am absolutely baffled and have been trying to get this to install all this for weeks.

Please Help me!

---

### Post by firecat53 on 2005-09-23
Try adding 'sudo' in front of your wpa_supplicant command.  That's probably why you're getting all the 'operation not permitted' messages. Ifconfig, iwconfig, dhclient and wpa_supplicant all need to be run as root. Well, at least on my machine they do  :)  Once you get it working don't forget to add the -B flag to daemonize it.

If it works....easy fix!!

Scott

---

### Post by keithce on 2005-09-26
Actually yes, that did fix it....only it lead to more problems :(

Here is the output that I get now:

```
root@kellio03:/home/keith # ifconfig wlan0 up && /usr/sbin/wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf && dhclient wlan0Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:90:96:b0:c7:a9
Sending on   LPF/wlan0/00:90:96:b0:c7:a9
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

```
root@kellio03:/home/keith #  dhclient -r wlan0 && ifconfig wlan0 down && killall wpa_supplicant
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:90:96:b0:c7:a9
Sending on   LPF/wlan0/00:90:96:b0:c7:a9
Sending on   Socket/fallback
```


```
root@kellio03:/home/keith # ifconfig wlan0 up && /usr/sbin/wpa_supplicant -w -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Line: 7 - start of a new network block
ssid - hexdump_ascii(len=9):
     56 69 6c 6c 61 6e 6f 76 61                        Villanova
mode=0 (0x0)
key_mgmt: 0x8
auth_alg: 0x1
eap methods - hexdump(len=2): 15 00
identity - hexdump_ascii(len=8):
     6b 65 6c 6c 69 6f 30 33                           kellio03
password - hexdump_ascii(len=11): [REMOVED]
anonymous_identity - hexdump_ascii(len=9):
     61 6e 6f 6e 79 6d 6f 75 73                        anonymous
ca_cert2 - hexdump_ascii(len=22):
     2f 68 6f 6d 65 2f 6b 65 69 74 68 2f 63 61 63 65   /home/keith/cace
     72 74 2e 70 65 6d                                 rt.pem
Priority group 0
   id=0 ssid='Villanova'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Own MAC address: 00:90:96:b0:c7:a9
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
Starting AP scan (broadcast SSID)
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Scan timeout - try to get results
Received 1148 bytes of scan results (7 BSSes)
Scan results: 7
Selecting BSS from priority group 0
0: 00:0c:85:ba:9f:b6 ssid='Villanova' wpa_ie_len=0 rsn_ie_len=0
   skip - no WPA/RSN IE
1: 00:0c:ce:1d:12:32 ssid='Villanova' wpa_ie_len=0 rsn_ie_len=0
   skip - no WPA/RSN IE
2: 00:0c:85:ea:d8:0f ssid='Villanova' wpa_ie_len=0 rsn_ie_len=0
   skip - no WPA/RSN IE
3: 00:0c:85:af:54:49 ssid='Villanova' wpa_ie_len=0 rsn_ie_len=0
   skip - no WPA/RSN IE
4: 0a:68:79:ac:d0:0c ssid='college2' wpa_ie_len=0 rsn_ie_len=0
   skip - no WPA/RSN IE
5: 02:c7:ae:06:38:ce ssid='college2' wpa_ie_len=0 rsn_ie_len=0
   skip - no WPA/RSN IE
6: 00:0c:ce:1d:12:04 ssid='Villanova' wpa_ie_len=0 rsn_ie_len=0
   skip - no WPA/RSN IE
   selected non-WPA AP 00:0c:85:ba:9f:b6 ssid='Villanova'
Trying to associate with 00:0c:85:ba:9f:b6 (SSID='Villanova' freq=5320 MHz)
Cancelling scan request
Automatic auth_alg selection: 0x1
Overriding auth_alg selection: 0x1
No keys have been configured - skip key clearing
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - portControl=Auto
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Signal 2 received - terminating
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
```

---

### Post by firecat53 on 2005-09-27
Well, you're starting to get out of my depth!  I only have used the WPA-PSK, so I'm not familiar with the authentication method you're using.  However, in general I had to do two things to make my WPA work (keep in mind this was with Madwifi drivers!)  

1. I had to compile the most recent version of the driver and the wpa_supplicant before I could get anything to work. I also had to use a static IP address as opposed to dhcp.

2. Now, on the flip side, I got a different machine working with ndiswrapper and wpa-psk using the existing driver/wpa_supplicant. Go figure!!

3. Have you checked the wpa_supplicant mailing list archives or forums?

Good luck!

Scott

---

