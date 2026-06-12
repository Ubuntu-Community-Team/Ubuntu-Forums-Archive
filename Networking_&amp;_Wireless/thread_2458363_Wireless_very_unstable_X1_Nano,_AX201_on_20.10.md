---
title: "Wireless very unstable X1 Nano, AX201 on 20.10"
date: 2021-02-22
forum: Networking &amp; Wireless
---

### Post by shizow on 2021-02-22
I have a very new laptop, Thinkpad X1 nano, it was just released 1-2 months ago from Thinkpad.

I just installed 20.10.

the Wifi is very buggy, it works for 1-2 hours than it disconnects and cannot reconnect, this happens with several different networks.

uname -a
Linux thinkpad 5.8.0-43-generic #49-Ubuntu SMP Fri Feb 5 03:01:28 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

$ lspci | grep Net
00:14.3 Network controller: Intel Corporation Wi-Fi 6 AX201 (rev 20)

$ sudo lshw -C network 
[sudo] password for user: 
  *-network                 
       description: Wireless interface
       product: Wi-Fi 6 AX201
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlp0s20f3
       version: 20
       serial: cc:d9:ac:cb:5a:a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.8.0-43-generic firmware=55.d9698065.0 QuZ-a0-hr-b0-55.u ip=192.168.0.27 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: iomemory:600-5ff irq:16 memory:603d1dc000-603d1dffff

lspci -nnkv | sed -n '/Network/,/^$/p'
00:14.3 Network controller [0280]: Intel Corporation Wi-Fi 6 AX201 [8086:a0f0] (rev 20)
	Subsystem: Intel Corporation Wi-Fi 6 AX201 [8086:0070]
	Flags: bus master, fast devsel, latency 0, IRQ 16, IOMMU group 11
	Memory at 603d1dc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [80] MSI-X: Enable+ Count=16 Masked-
	Capabilities: [100] Latency Tolerance Reporting
	Capabilities: [164] Vendor Specific Information: ID=0010 Rev=0 Len=014 <?>
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi

dmesg | grep -i -E '00:14.3|wlp|iwl|80211'
[https://pastebin.ubuntu.com/p/NMtvVW8k3W/](https://pastebin.ubuntu.com/p/NMtvVW8k3W/)

/var/log/syslog
[https://paste.ubuntu.com/p/8k4VJnYkS8/](https://paste.ubuntu.com/p/8k4VJnYkS8/)

any ideas?

====
I found smtg here not sure if it makes sense:
[https://www.reddit.com/r/thinkpad/comments/kspujw/x1_nano_wireless_not_working_in_linux/](https://www.reddit.com/r/thinkpad/comments/kspujw/x1_nano_wireless_not_working_in_linux/)

---

### Post by shizow on 2021-03-03
anyone?

---

### Post by howefield on 2021-03-03
Thread moved to the "*Networking & Wireless*" forum where you might get a bit more traction with the gurus here.

---

### Post by praseodym on 2021-03-04
Please show
```

iwconfig
sudo iwlist scan
```

---

### Post by lordgallen on 2021-03-10
My guess is that the Intel WiFi 6 adapters have been recently introduced into the kernel and that all bugs have not been worked out yet. However, let someone with a lot more experience than me chime in.

---

### Post by shizow on 2021-03-11
In the mean time i have installed kernel 5.11 and it seems more stable, but not flawless yet

$ iwconfig
lo        no wireless extensions.

wlp0s20f3  IEEE 802.11  ESSID:"halineaidar_5G"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: 80:D0:4A:96:00:CC   
          Bit Rate=702 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:70   Missed beacon:0

$ sudo iwlist scan
[https://pastebin.ubuntu.com/p/czpQG9NS7K/](https://pastebin.ubuntu.com/p/czpQG9NS7K/)

---

### Post by jeremy31 on 2021-03-11
See if disabling wifi power management helps
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

---

### Post by praseodym on 2021-03-12
And chose WPA2 instead of WPA in your router for encryption

---

### Post by shizow on 2021-03-19
> **praseodym said:**
> And chose WPA2 instead of WPA in your router for encryption

thank you. I am on many different wifis, airbnb, coworking space, etc

---

### Post by shizow on 2021-03-19
> **jeremy31 said:**
> See if disabling wifi power management helps
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

it is still a bit unstable, not sure if smtg improved

---

