---
title: "WPA on WPC54G v2 (Feisty)"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by MartenH on 2007-04-25
Hello,

I've been looking this forum and internet all over without finding a working solution to my problem. The thread of supported cars states that it should be supported out of the box.. but I'm not sure this goes for WPA as well? Should NetworkManager be able to do this for me?

My card shows up OK and presumably work with an open network but i am only able to choose WEP encryption. There are no WPA options. 

So, what I'm looking for is someone who can help me on how to correct my system for it to work with WPA. any and all help is greatly appreciated!

Details:
Network is using WPA Personal TKIP PSK and known to be woking
Card is Linksys WPC54G v2 ACX111 and known to be working
apt-get install wpasupplicant  and apt-get install ndiswrapper-common states both are installed with latest version.
NetworkMonitor is installed but as previously stated doesn't show the WPA option.

sudo iwconfig gives:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:""  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Encryption key:off
          Power Management:off
          Link Quality=36/100  Signal level=11/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:8  Invalid misc:0   Missed beacon:0


```

lspci gives:
```

00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:03.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
02:04.0 Communication controller: Agere Systems LT WinModem (rev 02)
02:05.0 CardBus bridge: Texas Instruments PCI1420
02:05.1 CardBus bridge: Texas Instruments PCI1420
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller (rev 41)
07:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

```

/etc/network/interfaces looks like this:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

/etc/wpasupplicant.conf looks like this:
```

#allow frontend (e.g., wpa_cli) to be used by all users in 'wheel' group
ctrl_interface=/var/run/wpa_supplicant
#
# home network; allow all valid ciphers
network={
	ssid="holi"
	scan_ssid=1
	pairwise=TKIP
	group=TKIP
	key_mgmt=WPA-PSK
	psk=<hex key>
}

```

Running sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -d
```

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'default' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Priority group 0
   id=0 ssid='holi'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=21 WE(source)=9 enc_capa=0x0
  capabilities: key_mgmt 0x0 enc 0x3
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:13:10:2f:01:fc
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
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:00:00:00:00:00 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
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
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=4):
     68 6f 6c 69                                       holi            
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 168 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:13:10:94:f7:16 ssid='holi' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
No APs found - clear blacklist and try again
Removed BSSID 00:00:00:00:00:00 from blacklist (clear)
Selecting BSS from priority group 0
0: 00:13:10:94:f7:16 ssid='holi' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:00:00:00:00:00 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
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
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
BSSID 00:00:00:00:00:00 blacklist count incremented to 2
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
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
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Scan timeout - try to get results
Received 445 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
0: 00:13:10:94:f7:16 ssid='holi' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 00:11:50:9a:d7:4a ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:09:5b:4f:5b:fc ssid='NETGEAR' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
No APs found - clear blacklist and try again
Removed BSSID 00:00:00:00:00:00 from blacklist (clear)
Selecting BSS from priority group 0
0: 00:13:10:94:f7:16 ssid='holi' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 00:11:50:9a:d7:4a ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:09:5b:4f:5b:fc ssid='NETGEAR' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
No suitable AP found.
Setting scan request: 5 sec 0 usec
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_hostap_set_wpa: enabled=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
Failed to disable WPA in the driver.
wpa_driver_hostap_set_drop_unencrypted: enabled=0
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
wpa_driver_hostap_set_countermeasures: enabled=0
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
No keys have been configured - skip key clearing
WEXT: Operstate: linkmode=0, operstate=6
Cancelling scan request

```

I find two things to suspect, but you might be able to spot more? One is that it's using PRISM drivers? And the second that it states *Driver does not support WPA.*

Again, **ANY** help is appreciated!
Let me know if you need more information!

BR,
MartenH

---

### Post by ruletrak on 2007-04-26
Thanks for such a well done description of the problem.  I have the same card and the same problem.  I'll watch this thread and hope to see some help....

Have a great day,
Rusty

---

### Post by MartenH on 2007-04-27
bump

---

### Post by ruletrak on 2007-04-28
Hi Marten,  I haven't been able to resolve my problem yet but just wanted to let you know that I'm watching the thread and hope we get some help on this one.  I've started the process to go back to 6.10 and see if I can get it working by using the old manual methods but haven't been able to complete that yet.  There's another thread on here titled:

Fiesty 7.04 wireless, working for you or not ? 

that has some ideas to try.  The wicd mentioned in there might also be something to try.  Good Luck....

---

### Post by Lapith on 2007-05-31
I'm also running into this problem with the WPC54G v2 in Feisty. I can confirm that the card is working with an open network; with WPA in place I put in the passphrase but do not get access to the internet; a minute later, I'm asked for the passphrase again. If somebody finds the solution, please post a link.

---

### Post by Lapith on 2007-05-31
This site purports to show how to get WPA to work, but it doesn't seem to address TKIP shared passphrases, as it only discusses hexkey generation...

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by bromix on 2007-05-31
Try this post and see if it helps.   [http://ubuntuforums.org/showthread.php?p=2718776](http://ubuntuforums.org/showthread.php?p=2718776)

---

### Post by enrico_ on 2007-06-25
> **Lapith said:**
> This site purports to show how to get WPA to work, but it doesn't seem to address TKIP shared passphrases, as it only discusses hexkey generation...

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

This worked for me! :-)
I am running Feisty (7.04)

Following the instructions it is very easy to convert a shared passphrase to hex format.
I hope this helps..

Thanks
Enrico

---

### Post by kevdog on 2007-06-25
Hmm interesting, particularly with the prism statement.

What does the following produce?
ndiswrapper -v
ndiswrapper -l
iwlist wlan0 scanning
sudo modproble -l | grep ndiswrapper


Can you post /etc/modprobe.d/blacklist?
Where did you get the driver for your card?

---

### Post by ricflomag on 2007-07-16
> **bromix said:**
> Try this post and see if it helps.   [http://ubuntuforums.org/showthread.php?p=2718776](http://ubuntuforums.org/showthread.php?p=2718776)

Edit : This post is rather off topic. It only describes how i've got the WPC54G v2 to work on feisty, but only with open and WEP networks. I put it here because of my ignorance of wireless protocols and because it was the only thread i could find dedicated to the version 2 of the WPC54G... 

For my WPC54G v2, this post is the solution, though it can be even simpler: i did not have to compile ndiswrapper from source, i just installed it from the repositories. Here are the steps:
[LIST]i downloaded the driver from linksys.com:
[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859842300&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4230037314B251&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859842300&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4230037314B251&displaypage=download#versiondetail)
and extracted it to my Dektop.
[/LIST]
[LIST]then i opened a terminal and:
[FONT="Courier New"]# remove any previous ndiswrapper settings
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils-1.9
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
# install ndiswrapper directly from the repositories
sudo apt-get install ndiswrapper-utils-1.9
# remove acx module
sudo rmmod acx
# install driver
cd Desktop/WPC54Gv2_40826
sudo ndiswrapper -i LSTINDS.INF
sudo modprobe ndiswrapper[/FONT]

Network manager should now show the available wireless networks and be able to connect.
[/LIST]
To have things done at each boot, i edited two files:
[LIST]
[FONT="Courier New"]sudo gedit /etc/modprobe.d/blacklist[/FONT]

at the end, i put a new line:
[FONT="Courier New"]blacklist acx[/FONT]

This prevents acx module to load and conflict with ndiswrapper
[/LIST]
[LIST]
[FONT="Courier New"]sudo gedit /etc/modules[/FONT]

at the end i put a new line:
[FONT="Courier New"]ndiswrapper[/FONT]

this loads ndiswrapper automatically on boot
[/LIST]

---

### Post by MartenH on 2007-07-16
ricflomag: This works for WPA encryption?

---

### Post by ricflomag on 2007-07-16
ups, sorry, it works with WEP encryption...

---

### Post by MartenH on 2007-07-16
Lapith, bromix and kevdog, I'll try to get around to trying your suggestions and getting the requested details. Have been tied up with work for quite some time. 

ricflomag, wep worked out of the box for me.

---

