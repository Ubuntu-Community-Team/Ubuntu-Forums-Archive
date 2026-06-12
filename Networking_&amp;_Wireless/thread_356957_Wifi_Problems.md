---
title: "Wifi Problems"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by retrohelix on 2007-02-09
Hello, 
A friend of mine recently put ubuntu on my laptop. He strongly recommended it ( although he had yet to install it on his computer) anywho long story short, As soon as wifi became a problem he referred me here and I havent heard from him since.

I have gone through a couple of the wiki posts for setting up my wireless connection...
I have a aironet wireless communications cisco aironet built in card.
One thing I have noticed that is weird about my setup is that there are two wireless interfaces, eth1 and wifi0.
I managed to get the thing working when, oddly against the advice of the article, I activated both interfaces. After that I had internet access, unfortunately this only worked while there was no WEP set on my router. After I got internet access, I tried to go through the steps on the how to for setting your connection up to deal with WEP, but It stopped working once I tried adding the WEP key. I have since gone through the FAQ, getting to the part where, after failing many tests I eventually worked my way down to the suggestion of putting wifi radar, which would not connect me to my network whether or not WEP was activated. According to the troubleshooter, my card is in there and the driver is fine, and it is communicating with the kernel, whatever that means. So please if anyone can help I would be very grateful, I use wireless a lot, this is starting to get to me. - Aman

---

### Post by gradedcheese on 2007-02-09
Can you please post the following things: the output of running the command "iwconfig" in a terminal, and the contents of the file "/etc/network/interfaces" (you can just open it in a text editor or run "cat /etc/network/interfaces" in your terminal).  The latter will (should) contain your WEP key, you can replace it with something like _wep_key_here if when you post if you want.  For example, the interfaces file could have lines like these:

```

auto eth1
iface eth1 inet dhcp
wireless-essid your_ssid_here
wireless-key your_wep_key_here

```

As an initial step, we should make sure that iwconfig's output and this file's settings make sense.  As far as the eth1 and wifi0, this is pretty common: one is your real WiFi card (eth1) and the other is a special management interface implemented as a virtual interface.  I'm not sure why you had to bring both up, but that's interesting to hear.

---

### Post by retrohelix on 2007-02-09
hmm.... doesnt seem to be showing a wep, i guess its because i restarted my computer, should I post again after I type in the code for wep? thank you - Aman

"iwconfig"
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"liniaman"  Nickname:"liniaman"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:BF:46:83:3C   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:98/100  Signal level:-46 dBm  Noise level:-108 dBm
          Rx invalid nwid:38410  Rx invalid crypt:315  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:152657   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"liniaman"  Nickname:"liniaman"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:BF:46:83:3C   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:98/100  Signal level:-46 dBm  Noise level:-108 dBm
          Rx invalid nwid:38410  Rx invalid crypt:315  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:152657   Missed beacon:0

sit0      no wireless extensions.


"/etc/network/interfaces"
auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp





auto eth0

---

