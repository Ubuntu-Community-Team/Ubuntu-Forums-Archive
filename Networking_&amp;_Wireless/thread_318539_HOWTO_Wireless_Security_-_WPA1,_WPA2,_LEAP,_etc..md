---
title: "HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc."
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by wieman01 on 2006-06-24
This guide was tested with **Dapper Drake**, **Feisty Fawn**, **Gutsy Gibbon**, and **Hardy Heron**. 
--
Since it appears that very few people take wireless security seriously, I'd like to come up with my first HOWTO and explain how I was able to configure a secure home network using WPA2, the latest encryption & authentication standard. There are also other types of configuration (WPA1, mixed mode, LEAP, PEAP, DHCP, etc.) shown in the appendix. Feedback is much appreciated.

_**Common stumbling blocks - Make sure that:**_
1. Ethernet cable is unplugged.
2. No firewall & configuration tool is running (e.g. Firestarter).
3. MAC filtering is disabled.
4. NetworkManager, Wifi-Radar & similar wireless configuration tools are disabled/turned off and not in use.
5.[COLOR="Red"] Some cards/drivers (e.g. Madwifi) do not support WPA2 (AES). Try WPA1 (TKIP) if WPA2 secured connections fail.[/COLOR]
6.[COLOR="Red"] **RTxxx (Ralink)** drivers do not support this approach. Either install "ndiswrapper" replacing Serialmonkey's driver or visit this [site]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=21546&sid=c5e02ed97dde07681fb564639e9f50c5").[/COLOR]
7. Turn off "roaming" if you repeatedly fail to establish a connection.

**_My Requirements:_**
1. WPA2 / RSN
2. AES / CCMP
3. Hidden ESSID (no broadcast)
4. Static IP (because I use port forwarding & firewall, etc.)
5. Pre-shared key (no EAP)

If you want to know more about WPA / RSN & 802.11i security specification, I recommend [this site]("http://en.wikipedia.org/wiki/IEEE_802.11i").

**_Now let's get started:_**
0. Install "wpa-supplicant":
> sudo apt-get install wpasupplicant
1. Verify that your network device ("wlan0"?) is working & your wireless network is detected:
> iwconfig
> iwlist scan
Your network device & wireless network should appear here.

2. Open "/etc/network/interfaces":
> sudo gedit /etc/network/interfaces
The content should look similar to this:
> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
3. Now replace the last 2 lines with the following using your own network settings (the sequence in which the lines appear is crucial):
> auto wlan0
iface wlan0 inet static
[COLOR="DarkGreen"][I]address 192.168.168.40
gateway 192.168.168.230	
dns-nameservers 192.168.168.230
netmask 255.255.255.0[/I][/COLOR]
wpa-driver wext
wpa-ssid [COLOR="Red"]<your_essid>[/COLOR]
[COLOR="Blue"]wpa-ap-scan 2[/COLOR]
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk [COLOR="Red"]<your_hex_key>[/COLOR] [COLOR="Blue"][IMPORTANT: See "WPA-PSK key generation"][/COLOR]
[LIST]
[*]**_auto wlan0:_**
Your network interface (e.g. wlan0, eth1, rausb0, ra0, etc.).
[/LIST]
[LIST]
[*]**_iface wlan0 inet static:_**
Self-explanatory... I am using a Static IP instead of DHCP. "iface wlan0" must correspond to your network interface (see above).
[/LIST]
[LIST]
[*]**_address, netmask, [..], dns-nameservers:_**
Also self-explanatory... Be aware that "broadcast" needs to end with ".255" for negotiation with the router. These lines need to be according to your own (static) network settings. For DHCP see further below.
[/LIST]
[LIST]
[*]**_wpa-driver:_**
That's the wpa-driver for your card ('wext' is a generic driver that is applicable when using "ndiswrapper"). Leave it as it is. Other drivers are:
> hostap = Host AP driver (Intersil Prism2/2.5/3)
atmel = ATMEL AT76C5XXx (USB, PCMCIA)
wext = Linux wireless extensions (generic)
madwifi =  Atheros
wired = wpa_supplicant wired Ethernet driver

[/LIST]
[LIST]
[*]**_wpa-ssid:_**
Your network's ESSID (no quotes "").
[/LIST]
[LIST]
[*]**_wpa-ap-scan:_**
"1" = Broadcast of ESSID.
"2" = Hidden broadcast of ESSID.
[/LIST]
[LIST]
[*]**_wpa-proto:_**
"RSN" = WPA(2)
"WPA" = WPA(1)
[/LIST]
[LIST]
[*]**_wpa-pairwise & wpa-group:_**
"CCMP" = AES cipher as part of WPA(2) standard.
"TKIP" = TKIP cipher as part of WPA(1) standard.
[/LIST]
[LIST]
[*]**_wpa-key-mgmt:_**
"WPA-PSK" = Authentication via pre-shared key (see 'key generation' further below).
"WPA-EAP" = Authentication via enterprise authentication server.
[/LIST]
[COLOR="Red"]_**VERY IMPORTANT ("WPA PSK Key Generation"):**_[/COLOR]
Now convert your WPA ASCII password using the following command:
> wpa_passphrase <your_essid> <your_ascii_key>
Resulting in an output like...
> network={
ssid="test"
#psk="12345678"
psk=fe727aa8b64ac9b3f54c72432da14faed933ea511ecab15bbc6c52e7522f709a
}
Copy the "hex_key" (next to "psk=...") and replace <your_hex_key> in the "interfaces" files with it. Then save the file and restart your network:
> sudo /etc/init.d/networking restart
You should be connecting to your router now... However, I figured that a restart is sometimes necessary so that's what I usually do (I know this sounds a bit clumsy - see post #2 for startup script). 


*****************************Revoking read-permission from 'others'*********************************
> sudo chmod o=-r /etc/network/interfaces
*****************************Revoking read-permission from 'others'*********************************

*****************************Sample configuration WPA2 & DHCP, ESSID broadcast enabled***************
> auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid [COLOR="Red"]<your_essid>[/COLOR]
[COLOR="Blue"]wpa-ap-scan 1[/COLOR]
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk [COLOR="Red"]<your_hex_key>[/COLOR] [COLOR="Blue"][IMPORTANT: See "WPA-PSK key generation"][/COLOR]
*****************************Sample configuration WPA2 & DHCP, ESSID broadcast enabled***************

*****************************Sample configuration WPA1 & DHCP, ESSID broadcast enabled***************
> auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid [COLOR="Red"]<your_essid>[/COLOR]
[COLOR="Blue"]wpa-ap-scan 1[/COLOR]
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk [COLOR="Red"]<your_hex_key>[/COLOR] [COLOR="Blue"][IMPORTANT: See "WPA-PSK key generation"][/COLOR]
*****************************Sample configuration WPA1 & DHCP, ESSID broadcast enabled***************

****************************Sample configuration mixed mode (WPA1, WPA2) & DHCP, ESSID broadcast*****
> auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid [COLOR="Red"]<your_essid>[/COLOR]
[COLOR="Blue"]wpa-ap-scan 1[/COLOR]
wpa-proto WPA RSN
wpa-pairwise TKIP CCMP
wpa-group TKIP CCMP
wpa-key-mgmt WPA-PSK
wpa-psk [COLOR="Red"]<your_hex_key>[/COLOR] [COLOR="Blue"][IMPORTANT: See "WPA-PSK key generation"][/COLOR]
****************************Sample configuration mixed mode (WPA1, WPA2) & DHCP, ESSID broadcast*****

****************************Sample conf. LEAP, WEP, DHCP, ESSID broadcast***************************
> auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid [COLOR="Red"]<your_essid>[/COLOR]
[COLOR="Blue"]wpa-ap-scan 1[/COLOR]
wpa-eap LEAP
wpa-key-mgmt IEEE8021X
wpa-identity [COLOR="Red"]<your_user_name>[/COLOR]
wpa-password [COLOR="Red"]<your_password>[/COLOR]
****************************Sample conf. LEAP, WEP, DHCP, ESSID broadcast***************************

****************************Sample conf. PEAP, AES, DHCP, ESSID broadcast***************************
> auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid [COLOR="Red"]<your_essid>[/COLOR]
[COLOR="Blue"]wpa-ap-scan 1[/COLOR]
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-eap PEAP
wpa-key-mgmt WPA-EAP
wpa-identity [COLOR="Red"]<your_identity>[/COLOR]
wpa-password [COLOR="Red"]<your_password>[/COLOR]
****************************Sample conf. PEAP, AES, DHCP, ESSID broadcast***************************

*****************************Sample conf. TTLS, WEP, DHCP, ESSID broadcast**************************
> auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid [COLOR="Red"]<your_essid>[/COLOR]
wpa-ap-scan 1
wpa-eap TTLS
wpa-key-mgmt IEEE8021X
wpa-anonymous-identity [COLOR="Red"]<anonymous_identity>[/COLOR]
wpa-identity [COLOR="Red"]<your_identity>[/COLOR]
wpa-password [COLOR="Red"]<your_password>[/COLOR]
wpa-phase2 [COLOR="Blue"]auth=PAP[/COLOR] [Also: CHAP, MSCHAP, MSCHAPV2]
*****************************Sample conf. TTLS, WEP, DHCP, ESSID broadcast**************************

*******************************[COLOR="Red"]NOT TESTED:[/COLOR]** Sample conf. EAP-FAST, WPA1/WPA2, DHCP, ESSID broadcast****
> auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid [COLOR="Red"]<your_essid>[/COLOR]
[COLOR="Blue"]wpa-ap-scan 1[/COLOR]
wpa-proto RSN WPA
wpa-pairwise CCMP TKIP
wpa-group CCMP TKIP
wpa-key-mgmt WPA-EAP
wpa-eap FAST
wpa-identity [COLOR="Red"]<your_user_name>[/COLOR]
wpa-password [COLOR="Red"]<your_password>[/COLOR]
wpa-phase1 [COLOR="Blue"]fast_provisioning=1[/COLOR]
wpa-pac-file [COLOR="Red"]/path/to/eap-pac-file[/COLOR]
*******************************[COLOR="Red"]NOT TESTED:[/COLOR]** Sample conf. EAP-FAST, WPA1/WPA2, DHCP, ESSID broadcast****

*****************************Tested adapters***************************************************
> 1. Linksys WUSB54G V4 (ndiswrapper; wpa-driver = wext)
2. Intel IPW2200 (Linux driver; wpa-driver = wext)
3. Linksys WPC54G (ndiswrapper; wpa-driver = wext)
4. D-Link WNA-2330 (Linux driver; wpa-driver = madwifi)
5. Linksys WMP54G V2 (ndiswrapper; wpa-driver = wext)
6. D-Link WDA-2320 (Linux driver; wpa-driver = madwifi)
7. Netgear WPN311 (Linux driver; wpa-driver = wext)
8. Netgear WG511v2 (ndiswrapper; wpa-driver = wext)
*****************************Tested adapters***************************************************

*****************************Post this if you are stumped******************************************
> # route
# iwconfig
# sudo iwlist scan
# sudo lshw -C network
# sudo cat /etc/network/interfaces
# sudo ifdown -v [COLOR="Red"]<your_interface>[/COLOR]
# sudo ifup -v [COLOR="Red"]<your_interface>[/COLOR]

*****************************Post this if you are stumped******************************************

*****************************Other useful commands*********************************************
> 
# Ubuntu version & kernel >> **uname -a **
# Root file access >> **alt F2 then 'gksudo nautilus' in cli**
# Get IP Address or Renew >> **sudo dhclient wlan0** [or whatever your wl adapter is]
# Get wireless info >> **iwconfig**
# Get AP info >> **iwlist scan**
# Get wireless info >> **iwlist** (lots of options will list)
# Routes if wlan0 working >> **route**
# DNS resolving via eth1 >> **cat /etc/resolv.conf**
# List devices/modules >> **lspci, lsusb, lshw, lsmod**
# Restart network >> **sudo /etc/init.d/networking restart**
# Boot messages >> **dmesg**
# Kill NWM >> **sudo killall NetworkManager **
# Events from your wl >> **iwevent **
# Restart all daemons >> **sudo /etc/init.d/dbus restart **
# Restart network >> **sudo /etc/init.d/networking restart**
*****************************Other useful commands*********************************************

_**CHANGE LOG:**_
08/11/2006: Added section "Post this if you are stumped" (SquibT).
08/11/2006: Added sample configuration for WPA2 with DHCP & ESSID broadcast (Wieman01).
08/11/2006: Added sample configuration for WPA1 with DHCP & ESSID broadcast (Wieman01).
08/11/2006: Added section "Tested adapters" (Wieman01).
08/11/2006: Added section "Useful commands" (SquibT).
08/11/2006: Added section "Common stumbling blocks" (Wieman01).
08/11/2006: Changed section "wpa-driver" and added new drivers (Wieman01).
08/11/2006: Added section "Revoking read-permission from group 'others'" (Wieman01).
09/11/2006: Minor changes in layout (Wieman01).
09/11/2006: Added sample configuration for mixed mode (WPA1, WPA2) with DHCP & ESSID broadcast (Wieman01).
09/11/2006: Added experimental sample configuration for LEAP with WEP, DHCP & ESSID broadcast (Wieman01).
09/11/2006: Added section "Install wpa-supplicant" (Wieman01).
10/11/2006: Added experimental sample configuration for TTLS with WEP, DHCP & ESSID broadcast (Wieman01).
15/11/2006: Added experimental sample configuration for EAP-FAST with WPA1/WPA2, DHCP & ESSID broadcast (Wieman01).
04/12/2006: Changed "wpa_passphrase" section & added quotes ("") for encryption keys containing special characters (Wieman01).
04/01/2007: Added various security options (Wieman01).
15/01/2007: Added valid script for EAP-LEAP (Wieman01).
31/01/2007: Added valid script for EAP-PEAP (Wieman01).
21/04/2007: Removed "wpa-conf" for Edgy Eft (Wieman01).
22/04/2007: Simplified section concerning static network settings (Wieman01).
02/05/2007: Added note concerning WPA2 support for Atheros cards & drivers (Wieman01).
13/05/2007: Added note on Ralink drivers (Wieman01).
15/04/2008: Tested with Hardy Heron (Wieman01).

---

### Post by frodon on 2006-12-14
[SIZE="4"][COLOR="Red"]**PLease do not post here but in the thread linked below, no support will be given here**[/COLOR][/SIZE]


If you're looking for support about this tutorial here is the original thread :
[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

---

