---
title: "QCA6174 connectivity full to limited randomly"
date: 2018-10-21
forum: Networking &amp; Wireless
---

### Post by gongshu on 2018-10-21
My Wifi goes from connectivity full to limited without any apparent reasons:
```
:~$ nmcli general
STATE      CONNECTIVITY  WIFI-HW  WIFI     WWAN-HW  WWAN    
connected  full          enabled  enabled  enabled  enabled 
```

```
:~$ nmcli general
STATE                  CONNECTIVITY  WIFI-HW  WIFI     WWAN-HW  WWAN    
connected (site only)  limited       enabled  enabled  enabled  enabled 
```

When this happens I can see the wifi icon turning in an interrogation mark and only currently open connections stay open.
Any new connection will resolve in 404.

Information of my hardware:
```
:~$ sudo lshw -C network
  *-network
       description: Wireless interface
       product: QCA6174 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:3e:00.0
       logical name: wlp62s0
       version: 32
       serial: xx:xx:xx:xx:xx:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=4.15.0-36-generic firmware=WLAN.RM.4.4.1-00079-QCARMSWPZ-1 ip=192.168.1.81 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:135 memory:dd200000-dd3fffff

```

I'm on an updated Ubuntu 18.04.
This was not happening with my previous version of Ubuntu (I re-formatted from scratch not long ago).
The router is still the same and in Windows with the same machine I do not have any issue.

My guess is the driver I am using, but I am not sure.

```
:~$ sudo lsmod | grep ath10k
ath10k_pci             45056  0
ath10k_core           360448  1 ath10k_pci
ath                    28672  1 ath10k_core
mac80211              778240  1 ath10k_core
cfg80211              622592  3 mac80211,ath,ath10k_core
```

Any idea?
Thanks

---

### Post by wildmanne39 on 2018-10-21
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by jeremy31 on 2018-10-22
See the wireless script link in my signature and post results

---

### Post by gongshu on 2018-10-24
> **jeremy31 said:**
> See the wireless script link in my signature and post results

Thanks Jeremi
here the [pastebin]("https://paste.ubuntu.com/p/NJd8fwmcPQ/")

---

### Post by jeremy31 on 2018-10-24
Do ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Reboot, these wifi cards don't have a module that handles power management very well

---

### Post by gongshu on 2018-10-24
Thanks Jeremy
I've just executed the command, from my understanding it was just turning off the power management.

I will give it try and let you know! 
Thanks for the suggestion.

---

### Post by gongshu on 2018-11-04
> **jeremy31 said:**
> Do ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Reboot, these wifi cards don't have a module that handles power management very well

Hi @jeremy31
As you can see, power save is set at 2 now (I restarted the laptop).
```
:~$ cat /etc/NetworkManager/conf.d/*
[connection]
wifi.powersave = 2

```
I've been using the laptop for few days and I keep keep having the same issue with the same frequency.

Any other ideas?

---

