---
title: "Wpa"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by Sam Lars on 2006-08-05
We've decided to switch our network to WPA2 encryption.  There's a lot more to it than WEP...
I searched the forums here looking for anything that would help.
[http://www.ubuntuforums.org/showthread.php?t=225290&highlight=WPA2](http://www.ubuntuforums.org/showthread.php?t=225290&highlight=WPA2)
There's a lot there, but I don't think they've resolved it yet.  I tried all kinds of settings in attempts to get it to work.  Nothing's gotten it right yet.
I really don't know what to do next.  I've checked and double checked the ssid, the key, the PSK... it still doesn't like it.

/etc/wpasupplicant.conf
```

ctrl_interface=/var/run/wpa_supplicant
network={
ssid="ssid"
scan_ssid=1
key_mgmt=WPA-PSK
proto=RSN
pairwise=CCMP
group=CCMP
psk=psk
}
```

/etc/network/interfaces
```
auto eth0
iface eth0 inet static
    wpa-driver wext
    wpa-conf managed
    wpa-ssid ssid
    wpa-ap-scan 1
    wpa-proto RSN
    wpa-pairwise CCMP
    wpa-group CCMP
    wpa-key-mgmt WPA-PSK
    wpa-psk psk
```



So when I run some commands to try to connect, it gives me this repeatedly:

```
sudo wpa_supplicant -i eth0 -c /etc/wpa_supplicant.conf -D wext -w
Trying to associate with 00:0f:66:57:f3:74 (SSID='ssid' freq=0 MHz)
Trying to associate with 00:0f:66:57:f3:74 (SSID='ssid' freq=0 MHz)
Associated with 00:0f:66:57:f3:74
WPA: 4-Way Handshake failed - pre-shared key may be incorrect
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
```

I replaced the key and ssid with placeholders and left out the static configuration stuff. (It works just fine with WEP... I'm using that until the WPA will work.)
NetworkManager has had mixed results for me.  I installed it on another computer so that it would start the network automatically.  It claims there is no network device, but at least it connects me.  And I can't use it now with the static IP.
Any help or suggestions are welcome.

---

### Post by wieman01 on 2006-08-05
Just two things... You either configure your wireless LAN through the "wpa_supplicant.sh" file OR have the corresponding stanza in the "interfaces" file. You cannot do both.

So your interfaces file should look like this for static IP (example):

> auto eth0
iface eth0 inet static
address 192.168.168.40
netmask 255.255.255.0
network 192.168.168.0
broadcast 192.168.168.255
gateway 192.168.168.230	
dns-nameservers 192.168.168.230

Secondly I don't think "eth0" is your wireless adapter. It rather looks like the ethernet network card. Can you confirm this?

Also when firing up "wpa_supplicant" try to use this commend (same as yours with -dd at the end to get debug information):

> sudo wpa_supplicant -D wext -i eth0 -c /etc/wpa_supplicant.conf -w -dd

Thirdly I am not sure if "wext" is the right driver for you. What wireless card are you using?

---

### Post by wieman01 on 2006-08-06
I still don't think "eth0" is your wireless adapter, but would you mind telling us what kind of wireless card (brand, model, etc.) you have? Will help a lot.

We have made some progress in this thread lately. Check it out.

[http://www.ubuntuforums.org/showthread.php?t=225290&highlight=WPA2]("http://www.ubuntuforums.org/showthread.php?t=225290&highlight=WPA2")

---

### Post by Sam Lars on 2006-08-06
Thank you very much for your replies.
Yes, after upgrading something or other (maybe to Breezy?) the wlan0 changed itself to eth0.  Will this convince you?
```
iwconfig eth0
eth0      IEEE 802.11b/g  ESSID:"essid"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0F:66:57:F3:74
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level=2/3  Noise level=189/100
          Rx invalid nwid:0  Rx invalid crypt:34  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

It's a Linksys WMP54GS.  I'm using the bcm43xx with what fwcutter pulled.  I'm connected with WEP right now so that I can post this.  I'll put WPA back and see what I can get.

```
auto eth0
iface eth0 inet static
    wpa-driver wext

    wpa-conf managed

    wpa-ssid ssid

    wpa-ap-scan 1

    wpa-proto RSN

    wpa-pairwise CCMP

    wpa-group CCMP

    wpa-key-mgmt WPA-PSK

    wpa-psk psk

    wireless-essid ssid
```

So, let's see if I understand this.  If I comment out the wpa_supplicant.conf file's contents, and use the lines in the interfaces file, ifup eth0 should do the trick?  And if I uncomment the wpa_supplicant .conf lines and comment out the interfaces stuff, the command you gave me should do the trick?

---

### Post by rexterd on 2006-08-06
Did you use wpa_passphrase in creating your wpa_supplicant.conf file

---

### Post by Sam Lars on 2006-08-06
Yes, I used wpa_passphrase to get the PSK.
I tried just using these lines in the interfaces file.
```

auto eth0
iface eth0 inet static
    wpa-driver wext
    wpa-conf managed
    wpa-ssid winetworkufounodos
    wpa-ap-scan 1
    wpa-proto RSN
    wpa-pairwise CCMP
    wpa-group CCMP
    wpa-key-mgmt WPA-PSK
    wpa-psk psk

 wireless-essid winetworkufounodos
```

I tried sudo ifup eth0, and it just sat there and eventually went back to a prompt with no effect.
So I commented out all of that and uncommented my wpa_supplicant.conf to contain this.

```
ctrl_interface=/var/run/wpa_supplicant
network={
ssid="winetworkufounodos"
scan_ssid=1
key_mgmt=WPA-PSK
proto=RSN
pairwise=CCMP
group=CCMP
psk=psk
}
```

So then I tried this command, and it didn't work.

```
sudo wpa_supplicant -D wext -i eth0 -c /etc/wpa_supplicant.conf -w -dd
Initializing interface 'eth0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 2 - start of a new network block
ssid - hexdump_ascii(len=18):
     77 69 6e 65 74 77 6f 72 6b 75 66 6f 75 6e 6f 64   winetworkufounod
     6f 73                                             os
scan_ssid=1 (0x1)
key_mgmt: 0x2
proto: 0x2
pairwise: 0x10
group: 0x10
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='winetworkufounodos'
Initializing interface (2) 'eth0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Own MAC address: 00:0f:66:74:0c:76
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface eth0
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=18):
     77 69 6e 65 74 77 6f 72 6b 75 66 6f 75 6e 6f 64   winetworkufounod
     6f 73                                             os
Wireless event: cmd=0x8b19 len=8
Received 225 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:0f:66:57:f3:74 ssid='<hidden>' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
```

And it just repeats from "Starting AP scan".

---

### Post by wieman01 on 2006-08-06
Convinced me in terms of your wireless adapter being "eth0". :-)

Let's put it this way... If you make use of the "interfaces" file to configure your WPA(2) network, then **_don't use_** "wpa_supplicant.conf". That's redundant.

Secondly, some wireless cards/Linux drivers do not really support WPA2, although WPA1 is generally no issue at all. We have just experienced that in the mentioned thread.

So on the whole, you are going in the right direction, but I would try to make WPA(1) work first of all before you continue setting up WPA(2).  

This is the right configuration:

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet **dhcp**
    wpa-driver wext
    wpa-conf managed
    wpa-ssid winetworkufounodos
    wpa-ap-scan 1
    wpa-proto WPA
    wpa-pairwise TKIP
    wpa-group TKIP
    wpa-key-mgmt WPA-PSK
    wpa-psk **your_hex_key**

Could you tell us what wireless card you are using? Driver "wext" may not be the correct one. "Ndiswrapper? Then "wext" is the right one.

The last line in your example is also redundant ("wireless-essid"), please remove it.

Are you planning to use **DHCP** or **Static IPs**? If DHCP the first line should say "dhcp" as I have shown in here. In case you require static IP assignment, then you need to assign one as I have highlighted further above. No surprise your AP is not recognized.

I recommend to start with DHCP and WPA(1) so you can make use of my example. You need to change the settings in the router accordingly.

---

### Post by Sam Lars on 2006-08-07
Okay, this is a WMP54GS using the bcm43xx driver in the kernel with what fwcutter provided.  It works fine with WEP and static IP.
This is what the wpa_supplicant.conf looks like now.
```
#ctrl_interface=/var/run/wpa_supplicant
#network={
#ssid="winetworkufounodos"
#scan_ssid=1
#key_mgmt=WPA-PSK
#proto=RSN
#pairwise=CCMP
#group=CCMP
#psk=0ae6f4d87c3ca96195ee58b73233c1274fc564dc28d93eb838973fd54cc6cd24
#}
```
And this is what the interfaces file looks like.
```
auto eth0
iface eth0 inet static
wpa-driver wext
wpa-conf managed
wpa-ssid winetworkufounodos
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 0ae6f4d87c3ca96195ee58b73233c1274fc564dc28d93eb838973fd54cc6cd24

```
I set the router to WPA and TKIP.
I'm planning on static IP's (otherwise I would have at least tried the NetworkManager solution), but I did try taking out the static configuration and using DHCP.  I've seen enough of this before.
```
sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:0f:66:74:0c:76
Sending on   LPF/eth0/00:0f:66:74:0c:76
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20

```
The Windows machine is using DHCP, since it had issues with static IP.  So that works.  Back to static IP.
Running sudo ifup eth0 made the network icon start blinking... but it wouldn't connect.  Sometimes it would become disconnected before attempting again.  Eventually the prompt would come back, but it would keep trying to connect.
The only thing I'm changing when I test this is commenting out the WEP configuration and uncommenting the WPA configuration.  I leave the static IP stuff alone, and it should work with WPA just as it does with WEP.
Thanks for all of the help!

---

### Post by wieman01 on 2006-08-07
That's what I said... If you want to use static IP, the you need to add these lines as well:

> auto eth0
iface eth0 inet **static**
[B]address 192.168.168.40
netmask 255.255.255.0
network 192.168.168.0
broadcast 192.168.168.255
gateway 192.168.168.230
dns-nameservers 192.168.168.230[/B]
wpa-driver wext
wpa-conf managed
wpa-ssid winetworkufounodos
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 0ae6f4d87c3ca96195ee58b73233c1274fc564dc28d93eb838973fd54cc6cd24

Your interfaces file says "static"... if you use DHCP, then you need to replace it with "dhcp", otherwise you won't be able to establish a connection.

Please change the IP configuration according to your own network settings. 

DHCP should look like this:

> auto eth0
iface eth0 inet **dhcp**
wpa-driver wext
wpa-conf managed
wpa-ssid winetworkufounodos
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 0ae6f4d87c3ca96195ee58b73233c1274fc564dc28d93eb838973fd54cc6cd24

---

### Post by Sam Lars on 2006-08-07
Okay, this is what works with WEP.
```
auto eth0
iface eth0 inet static
#wpa-driver wext
#wpa-conf managed
#wpa-ssid winetworkufounodos
#wpa-ap-scan 1
#wpa-proto WPA
#wpa-pairwise TKIP
#wpa-group TKIP
#wpa-key-mgmt WPA-PSK
#wpa-psk 0ae6f4d87c3ca96195ee58b73233c1274fc564dc28d93eb838973fd54cc6cd24


up iwconfig eth0 essid winetworkufounodos
up iwconfig eth0 enc 1F49D22932157BB443006F7E11
up iwconfig eth0 channel 11
up iwconfig eth0 mode managed
up iwconfig eth0 ap auto


    address 192.158.7.103
    netmask 255.255.255.0
    network 192.158.7.0
    broadcast 192.158.7.255
    gateway 192.158.7.1
```
And this is what does not work with WPA.
```
auto eth0
iface eth0 inet static
wpa-driver wext
wpa-conf managed
wpa-ssid winetworkufounodos
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 0ae6f4d87c3ca96195ee58b73233c1274fc564dc28d93eb838973fd54cc6cd24


#up iwconfig eth0 essid winetworkufounodos
#up iwconfig eth0 enc 1F49D22932157BB443006F7E11
#up iwconfig eth0 channel 11
#up iwconfig eth0 mode managed
#up iwconfig eth0 ap auto


    address 192.158.7.103
    netmask 255.255.255.0
    network 192.158.7.0
    broadcast 192.158.7.255
    gateway 192.158.7.1
```

---

### Post by bensexson on 2006-08-07
I was unable to get a connection working with WPA or WPA2 with my hidden SSID until I set wpa-ap-scan  to 2.  I used this for WPA2 with my Broadcom 4306 using ndiswrapper.

auto eth1 (my wireless interface)
iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid <your_essid>
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <your_hex_key>

I now have my custom networking scripts working to check which AP to connect to on boot up with WPA.  I am very happy right now.

I wouls suggest you test by enabling SSID broadcast on your AP and see if you can connect then.

---

### Post by KJFreak on 2006-08-07
Hi everybody, first sorry my english but isn't my natural language, i have a question, i'm ussing KUbuntu, and the tool Wireless Assistant to connect to the wireless network, in my house i was configured the wireless to use WPA but when try to connect whit KUbuntu-Wireless Assitant i can't setup the wireless whit WAP couse the assistant haven't the option to use this security kind, just WEP, then i have to change my router's configuration to use WEP and whit that, all works fine.

The question is how setup a wireless connection with de tool Wireless Assistant of KUbuntu if is possible else what can i do??

Thks for all. 

Sorry if this is a "Off Topic" cause i'm ussing KUbuntu and not Ubuntu.

---

### Post by wieman01 on 2006-08-07
"Sam Lars":

Two questions:

1. Have you got hidden ESSID enabled?
2. Is your router set static IP or still DHCP?

If static IPs & hidden ESSID apply, this script should do. Please try again:
> auto eth0
iface eth0 inet static
address 192.158.7.103
netmask 255.255.255.0
network 192.158.7.0
broadcast 192.158.7.255
gateway 192.158.7.1
wpa-driver wext
wpa-conf managed
wpa-ssid winetworkufounodos
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 0ae6f4d87c3ca96195ee58b73233c1274fc564dc28d93eb838973fd54cc6cd24


**"wpa-ap-scan"** needs to have a value of **2** rather than 1. This controls the way the wireless adapter is scanning for wireless networks.

Please restart your network **twice** (some users have reported that this is the case):
> sudo /etc/init.d/networking restart
A reboot may be necessary as well.

---

### Post by wieman01 on 2006-08-07
> **KJFreak said:**
> Hi everybody, first sorry my english but isn't my natural language, i have a question, i'm ussing KUbuntu, and the tool Wireless Assistant to connect to the wireless network, in my house i was configured the wireless to use WPA but when try to connect whit KUbuntu-Wireless Assitant i can't setup the wireless whit WAP couse the assistant haven't the option to use this security kind, just WEP, then i have to change my router's configuration to use WEP and whit that, all works fine.

The question is how setup a wireless connection with de tool Wireless Assistant of KUbuntu if is possible else what can i do??

Thks for all. 

Sorry if this is a "Off Topic" cause i'm ussing KUbuntu and not Ubuntu.

Try NetworkManager. Nice little tool despite the fact that it has two major constraints:

1. No hidden ESSID
2. DHCP only.

[http://www.ubuntuforums.org/showthread.php?t=125150]("http://www.ubuntuforums.org/showthread.php?t=125150")

---

### Post by wieman01 on 2006-08-07
> **bensexson said:**
> I was unable to get a connection working with WPA or WPA2 with my hidden SSID until I set wpa-ap-scan  to 2.  I used this for WPA2 with my Broadcom 4306 using ndiswrapper.

auto eth1 (my wireless interface)
iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid <your_essid>
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <your_hex_key>

Somehow I have seen this before. :-) Glad to hear it worked for you. Yes, you're right. "wpa-ap-scan" needs to be set to 2 in that case.

---

