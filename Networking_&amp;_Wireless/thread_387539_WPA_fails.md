---
title: "WPA fails?"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by HarrisonHopkins on 2007-03-18
Alright, I just got my FON router, the one with the two SSIDs, one public, one private and WPA secured. I've done the setup, by first connecting to the public one, and going through the setup, and now when I try to connect to the WPA secured one, I can't. I could connect fine to the WEP on my old router. Does Ubuntu not work with WPA or am I missing something?

---

### Post by Floppyjoe on 2007-03-18
Here is a link to a WPA howto:

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

### Post by HarrisonHopkins on 2007-03-18
I tried what was at hat link, but it didn't work.  

This is what it says 

```
harrison@harrison-laptop:~$ sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dndiswrapper -w
Trying to associate with 00:18:84:1f:ba:0e (SSID='MyPlace' freq=2412 MHz)
Association request to the driver failed
Authentication with 00:00:00:00:00:00 timed out.

```

---

### Post by Floppyjoe on 2007-03-18
> **HarrisonHopkins said:**
> I tried what was at hat link, but it didn't work.  

This is what it says 

```
harrison@harrison-laptop:~$ sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dndiswrapper -w
Trying to associate with 00:18:84:1f:ba:0e (SSID='MyPlace' freq=2412 MHz)
Association request to the driver failed
Authentication with 00:00:00:00:00:00 timed out.

```
try this:
```
sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dwext -w
```

---

### Post by HarrisonHopkins on 2007-03-18
Just tried that, and I got this:

```
Trying to associate with 00:18:84:1f:ba:0e (SSID='MyPlace' freq=2412 MHz)
Associated with 00:18:84:1f:ba:0e
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

```

---

### Post by Floppyjoe on 2007-03-18
Did you click ctrl-c or did it exit on it's own?

---

### Post by HarrisonHopkins on 2007-03-18
It repeated that for a while, and then I CTRL-Ced it.

---

### Post by Floppyjoe on 2007-03-18
seems to me like it is working. try rebooting your computer to see if it works.

and make sure your /etc/network/interfaces file has this in it.
> wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf

---

### Post by HarrisonHopkins on 2007-03-18
I rebooted. The network manager thing at the top right says that it has a great signal, but it isn't connected..

---

### Post by Floppyjoe on 2007-03-18
What does your /etc/network/interfaces file look like?
```
sudo gedit /etc/network/interfaces
```

---

### Post by HarrisonHopkins on 2007-03-18
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid MyPlace
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk c59a7bfecedfbb233bddf0c642619115a017d397968006dd34760d0cb086ed71

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp






auto eth0

```

The things under eth1 are from another HowTo. Should I remove them?

---

### Post by Floppyjoe on 2007-03-18
> **HarrisonHopkins said:**
> ```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid MyPlace
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk c59a7bfecedfbb233bddf0c642619115a017d397968006dd34760d0cb086ed71

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp






auto eth0

```

The things under eth1 are from another HowTo. Should I remove them?
Try changing it to this:
```
auto lo
iface lo inet loopback


#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp
#wpa-driver wext
#wpa-conf managed
#wpa-ssid MyPlace
#wpa-ap-scan 1
#wpa-proto WPA
#wpa-pairwise TKIP
#wpa-group TKIP
#wpa-key-mgmt WPA-PSK
#wpa-psk c59a7bfecedfbb233bddf0c642619115a017d397968006dd34760d0cb086ed71

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp






#auto eth0
```
and disable all network adapters in System/Administration/Networking.
This is required for network manager to work.

---

### Post by HarrisonHopkins on 2007-03-18
I did that, rebooted, and it claimed to have been connected, but I couldn't get any internet.

I swear, I hate my Fon router right now. It is supposed to broadcast 2 SSIDs, and I am trying to connect to the secure one. When I do iwlist scanning though, the secure one iisn't appearing.

---

### Post by Floppyjoe on 2007-03-18
> **HarrisonHopkins said:**
> I did that, rebooted, and it claimed to have been connected, but I couldn't get any internet.

I swear, I hate my Fon router right now. It is supposed to broadcast 2 SSIDs, and I am trying to connect to the secure one. When I do iwlist scanning though, the secure one iisn't appearing.
Is the router set up to broadcast both SSID's? Maybe it's not configured properly.

What is the output of:
```
ifconfig
```
Does it show that you are getting an IP address?

---

### Post by HarrisonHopkins on 2007-03-19
Yeah, the router is  set up correctly. In Windows, it shows both.

I had it working, but then I restarted my computer and now it says I have great signal, but I'm not connected. However, I'm getting internet, but not through the correct SSID obviously, because I was redirected to a login age like you would get if you tried to connect to the internet at a McDonalds or whatever.

ifconfig shows:

```
eth0      Link encap:Ethernet  HWaddr 00:15:C5:C5:5F:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 

eth1      Link encap:Ethernet  HWaddr 00:18:F3:D8:30:6B  
          inet addr:192.168.182.3  Bcast:192.168.182.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fed8:306b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2345 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1232747 (1.1 MiB)  TX bytes:287243 (280.5 KiB)
          Interrupt:169 Memory:efcfc000-efd00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:700 (700.0 b)  TX bytes:700 (700.0 b)

```

why is eth0 there? thought I had it disabled?

---

### Post by HarrisonHopkins on 2007-03-20
Any ideas?

---

### Post by HarrisonHopkins on 2007-03-20
I'll ask again.

---

