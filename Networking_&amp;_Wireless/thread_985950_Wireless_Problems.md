---
title: "Wireless Problems"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by Enigmatus on 2008-11-18
Yesterday evening, I was rather unexpectedly disconnected, and my wireless network seemingly disappeared from the face of the earth.

As far as I know, my wireless network card is working (it is still being detected by Ubuntu), and I know that my router is functioning correctly (I connected to the Internet via my PSP earlier this morning), yet when I click on the network connections symbol on the taskbar, my wireless connection is nowhere to be seen?

If it helps, I am currently running Ubuntu 8.10 (Intrepid Ibex).

Thank you in advance for your assistance.

---

### Post by spotsworth on 2008-11-18
what's the output from iwconfig?
lshw -C network?

---

### Post by Enigmatus on 2008-11-18
> **spotsworth said:**
> what's the output from iwconfig?

> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


Hopefully this can give you some clues as to what's happening!

---

### Post by Enigmatus on 2008-11-18
> **spotsworth said:**
> lshw -C network?

>   *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:3e:61:7a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.0.2 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:19:7e:79:e0:66
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a2:55:f8:f9:13:c9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


My apologies for the delayed reply, I only just noticed your second request.

---

### Post by Enigmatus on 2008-11-18
Anyone?

---

### Post by Enigmatus on 2008-11-18
No?

---

### Post by pmsumner on 2008-11-18
OK, try this in your terminal and post the results:

```
lsmod | grep ath
```

If it returns nothing then try running:

```
sudo modprobe ath5k
```
or if this doesn't get you anything in the lsmod | grep ath thingie...
```
sudo modprobe ath_pci
```

---

### Post by Enigmatus on 2008-11-18
> **pmsumner said:**
> ```
lsmod | grep ath
```

> ath5k                 106496  0 
lbm_cw_mac80211       210728  1 ath5k
lbm_cw_cfg80211        39696  2 ath5k,lbm_cw_mac80211
led_class              12164  2 acer_wmi,ath5k


:)

---

### Post by Enigmatus on 2008-11-19
Can anyone possibly help me with this please? I need it remedied ASAP if possible! :oops:

---

### Post by CodeAlias on 2008-11-19
what security settings are you using ? WEP/WPA ?

---
[Security, Performance, Wireless]("http://www.codealias.info")

---

### Post by Enigmatus on 2008-11-19
> **CodeAlias said:**
> what security settings are you using ? WEP/WPA ?

---
[Security, Performance, Wireless]("http://www.codealias.info")

"WPA & WPA2 Personal"

---

### Post by CodeAlias on 2008-11-19
It can be an issue with the supplicant using wrong parameters.

You can try to disable any network manager controlling the interface, then use wpa_supplicant to manage your association with the AP. This is guide on how to do it :

[WPA2 with PSK using wpa_supplicant]("http://www.codealias.info/technotes/wireless_security_wpa2_with_psk_using_wpa_supplicant_linux_setup")


---
[Security, Performance, Wireless]("http://www.codealias.info")

---

### Post by Enigmatus on 2008-11-21
Unfortunately, this remedy didn't work, any other suggestions? :(

---

### Post by Enigmatus on 2008-11-21
Anyone?

---

### Post by Enigmatus on 2008-11-22
Anyone?

---

### Post by Enigmatus on 2008-11-23
Anyone at all?

---

### Post by kevdog on 2008-11-23
what's the problem?? I'm confused?

---

### Post by Enigmatus on 2008-11-24
> **kevdog said:**
> what's the problem?? I'm confused?

Basically, my wireless network has totally 'disappeared', regardless of the fact that my router is functioning perfectly, and to the best of my knowledge, my wireless network card is functioning correctly.

---

### Post by ddixonr on 2008-11-24
Hopefully you already tried this, but I am curious to see if you can connect directly (wired) to the router? 

I imagine this is how you are connecting to these forums, but you can never assume these things.

---

### Post by Enigmatus on 2008-11-24
> **ddixonr said:**
> Hopefully you already tried this, but I am curious to see if you can connect directly (wired) to the router? 

I imagine this is how you are connecting to these forums, but you can never assume these things.

You are correct! :)

I just wish I could get this problem rectified.

---

### Post by ddixonr on 2008-11-25
Is there any way possible that the ssid broadcast was turned off in the router settings? When I had mine turned off, I connected to it by using "Connect to Other Wireless Network" under the list of wireless networks in the network manager.

---

