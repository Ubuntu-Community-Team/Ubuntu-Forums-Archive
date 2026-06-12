---
title: "need help config 3945abg wireless card"
date: 2006-08-09
forum: Networking &amp; Wireless
---

### Post by nymphaeles on 2006-08-09
I have Dapper 6.06 installed in a laptop HP DV5000 with intel pro 3945 wireless card.  To enable wireless networking, I started out with installing network-manager-gnome and that went OK.  Then I went ahead and reboot the machine.  After the reboot, network manager is up and running OK.  It detects my AP fine; however, it doesn't seem to take my passphrase.  Here are some console output for a couple of troubleshooting tools

lshw output
```

...

*-network
    description: Wireless interface
    product: Intel Corporation
    vendor: Intel Corporation
    physical id: 0
    bus info: pci@06:00.0
    logical name: eth1
    version: 02
    serial: 00:13:02:53:e8:27
    width: 32 bits 
    clock: 33MHz
    capabilities: bus_master cap_list ethernet physical wireless
    configuration: broadcast=yes driver=ipw3945 driverversion=1.0.5m firmware=13.0 1:0 () link=yes
...

```


iwconfig output
```

...
eth1      IEEE 802.11g  ESSID:"xxxxxxxx"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx   Security mode:open
          Power Management:off
          Link Quality=88/100  Signal level=-44 dBm  Noise level=-45 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:181   Missed beacon:0
...


```

On my AP, SSID broadcast is on, encryption is WPA (PKS), WPA1 & WPA2 mode are both supported, WPA algorithm is RC4 (TKIP) & AES.

Because iwconfig shows Security mode = open, I suspect that it is misconfigured. The question is what I need to do to correct it.  Are there any configuration files that work with network-manager-gnome?

Thanks in advance for your repsponse.

---

