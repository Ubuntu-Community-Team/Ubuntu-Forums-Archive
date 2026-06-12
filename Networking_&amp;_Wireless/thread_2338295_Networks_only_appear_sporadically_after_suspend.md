---
title: "Networks only appear sporadically after suspend"
date: 2016-09-26
forum: Networking &amp; Wireless
---

### Post by jdkcarlson on 2016-09-26
Hi. I'm the same person as in the threads [https://ubuntuforums.org/showthread.php?t=2316533](https://ubuntuforums.org/showthread.php?t=2316533) and [https://ubuntuforums.org/showthread.php?t=2329006](https://ubuntuforums.org/showthread.php?t=2329006) in case that helps, running Ubuntu 16.04 on a Acer Aspire R5-471T.

With regularity, after my laptop comes back from suspend, it fails to detect the **majority** (but generally **not all**) of the wi-fi networks around it (including the network I was on before suspend). Disabling and re-enabling networking does nothing; the same networks are detected. If one does Connect to Hidden Wi-Fi Network, then one can see the desired network, but if one selects it, the Connect button will be grayed out.

If I'm lucky, suspending and resuming again solves this problem, but most of the time, I need to restart to have the option to select my preferred network again. How can I fix this?

---

### Post by jeremy31 on 2016-09-26
Post the result of ```
iwconfig; lshw -c net
``` after a resume from suspend.  If needed you can route the output to a text file using ```
iwconfig; lshw -c net > info.txt
```
And the info.txt will be in your home folder after a reboot so you can post the results

---

### Post by jdkcarlson on 2016-10-01
Okay, I waited until the problem recurred. Here's the feedback when it only detects irrelevant networks:

```
  *-network
       description: Wireless interface
       product: QCA6174 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 32
       serial: 30:52:cb:14:9b:cd
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=4.4.0-38-generic firmware=WLAN.RM.2.0-00180-QCARMSWPZ-1 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:127 memory:a1000000-a11fffff
```

and here is the feedback after restart

```
  *-network
       description: Wireless interface
       product: QCA6174 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 32
       serial: 30:52:cb:14:9b:cd
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=4.4.0-38-generic firmware=WLAN.RM.2.0-00180-QCARMSWPZ-1 ip=192.168.1.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:127 memory:a1000000-a11fffff
```

The only difference seems to be that now I have an IP address!

---

### Post by jeremy31 on 2016-10-11
Does ```
iwconfig
``` show power management being on when you have the issue?

You may want to change this file anyway
```
sudo -H gedit /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```


This contains:
```
[connection]
wifi.powersave = 3
```

Change the 3 to 0 then save and reboot

Some Linux Mint user found this and posted it [https://ubuntuforums.org/showthread.php?t=2339523](https://ubuntuforums.org/showthread.php?t=2339523)  I do have this file on my Ubuntu laptop but it doesn't allow power management settings to be changed due to the ath9k module parameter preventing changes.  I read the bug report that caused this file and the intention was for it to enable power management on wifi only when using battery power but what I have seen recently doesn't agree

---

### Post by jdkcarlson on 2017-01-18
Hi Jeremy,

Sorry to never have responded. For what it's worth, I did this, but it doesn't seem to help on my machine for whatever reason. :/

---

### Post by jeremy31 on 2017-01-18
Actually I have found that setting it to 0 might not help any, try this command
```
sudo sed -i 's/wifi.powersave = 0/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

Reboot

---

