---
title: "Another broadcom - ndiswrapper - wpa_supplicant problem"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by super-user on 2007-04-26
Hi,

I've been reading several posts about wireless networking in feisty. Since I updated to feisty wireless networking does not work for me. I have a Broadcom Wireless Networking card 4306 in a HP Compaq nx9105 which was working perfectly with ndiswrapper, wpa_supplicant and NetworkManager until last week.

Here is some info at first:

```

$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320:103C:12F4) present (alternate driver: bcm43xx)
        device (14E4:4320) present (alternate driver: bcm43xx)

```

```

$ lsmod | grep ndiswrapper
ndiswrapper           194608  0

```

```

$ cat /etc/wireless/wpa_home.conf 
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
network={
        ssid="my network"
        psk=very long number generated with wpa_passphrase
        key_mgmt=WPA-PSK
        proto=WPA
        priority=1
        group=CCMP TKIP
}

```

Having all these problem I remove NetworkManager and started using the /etc/network/interfaces again which looks like this:

```

iface wlan0-home inet dhcp                                                                                                                                     
    wpa-driver ndiswrapper                                                                                                                                     
    wpa-conf /etc/wireless/wpa_home.conf

```

The previous version of this section does not work as well:

```

iface wlan0-home inet dhcp                                                                                                                                    
   pre-up  /sbin/wpa_supplicant -Bw -D ndiswrapper -i wlan0 -c /etc/wireless/wpa_home.conf                                                                    
   post-down killall -q wpa_supplicant

```

When I run wpa_supplicant on the console I noticed the following error: **"Association request to the driver failed"**. The only thing I see in the logs is **"[2007/04/26 14:35:56] info kern kernel: [ 3483.952000] ADDRCONF(NETDEV_UP): wlan0: link is not ready"**.

When I try to ifup the interface everything looks ok except that I never get an ip address from my dhcp router...

Does anyone have a clue what I am missing here?

Thanks in advance!

---

