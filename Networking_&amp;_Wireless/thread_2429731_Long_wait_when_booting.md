---
title: "Long wait when booting"
date: 2019-10-22
forum: Networking &amp; Wireless
---

### Post by makem2 on 2019-10-22
I am using Ubuntu 18.04 LTS Bionic Beaver on a Raspberry Pi3.

The onboard wifi chip has been disabled and instead I am using an external wifi dongle.

When the Pi is booted it waits for a long time (2mins?) before an error is produced and boot continues successfully. Wifi is then available.

The error states, "A start job is running for wait for network to be configured (1min 51s / no limit)" and continues with a "Failed to start................" I think it refers to the start job.

Networking is set up with Netplan 50-cloud-init.yaml as follows:

```

network:
    version: 2
    ethernets:
        eth0:
            dhcp4: true
            match:
                macaddress: b8:27:eb:81:46:0e
            set-name: eth0

network:
  version: 2
  renderer: networkd
  wifis:
    wlan0:
      dhcp4: no
      dhcp6: no
      addresses: [192.168.2.134/24]
      gateway4: 192.168.2.1
      nameservers:
        addresses: [192.168.2.1, 8.8.8.8]
      access-points:
        "xxxxxxxxxxxx_2.4GHz":
          password: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"

```

Is such a long wait normal or are my wireless settings incorrect?

I have suffered a lot of settings resets due to the onboard wifi chip not being usable and may have left a mess that has to be followed through by the system I suppose.

wireless-info.txt:

[http://paste.ubuntu.com/p/KQrZrScNwZ/](http://paste.ubuntu.com/p/KQrZrScNwZ/)

---

### Post by Skaperen on 2019-10-25
it's possibly trying to lookup a host name for an address which will fail.  the time is how long it waits multiplied by the number of times it tries.  for each address you have, put a line in [COLOR=#0000cd][FONT=courier new]**/etc/hosts**[/FONT][/COLOR] for it.  maybe it will find them there instead of waiting on DNS response from nowhere.  or, it could be waiting for something else.

---

