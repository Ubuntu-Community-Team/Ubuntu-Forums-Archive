---
title: "ndiswrapper + wpa_supplicant =&gt; skip - no WPA/RSN IE"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by mikecurtis on 2006-11-12
Hi all,

So I've got a BCM4318 card in my box, and I've got wireless working without encryption, after following these instructions:
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

I've also got wpa_supplicant set up, based upon these instructions:
[http://help.ubuntu.com/community/WifiDocs/WPAHowTo](http://help.ubuntu.com/community/WifiDocs/WPAHowTo)

However, when I try to enable WPA, I run into some problems.  On my WRT54GS, I enabled WPA Personal with TKIP, and I've got SSID broadcast enabled and Mixed mode on.  I've got a Winblows machine here on the side that can then connect to that using WPA just fine.  However, here on my Ubuntu box, when I try to connect to Mike3 using wpa_supplicant, I get "skip - no WPA/RSN IE" messages, for reasons that aren't clear to me:

```
> sudo wpa_supplicant -iwlan1 -c/etc/wpa_supplicant.conf -Dndiswrapper -dd
Initializing interface 'wlan1' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Line: 679 - start of a new network block
ssid - hexdump_ascii(len=5):
     4d 69 6b 65 33                                    Mike3
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='Mike3'
Initializing interface (2) 'wlan1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Own MAC address: 00:14:bf:76:ba:72
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Setting scan request: 0 sec 100000 usec
Added interface wlan1
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 1285 bytes of scan results (6 BSSes)
Scan results: 6
Selecting BSS from priority group 0
0: 00:06:25:66:ac:d0 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 00:13:10:65:e2:d8 ssid='MWE' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:14:95:05:c9:19 ssid='2WIRE498' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:18:3f:b9:68:e9 ssid='2WIRE671' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:12:88:50:e0:31 ssid='2WIRE358' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
5: 00:14:bf:c4:3d:6d ssid='Mike3' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
No suitable AP found.
Setting scan request: 5 sec 0 usec
```


Here's the relevant part of the output of iwlist wlan1 scan for Mike3:

```
Cell 14 - Address: 00:14:BF:C4:3D:6D
          ESSID:"Mike3"
          Protocol:IEEE 802.11g
          Mode:Managed
          Frequency:2.437 GHz (Channel 6)
          Quality:0/100  Signal level:-62 dBm  Noise level:-256 dBm
          Encryption key:off
          Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                    11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                    48 Mb/s; 54 Mb/s
          Extra:bcn_int=100
          Extra:atim=0
```


Based upon other threads I've read, I believe that I'm supposed to have something in the "Extra" section that says rsn_ie=..., but I don't really know what to do about that.

And my wpa_supplicant.conf doesn't really have anything interesting:

```
network={
  ssid="Mike3"
  psk=[password]
}

```


Just to be pedantic, I also tried making this more explicit:

```
network={
  ssid="Mike3"
  psk=[password]
  proto=WPA
  key_mgmt=WPA-PSK
  pairwise=TKIP
  group=TKIP
}
```


But, alas, this was to no avail.

Any suggestions on how to debug this problem?


As an aside, I'm not entirely sure of how the ubuntu gnome networking tools interact (or don't interact) with the /etc/network/interfaces file.  But, in any event, here's what I've got in there now:

```
> cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface wlan1 inet dhcp
wireless-essid Mike3

auto wlan1
```

Thanks in advance for any suggestions!

---

### Post by mikecurtis on 2006-11-12
Alright, I got it!

So, after working on this for countless hours, the moral of the story, as far as I'm concerned, is that network-manager is evil :evil:!  (At least when trying to get WPA working with this card)

I had strongly suspected that somehow the network-manager was screwing me up, and I really don't like using GUI tools that act as black boxes where I have no idea what they are doing.  It seemed like network-manager somehow thought that my AP was unencrypted, and so I wanted to just get rid of it.  So, I was trying to fiddle with the options in network-manager, removing the password, unchecking "enable this connection", hitting deactivate and reactivate in various iterations, all the while trying to run wpa_supplicant on the side.  After doing this for a while, at a certain point wpa_supplicant finally didn't return "no WPA/RSN IE", but instead started working!

I wasn't really sure what I did, but this was definitely progress.  I tried pinging [www.google.com](www.google.com), but to no avail.  Then, I remembered that I probably needed to run "sudo dhclient" first, and after that I could connect to the internet.  Yay! :D 

So, I had earlier been using

```
sudo wpa_supplicant -iwlan1 -c/etc/wpa_supplicant.conf -Dndiswrapper -dd
```

to run wpa_supplicant with debugging messages.  Now that I could find my AP, I tried rebooting.  This time, I made sure not to touch anything on network-manager after my system came back on.  Now, I tried:

```
sudo wpa_supplicant -iwlan1 -c/etc/wpa_supplicant.conf -Dndiswrapper -B
sudo dhclient
```

And it worked!

After a little bit of searching, I found that I could now simplify things by modifying my /etc/network/interfaces to look like so:

```

auto lo
iface lo inet loopback

auto wlan1
iface wlan1 inet dhcp
wpa-driver ndiswrapper
wpa-conf /etc/wpa_supplicant.conf
```

Now, a reboot, and my internet connection is good to go straight from startup!

Hope this information saves someone else the amount of time I lost on this!

---

