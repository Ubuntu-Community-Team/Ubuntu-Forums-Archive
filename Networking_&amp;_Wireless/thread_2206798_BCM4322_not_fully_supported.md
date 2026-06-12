---
title: "BCM4322 not fully supported"
date: 2014-02-20
forum: Networking &amp; Wireless
---

### Post by w-michael on 2014-02-20
Hello,
I need wlan with >60Mb/s. Additionally, 2.4GHz is overloaded. 5GHz should be used. Especially the channels >=100 are completely free. The network controller is:
```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Dell Wireless 1510 Wireless-N WLAN Mini-Card [1028:000d]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
```
802.11n and channels >=100 do work with Windows XP. The 5GHz Channels <100 are OK, too.

On Ubuntu 12.04 the best what I get is **wl**:
```
eth1      IEEE 802.11**abg**  ESSID:"XXXX"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:24:FE:08:D1:AB   
          Bit Rate=54 Mb/s   Tx-Power=200 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:54   Missed beacon:0

```
802.11n doesn't work. 5Ghz works but without channels >=100 (I use "iwlist wlan1 frequency").

**brcmsmac**:
```
wlan1     IEEE 802.11**bg**  ESSID:"XXXX"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:24:FE:08:D1:AB   
          Bit Rate=12 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:54   Missed beacon:0

```
5GHZ doesn't work at all and I get <12Mb/s.

**b43:**
```
wlan1     IEEE 802.11**bg**  ESSID:"XXXX"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:24:FE:08:D1:AB   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:53   Missed beacon:0
```
5GHZ doesn't work at all and I get <12Mb/s.

[B]ndiswrapper:
[/B]iwconfig says just 802.11**g** is supported. 5GHZ doesn't work. I can connect with 2.4 GHz to a Access Point and I get a IP from the DHCP. But no other data can be transferred. Maybe a problem with the encryption?

I posted no logs, because I don't know how I should continue (which driver?). The syslog seems ok for all drivers. I hoped ndiswrapper would work, because the Windows driver works. 
Any suggestions? Or should I buy an other controller?

---

### Post by varunendra on 2014-02-21
Welcome to the forums w-michael !

As you can see in this table, the 14e4:432b card is only partially supported by the b43, and based on the info in the same card, I'm surprised that it even worked with brcmsmac.

The sta (wl) driver doesn't support n channel so anything above 54 Mb/s is out of question.

We may try some tweaks but to be honest, I think you need a better supported card to get >60 Mb/s speed (maybe an Intel 7260?).

Make sure the encryption is pure WPA2-PSK with AES (CCMP), no WEP or WPA/WPA2 mixed mode, and certainly not TKIP, and if this can't help notch up the speed, there is probably nothing much we can do about it.

**PS:**
Don't expect ndiswrapper to get same performance from the windows driver that it can deliver when running natively on Windows. It is just a compatibility layer, running in emulation mode after all.

---

### Post by w-michael on 2014-02-24
Thank you very much. I have given up and I will buy an other network controller. 
I already tried 3 other controllers (2*USB + 1 H alf-Mini-Card). All should support 802.11n (But no 5 GHz). iwconfig shows that 802.11n is supported but the rate is always 54Mb/s (I measure 20 to 27 Mb/s). 
So 802.11n is supported by the driver but not used?  What else should I pay attention to?

---

### Post by varunendra on 2014-02-24
Many things. N-speeds require an overall ideal setup/configuration. That includes the card, driver, router capabilities/settings, traffic load, no. of simultaneous users, signal quality, surrounding signal interference/noise etc.

Not everything is under your control, and router/its firmware should be of good quality, not one of those that are just "Patched" to keep windows happy.

Some of the things that you can control dynamically (assuming you already have a card and router in hand that you are not going to change) -

**1)** Make sure the encryption type is pure WPA2 (not WPA or WPA/WPA2 mixed mode or WEP), and encryption algorithm is AES (CCMP), not TKIP. _TKIP effectively limits the max speed to 54 Mbps_.

**2)** Channel that is least used in the neighborhood and is least overlapped by its adjacent channels. That means channels 1, 6 and 11 (or 13 where it is available).

**3)** Use 5 Ghz frequency if it is available and is properly supported by the driver and the router.

**4)** May have to experiment with QoS/WMM support in the router. WMM support is supposed to enhance certain type of traffic speed, but some users have reported that it actually caused problems and needed to be turned off.

**5)** If you are not using IPv6, better set it to "Ignore" in Network Manager.

**6)** Sometimes setting a lower MTU value, like 1492 or 1392 instead of default 1500 does miracles to the traffic speeds. But only *sometimes*, usually when either the card or the router is a buggy or ancient one.

**7)** Different drivers often have different parameters available. Sometimes they can help in optimizing the performance.

**8)** It is a good idea to make sure the "Power Management" is kept "Off" on the wireless interface. Power saving during operation = loss of performance.

Lastly, as per our best and senior most wireless expert on the forums - chili555, with the same card, same OS and kernel version, same driver and same settings, the performance may dramatically differ for different people. And this is something that we witness everyday here. That's why we believe that full N-speeds depend not only on the driver and card, but the overall infrastructure in use, and most probably the external surrounding factors too.

We may try to optimize what we have, but 100% performance is, unfortunately, never guaranteed.

---

### Post by chili555 on 2014-02-24
Just a comment to add to the discussion:```
iwconfig wlan0 
wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:[COLOR="#FF0000"]5.805 GHz[/COLOR]  Access Point: xx:D7:19:41:54:xx
          Bit Rate=[COLOR="#FF0000"]108 Mb/s[/COLOR]   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:38   Missed beacon:0

```This is the default kernel driver *iwlwifi* with carefully tuned settings in the router.

---

### Post by varunendra on 2014-02-24
Now we have 'The best' with us. :P

Thanks for joining us sir!

---

### Post by chili555 on 2014-02-24
> 2) Channel that is least used in the neighborhood and is least overlapped by its adjacent channels. That means channels 1, 6 and 11 (or 13 where it is available).
You may get useful information with *horst*:```
sudo apt-get install horst
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
sudo horst
```

---

### Post by w-michael on 2014-02-24
Using Windows XP and 5 GHz I measure an average of 110 Mb/s. Using  2.4GHz I get 25 to 40 Mb/s at the moment. I think '2)' is the problem,  too many other networks on this frequency band.
I still not understand the output from iwlist scan. It shows the bit rates(e.g. "Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s").
But  I had never more then 54 Mb/s (with 5 different network controllers).  In Windows I see always what I set(54, 130 or 300 Mbit/s) in the router  configuration (WNDR3700). What does iwlist scan show? The intersection  between what the Access Point offers and what the driver supports?

---

### Post by praseodym on 2014-02-24
You need a patched wl driver:
```

sudo apt-get remove --purge bcmwl-kernel-source ndisgtk ndiswrapper*
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
```
Install the driver according to this for 32 or 64 bit with dkms:

[http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Installation-mittels-DKMS](http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Installation-mittels-DKMS)

---

### Post by varunendra on 2014-02-24
> **w-michael said:**
> I still not understand the output from iwlist scan. It shows the bit rates(e.g. "Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s").
But  I had never more then 54 Mb/s (with 5 different network controllers).  In Windows I see always what I set(54, 130 or 300 Mbit/s) in the router  configuration (WNDR3700). What does iwlist scan show? The intersection  between what the Access Point offers and what the driver supports?

Tools like "iwlist" show a detailed "Raw" information about what they see. What you see in windows is a calculated result, something similar to what you see in iwconfig.

In the result of "iwlist scan", what you see are the speeds supported by the device for "Individual" data streams - that is a raw info. The 'N' speeds are obtained _by multiplexing multiple such streams simultaneously_. The possible speed obtained by such multiplexing depends on many factors, and the end result is shown by iwconfig.

To be honest, I am myself a bit confused on what the TWO bit rate sequences show in the output (sometimes there is only one series), so I better not try to explain that. But for understanding the N-speeds, the wikipedia page is a good resource : [https://en.wikipedia.org/wiki/802.11n](https://en.wikipedia.org/wiki/802.11n)

---

### Post by w-michael on 2014-02-27
@praseodym: THX. I tested several wl versions. All worked, but without 802.11n.
@All: THX for the help.

---

