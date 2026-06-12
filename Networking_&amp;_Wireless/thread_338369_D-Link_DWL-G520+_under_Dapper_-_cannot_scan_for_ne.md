---
title: "D-Link DWL-G520+ under Dapper - cannot scan for networks or connect"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by kilps on 2007-01-14
Hi all - I have been trying to figure out how to get this to work for a few hours now and I am pretty stuck ](*,)

I have a D-Link DWL-G520+ which I am trying to get to work under Dapper - basically whether I use network-manager or the built in app I can't get anywere ... bellow are some of the outputs from different command from the WifiTroubleShooting guide
sudo lshw
```

*-network:1
                description: Wireless interface
                product: ACX 111 54Mbps Wireless Interface
                vendor: Texas Instruments
                physical id: 2
                bus info: pci@02:02.0
                logical name: wlan0
                version: 00
                serial: 00:11:95:2b:30:bb
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=acx_pci multicast=yes wireless=IEEE 802.11b+/g+
                resources: iomemory:e8020000-e8021fff iomemory:e8000000-e801ffff irq:209
```iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"STA2B30BB"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=48/100  Signal level=27/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```iwlist wlan0 scan

```
wlan0     No scan results
```(I know that there are networks in range - i've got my laptop here which is picking things up fine ...)

Hopefully someone can help :( - thanks :)

---

### Post by Metaljaz on 2007-01-14
Read through this thread. Good Luck

[http://www.ubuntuforums.org/showthread.php?t=269149&highlight=D-Link+DWL-G520+ubuntu](http://www.ubuntuforums.org/showthread.php?t=269149&highlight=D-Link+DWL-G520+ubuntu)

---

