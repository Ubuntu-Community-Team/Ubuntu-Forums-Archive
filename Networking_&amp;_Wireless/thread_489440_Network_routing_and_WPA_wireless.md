---
title: "Network routing and WPA wireless"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by jdpipe on 2007-07-01
Hi all

After having my wireless-connected laptop working fine for a little while, I've managed to break it and can't work out what's wrong now.

When I boot into windows, it all works fine, connecting with a passphrase using WPA2-PSK. So it's not hardware, and it's not a problem with the router.

When I boot into Ubuntu (7.04), I can connect to the Dlink DI-524 router (it shows my mac address in the 'DHCP' page of the router control-panel website). I assume that means that I have all the encryption stuff sorted? 

The router gives me an IP address via DHCP. I can ping myself on the IP address it gives me.

The problems come now: I *can't* ping any *other* machine: not the router (192.168.0.1), not the DSL modem (10.1.1.1), not the desktop machine also on the network, and not any outside IP addresses.

My 'route -n' output shows (note I have disabled eth0 at this point):

192.168.0.0    0.0.0.0    255.255.255.0    U    0 0 0 ath0
169.254.0.0  0.0.0.0  255.255.0.0    U    1000 0 0 ath0
0.0.0.0 192.168.0.1   0.0.0.0  UG    0 0 0 ath0

(I don't know what that line 169.254.0.0 is about. Firewire, maybe? I presume it's not causing any problems?)

One final thing. The output of the 'wpa_cli' command 'status' is:

bssid:00:1b:9a:......
ssid:MYESSID
id=0
pairwise_cipher=CCMP
group_cipher=TKIP
key_mgmt=WPA2-PSK
wpa_state=completed
ip_address=192.168.0.102

My 'ifconfig' output shows ath0, lo, and 'wifi0_ren'. I don't know why I get that 'wif0_ren' and not just 'wifi0'. 

SO... what could the problem here? Any ideas? Any other tests I should run?

Cheers
JP

---

