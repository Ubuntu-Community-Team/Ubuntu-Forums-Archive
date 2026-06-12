---
title: "ar5212 and WPA-PSK : wpa_supplicant not picking the good essid"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by guix on 2008-05-10
Hi,

I have this problem since a couple of weeks, it showed up suddenly on my Gutsy : everything was working fine,then my wireless connection (Atheros ar5212) suddenly started to get slower and I had to relaunch it several times ("sudo /etc/init.d/networking restart") before trying to reboot (sometimes the wireless stack needs to be cleaned or something and rebooting works nice). But since that reboot I can't connect any more to my wifi, because wpa_supplicant fails to pick my essid and keeps trying other available essids.

I decided to upgrade to Hardy but I have the same problem, so it shouldn't be, as suggested before, a brokage of the madwifi driver. I didn't have to compile and install it for Gutsy, the one included in the kernel modules was working nicely. I'm using wext for a long time now, can't remember why but I think madwifi was failing to work with my WPA-SPK + static IP configuration. I did my setup that was working nicely with this how-to : [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539))

Moreover, since I had this problem on Gutsy, the driver was working at least to give me the available essids when I was typing "iwlist scanning", and I can get the same list on Hardy now.

Finally under Windows the connectivity is good and with the same parameters as always, so it shouldn't be a hardware problem.

The problem could be that wpa-supplicant can't authentificate any more to my essid, it may fail to give the password or it may be a problem with the WPA-PSK protocol ? Maybe something changed on my router (it's a Freebox, it sometimes updates and maybe the WPA-PSK protocol I'm using is no longer available ?), but in that case it's a change that Windows XP would have been able to correct automatically.

Really I wonder what's happening. I'm giving below my configuration. I'm not using Network manager because last time I tried (on Feisty I guess) it couldn't manage a WPA connection with a fixed IP.

/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet static
address 192.168.0.2 # my fixed local IP
gateway 192.168.0.254 # my router
dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx # my DNS servers
netmask 255.255.255.0
wpa-driver wext
wpa-ssid *my-essid-name*
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk *my-wpa-psk-key*

```

I've disabled the Network manager service in the Gnome session and to prevent it to load I have also :

/etc/default/NetworkManager
```

exit

```

/etc/default/NetworkManagerDispatcher
```

exit

```

Here are different outputs of 'iwconfig' that show it tries a and g wifi modes. The frequencies change slightly also, for instance for the g mode it can be 5.2 GHz, 5.19 GHz, 5.24 GHz, ...). The essid can be void like on these examples but if I do "sudo /etc/init.d/networking restart" it can be another essid but not mine !
```

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Frequency:5.2 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:1536  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
```

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.467 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-99 dBm  Noise level=-99 dBm
          Rx invalid nwid:1536  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Example with an essid but not mine, after "sudo /etc/init.d/networking restart" :

```

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:"OzoneParis.net : acces libre"  Nickname:""
          Mode:Managed  Frequency:5.58 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=14/70  Signal level=-84 dBm  Noise level=-98 dBm
          Rx invalid nwid:1538  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
Once again this config was working really nicely and I can't understand what's happening ! Would appreciate any help :)

---

### Post by guix on 2008-05-11
Sunday bump !

---

### Post by guix on 2008-05-22
Any ideas on this... ?

---

### Post by guix on 2008-05-23
One last try... please help if you have any idea !

---

### Post by guix on 2008-06-07
Still not resolved...

---

### Post by guix on 2008-06-14
bump. help plz

---

