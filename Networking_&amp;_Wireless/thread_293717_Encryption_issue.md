---
title: "Encryption issue"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by orian on 2006-11-05
Hi

Could someone help me to understand this problem?  

My wireless works if I disable the encryption on my router (a linksys WRT54G) When I enable it, and ensure the wep key is correct in my network settings, the wireless disables--it won't enable again until I disable the encryption on the router??? This only started with Edgy. My wireless (with security) worked fine with Dapper. I have a Intel pro-wireless 2200.

Anyone know what is going on?

Orian

---

### Post by spd106 on 2006-11-05
Does it still associate with the AP? I.e. does it still show the right AP in **iwconfig**?

Have you tried checking the encryption key? It's best to use a hex key, rather than a passphrase. Does it work with another host? on windows?

---

### Post by orian on 2006-11-05
Hi, thanks for responding

Here is my iwconfig output with encryption enabled: 

unassociated  ESSID:"linksys"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
Like I said, with encryption disabled it does show an AP, channel etc.

I don't dual  boot, however, when I did it worked fine in Windows xp Pro

I have tried different encryptions-no luck so far.

Could you give me an example of one that works in Edgy and what security setting to choose on the rougter ie WPA WPA2 etc. and what type of algorithm:TKIP AES?

Thanks
Orian

---

### Post by spd106 on 2006-11-06
I suggest that you start with the simplest case, 64 bit WEP. It should be enough to enable it on the router with a simple hex password eg 1234567890. Then on your laptop enter the details in the network admin tool. System -> Admin -> Networking. 

If that doesn't work then switch to a terminal and edit the /etc/network/interfaces file. It should look something like this
```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys
wireless-key 1234567890

```

Check it works by restarting the interfaces **sudo ifdown -a** then **sudo ifup -a**.

You should be connected. If not check **iwconfig** and try scanning for APs **sudo iwlist wlan0 scan**.

If you want WPA, I strongly suggest you install network-manager [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo) or wifi-radar.

---

