---
title: "Issues with WPA, WG111T"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by aoanla on 2006-10-27
I know that many people have been having issues with upgrades to Edgy destroying their ability to use wireless. I am one such person.

In Dapper, I had a functioning wireless connection with my WG111T (USB) wireless card, using ndiswrapper, wpa_supplicant, and the relevant drivers from the Windows install.

In Edgy, this fails, but in an interesting way. I compiled the latest stable ndiswrapper up from source, and installed both the athfmwdl and netwg11t drivers with it, as with Dapper.
I then tried to start wpa_supplicant, as normal, with the configuration file from Dapper.
This is the output:

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
proto: 0x1
PSK (ASCII passphrase) - hexdump_ascii(len=32): [REMOVED]
ssid - hexdump_ascii(len=7):
     73 70 6f 72 72 61 6e                              sporran         
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='sporran'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=20 WE(source)=18 enc_capa=0xd
  capabilities: key_mgmt 0x5 enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:14:6c:5d:ba:ec
Driver does not support WPA.
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Setting scan request: 0 sec 100000 usec
Added interface wlan0
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 487 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 0
0: 00:14:6c:ad:6c:24 ssid='sporran' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:14:6c:ad:6c:24 (SSID='sporran' freq=2462 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
State: SCANNING -> ASSOCIATING
WEXT: Operstate: linkmode=-1, operstate=5
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:14:6c:ad:6c:24 into blacklist
State: ASSOCIATING -> DISCONNECTED


and then it just loops trying to scan.

I've tried various fiddles with the configuration, with no real change. Any help would be appreciated.

---

### Post by aoanla on 2006-10-28
So, since no-one's offered any useful suggestions yet, I tried the following additional things:

1) Installing all of the ndiswrapper packages (and the appropriate kernel object which lives, stupidly, in the kernel packages, rather than being distributed with ndiswrapper). Doesn't work.

2) Installing network-manager + network-manager-gnome. With either the "official" ndiswrapper packages, or going back to my locally compiled versions of the latest ndiswrapper stable source... network-manager can't even see that I have a potential wireless device. The applet displays a white cross in red box, the status "No network connection", and, when clicked, lists, greyed-out, my wired ethernet card (which hasn't worked since a thunderstorm), and nothing else.

3) Tried removing the "auto wlan0" and "iface wlan0 ..." lines from /etc/network/interfaces, as suggested in some other threads.
Network-manager still can't see anything.

4) Tried various combinations of blacklisting kernel drivers listed in various threads.
Still doesn't work.


So, some help, and the heads of the people who allowed Edgy to ship when it breaks people's wireless, would be most appreciated.

---

### Post by aoanla on 2006-10-28
Right! Finally, I'm getting somewhere:

I've managed to get network-manager to admit that I have a wireless card, and to try to connect to my router with WPA.

It managed to connect, but I had no luck using Firefox to test if I could connect to anything beyond the router.

And then, suddenly, the connection dropped (this is with a signal strength reported as well into the top quarter of the bar), and I've been unable to regain it since.


(And now, changing nothing, after a reboot, network-manager fails to see my card again.)

---

### Post by aoanla on 2006-10-29
So! Spontaneously, network-manager started working again, and has been for several reboots.

And then, just a couple of hours ago, I was stupid enough to try following this thread:
[http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)
on installing Beryl.
(Of course, I thought to myself, merrily, how could that break my wireless?)

Well, it broke my wireless!
iwconfig and ifconfig don't list anything other than lo and the wired card anymore, even if I fiddle with /etc/network/interfaces. Modprobe claims it is still loading ndiswrapper, and ndiswrapper claims that it has installed drivers.

Network-manager now doesn't list the device anymore (it only lists, greyed-out, the wired ethernet card). 

However! Something is clearly working, as the power/signal light is on on the dongle, flashing slowly (which is what it tends to do in standby/no connection mode).

If anyone can tell me why installing linux-restricted-modules, or the nvidia drivers (note: I already had the standard Ubuntu nvidia drivers installed, when this was working) has broken my wifi so much, please do.

In fact, if anyone would like to reply to this thread /at all/, that'd make me feel a little less lonely here.

---

### Post by Yourname on 2006-10-30
If someone can just reply, it would be good.
Because I'm getting the same errors after trying to set wpa_supplicant, and test it. 

Spewing the same errors.
Edgy Eft, USB D-link G-122 WPA2 (AES)

---

### Post by L2wis on 2006-11-03
hey guys, I can't be much of a contributor to the solution of this since im still in 6.06. However i am intrested in a soloution because i also have the netgear WG111T usb wireless device. In future i maybe updating to 6.10 so it's all relevent.

Hope the solution comes soon.

Regards!

---

### Post by wieman01 on 2006-11-03
Post this file would help:
> sudo gedit /etc/network/interfaces
Plus can you test the device after disabling all kind of network authentication & encryption? Simply use DHCP and try to hook up to your network. Does that work?

Restart your network this way (post the output please):
> sudo /etc/init.d/networking restart
Please note: "wlan0" in Edgy is referred to as "eth1"... it's a potential stumbling-block, that's why I am mentioning it.

**_EDIT:_**
Please also post the results of:
> iwconfig
> iwlist scan
> route
All after having disabled security. WPA will be the next step.

---

