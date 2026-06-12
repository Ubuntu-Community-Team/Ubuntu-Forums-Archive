---
title: "WPA Configuration"
date: 2007-01-15
forum: Networking &amp; Wireless
---

### Post by acheton on 2007-01-15
Hi there,

After following some instructions from the Ubuntu wiki I've now got my driver for my wireless card set up correctly. Running an [b]iwconfig scan[b] produces a list of nearby wireless networks including my own. However despite following the WPA thread which is stickied at the top of this forum, I've been unable to connect. The salient section of /etc/network/interfaces is:

auto wlan0
iface wlan0 inet static
address 192.168.0.2
netmask 255.255.255.0
network 192.168.0.1
broadcast 192.168.0.255
gateway 192.168.0.1
dns-nameservers 212.159.6.9
wpa-driver wext
wpa-conf managed
wpa-ssid NETGEAR
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <my key here>

However ubuntu shows no signs of being able to connect to the wireless network. When I restart the networking I get the following output:

Listening on LPF/eth0/00:12:3f:9f:12:e9
Sending on   LPF/eth0/00:12:3f:9f:12:e9
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
SIOCDELRT: No such process
wpa_supplicant: unknown or stale ctrl_interface socket located at /var/run/wpa_supplicant/wlan0...aborting!
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416

Does anyone have any ideas about where I may be going wrong?

thanks,


ach

---

### Post by spd106 on 2007-01-15
Try making a wpa_supplicant.conf file and start it directly from a terminal. That way you can check for error messages. Have a look at this wiki page for some more details [https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto)

---

### Post by acheton on 2007-01-15
Thanks for the reply. I've followed the instructions on the wiki to the best of my ability. I've set up a wpa_supplicant.conf file. When I get to the section "Testing the Configuration" I run the following:

**sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dwext -w**

The output is as follows:

Trying to associate with 00:09:5b:ce:ae:b0 (SSID='NETGEAR' freq=2462 MHz)
ioctl[SIOCSIWFREQ]: Invalid argument
Association request to the driver failed
Associated with 00:09:5b:ce:ae:b0
WPA: 4-Way Handshake failed - pre-shared key may be incorrect
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:09:5b:ce:ae:b0 (SSID='NETGEAR' freq=2462 MHz)

I'm not sure how to interpret it although the problem appears to be with the line:

ioctl[SIOCSIWFREQ]: Invalid argument

But I've no idea what this means. Any ideas?

Thanks,


Ach

---

### Post by acheton on 2007-01-15
I've got some more detailed output if this helps:

**sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dwext -w -dd**
[INDENT]Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=7):
     4e 45 54 47 45 41 52                              NETGEAR         
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='NETGEAR'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=20 WE(source)=13 enc_capa=0x0
  capabilities: key_mgmt 0x0 enc 0x3
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:17:3f:4e:75:9f
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:00:00:00:00:00 into blacklist
State: DISCONNECTED -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
Wireless event: cmd=0x8b19 len=8
Received 919 bytes of scan results (4 BSSes)
Scan results: 4
Selecting BSS from priority group 0
0: 00:09:5b:ce:ae:b0 ssid='NETGEAR' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:09:5b:ce:ae:b0 (SSID='NETGEAR' freq=2462 MHz)
Cancelling scan request
[/INDENT]

I'd really appreciate any advice.

thanks again.

ach

---

