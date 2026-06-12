---
title: "[SOLVED] problem with NETGEAR WG111v2"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by shanem on 2007-09-22
Hi,

I have just installed Ubunto 7.04 "Feisty Fawn" on my Dell Inspiron 8000 laptop which has a NETGEAR WG111v2 54Mbps Wireless USB 2.0 Adapter. I see the package wpasupplicant has installed version: 0.5.7-0ubuntu2

The adapter works fine on the same laptop under windows 2000. The router is configured to use security encryption (WPA-PSK) TKIP and since the router is not mine, I can't change it.

According to iwconfig (see below), the correct network "@Home54960" is detected by the adapter but it can't connect. But when I ```
sudo /etc/init.d/networking restart
```, I see “wmaster0: unknown hardware address type 801” amongst the error messages (see below)

Can anyone see what the problem is?

Dell

sss@sss-laptop:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"@Home54960"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


sss@sss-laptop:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                          
There is already a pid file /var/run/dhclient.eth0.pid with pid 4895
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:20:e0:67:86:de
Sending on   LPF/eth0/00:20:e0:67:86:de
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.201 port 67
RTNETLINK answers: No such process



sss@sss-laptop:~$ wpa_supplicant -c/etc/wpa_supplicant.conf -iwlan0 -d
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'default' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Priority group 0
   id=0 ssid='@Home54960'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: Operation not permitted
ioctl[SIOCSIWMODE]: Operation not permitted
Could not configure driver to use managed mode
SIOCSIFFLAGS: Permission denied
Could not set interface 'wlan0' UP
SIOCGIWRANGE: WE(compiled)=21 WE(source)=14 enc_capa=0x0
  capabilities: key_mgmt 0x0 enc 0x3
WEXT: Operstate: linkmode=1, operstate=5
socket(PF_PACKET): Operation not permitted
Failed to add interface wlan0
State: DISCONNECTED -> DISCONNECTED
Segmentation fault (core dumped)


sss@sss-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82557/8/9 [Ethernet Pro 100]
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@08:04.0
       logical name: eth0
       version: 08
       serial: 00:20:e0:67:86:de
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A latency=32 maxlatency=56 mingnt=8 multicast=yes
       resources: iomemory:f8fff000-f8ffffff ioport:ecc0-ecff iomemory:f8e00000-f8efffff irq:11
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:6c:ae:53:a3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g




sss@sss-laptop:~$ sudo wpa_supplicant -c/etc/wpa_supplicant.conf -iwlan0 -d
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'default' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Priority group 0
   id=0 ssid='@Home54960'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=21 WE(source)=14 enc_capa=0x0
  capabilities: key_mgmt 0x0 enc 0x3
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:14:6c:ae:53:a3
wpa_driver_hostap_set_wpa: enabled=1
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
Driver does not support WPA.
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_countermeasures: enabled=0
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
wpa_driver_hostap_set_drop_unencrypted: enabled=1
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=8
Ignore event for foreign ifindex 3
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 169 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:14:6c:a6:83:a6 ssid='@Home54960' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:14:6c:a6:83:a6 (SSID='@Home54960' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_hostap_set_drop_unencrypted: enabled=1
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_hostap_associate

---

### Post by deroldj on 2007-09-22
As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this option through Windows' device manager.

---

### Post by Jose Catre-Vandis on 2007-09-22
Check here for answers

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

this should sort out your security issues.

If you need to find out the wireless key (hash) then you'll have to go back into windows and download a little program called (believe it or not) wireless keyview (search on those two words)

The WG111v2 should work out of the box on Feisty, ensure it is plugged in on boot though (it uses the r8187 driver) You can always use ndiswrapper and your windows driver instead (this give you the blue light back!)

Search for a thread by "phossal" which sorts out connection using this adapter

---

### Post by shanem on 2007-09-25
Hi,

I finally got connected. Apart for the minor annoyance of having to manually run sudo /etc/init.d/networking restart after each reboot of Ubunto, it works fine. Contrary to what I have read in other posts, I could not connect to the router using WPA encryption using the standard kernel module rtl8187, but it does work with ndiswrapper and the Netgear 1.3 windows 98 driver. Nor I could I connect using the network manager applet, hence the additions to /etc/network/interfaces below. Here is how I did it -


Installation of WG111v2 Ubunto 7.04 "Feisty Fawn"

Check the following -

sss@sss-laptop:~$ lsusb | grep NetGear
Bus 001 Device 002: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)

download ndiswrapper

[http://packages.ubuntu.com/feisty/misc/ndiswrapper-common](http://packages.ubuntu.com/feisty/misc/ndiswrapper-common)
[http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9)
[http://packages.ubuntu.com/feisty/net/ndisgtk](http://packages.ubuntu.com/feisty/net/ndisgtk)

and install 

  sudo dpkg -i ndiswrapper-common_*.deb
  sudo dpkg -i ndiswrapper-utils*.deb
  sudo dpkg -i --force-depends ndisgtk_*.deb

and the following to /etc/modprobe.d/blacklist

#wg111v2 conflicting drivers
# blacklist r8187 should already be in the list
blacklist islsm_pci
blacklist islsm
blacklist islsm_usb
blacklist prism2_usb
blacklist rtl8187
blacklist r8187b

Download the Netgear 1.3 driver wg111v2_1_3_0.zip from [http://kbserver.netgear.com/release_notes/D102843.asp](http://kbserver.netgear.com/release_notes/D102843.asp) and unzip


sudo ndiswrapper -i [path to driver]/win98/net111v2.inf

check

sss@sss-laptop:~$ ndiswrapper -l
net111v2 : driver installed
        device (0846:6A00) present (alternate driver: rtl8187)


  sudo depmod -a
  sudo modprobe ndiswrapper

check for error messages:

tail /var/log/messages

add the following /etc/network/interfaces,

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf

convert your WPA ASCII password using the following command

wpa_passphrase 'your_essid' 'your_ascii_key'

create /etc/wpa_supplicant.conf

# WPA-PSK/TKIP

ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="your_essid"
	key_mgmt=WPA-PSK
	proto=WPA
#	pairwise=TKIP
#	group=TKIP
	#psk=" your_ascii_key "
        psk=[paste the your hex key generated by wpa_passphrase above]
}

Automatic loading at start-up

sudo ndiswrapper -m

gksudo gedit /etc/modules

and add the word "ndiswrapper" to the end of this file and save it.

reboot and run 

sudo /etc/init.d/networking restart

---

### Post by coolbrook on 2007-12-12
Just wanted to say thanks for pointing me to this version of the driver.  I had this adapter working before on another version and then I did something to stop it form working, but this one seems to be the best since I can see network activity on the LED.

---

