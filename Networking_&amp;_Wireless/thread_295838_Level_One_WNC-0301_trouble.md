---
title: "Level One WNC-0301 trouble"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by cfp999 on 2006-11-08
I have been trying to get this thing to work, but so far no luck. As far as I can tell the WNC-0301 is based on the RaLink chipset. After reading this thread [http://ubuntuforums.org/showthread.php?t=132980]("http://ubuntuforums.org/showthread.php?t=132980")
 I issued *lspci* to identify the chipset, but it does not show up as an unknown device. Rather it identifies itself as:
> 01:08.0 Network controller: RaLink RT2561/RT61 802.11g PCI.

iwconfig gives this:

> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz RTS thr:off Fragment thr=2346 B 
            
wlan0     IEEE 802.11g  ESSID:"" Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated           RTS thr:off   Fragment thr=2346 B          

sit0      no wireless extensions.

Does that mean it is partially working, and how should I proceed?

I have already tried running my wireless network in both WEP and unencrypted mode just to make sure. All info (SSID, WEP-key etc.) was entered in Administration -> Network, but all that shows up in the network applet is the loopback lo.

---

