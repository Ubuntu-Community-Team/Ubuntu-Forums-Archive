---
title: "rtl8822bu not working , even after modprobe"
date: 2019-01-10
forum: Networking &amp; Wireless
---

### Post by Voryzen on 2019-01-10
Hi forums,

I've been on here a lot over the last couple of days, so I figured that I would sign up, again.

I've been trying to get my [Edimax EW-7822ULC]("http://us.edimax.com/edimax/merchandise/merchandise_detail/data/edimax/us/wireless_adapters_ac1200_dual-band/ew-7822ulc/") to work on my Ubuntu 18.04 server ( I've got it in a picture frame :) )
I've found the driver from [Fomalhaut Weisszwerg's Github]("https://github.com/FomalhautWeisszwerg/rtl8822bu") and I've followed the instructions that chili555, had given chapterjason, earlier last year in another post
The issue is that, I still need to use ifconfig and dhclient to 'up' the adaptor/ installed driver, otherwise it will not connect.

Any help, would be appreciated. Fair warning, my CLI knowledge is limited, though not completely 'noob'ish.

EDIT:

I've tried putting the command I use to 'up' the usb/driver into a service, and into cron, but neither of them work.
I need the wireless to reconnect on reboot, just in case, the server gets accidentally switched off (god bless the kids)

---

### Post by chili555 on 2019-01-10
Networking in Ubuntu server 18.04 is handled by netplan. May we see your no doubt incomplete netplan file?```
cat /etc/netplan/*.yaml
```And also:```
iwconfig
```

---

### Post by Voryzen on 2019-01-11
Sure thing, chili. you the man

```

# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    ethernets:
        enp0s29f7u4:
            addresses: []
            dhcp4: true
        enp1s0:
            addresses: []
            dhcp4: true
            optional: true
    version: 2
# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    version: 2
    renderer: networkd
    ethernets:
      wlx74da38efc83b:
        addresses: [10.0.0.88/24]
        gateway4: 10.0.0.138
        nameservers:
          addresses: [10.0.0.138,8.8.8.8,8.8.4.4]
        dhcp4: false

```

```

wlx74da38efc83b  unassociated  Nickname:"rtl8822bu"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by Voryzen on 2019-01-11
Hi Chili,
It's working now, I've followed up on your netplan idea.
I've provided the code with some explanations below, so that others may be helped :)

I had issues with .YAML files, because I used tab button instead of space,
and YAML files only support spaces, not tabs

I also deleted my wpa_supplicant.conf file, as it was no longer needed.

```

network:
    version: 2
    renderer: networkd
    wifis:
      wlx74da38efc83b:
        dhcp4: false
        dhcp6: false
        addresses: [<ip address>/24] (netmask is included in this line, hence the /24)
        gateway4: <gateway ip address>
        nameservers:
          addresses: [8.8.8.8,8.8.4.4]
        access-points:
          <SSID>:
            password: <password>

```

Thanks again for your help, Chili

---

### Post by chili555 on 2019-01-11
> I've provided the code with some explanations below, I believe, in your effort to redact personal details, you have over-simplified.

For the benefit of the searchers, I believe it is:```
network:
  version: 2
  renderer: networkd
  wifis:
    wlx74da38efc83b:
      dhcp4: false
      dhcp6: false
      addresses: [192.168.1.150/24] 
      gateway4: 192.168.1.1
      nameservers:
        addresses: [8.8.8.8,8.8.4.4]
      access-points:
        "myrouter":
          password: "chi1iizd4m4n"
```Of course, substitute your details here. Note that the access point name and the password are enclosed in quotation marks ".

Reference:  /usr/share/doc/netplan.io/examples/wireless.yaml

---

