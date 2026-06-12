---
title: "Kubuntu 17.10 configure static IP for wired interface"
date: 2018-02-05
forum: Networking &amp; Wireless
---

### Post by gus_zernial on 2018-02-05
I have a *Kubuntu* 17.10 64-bit box, and wired networking interfaces default to and work with DHCP. But I need a static IP for this system, and can't figure out how to configure it. System Settings Network Connections won't let me set up and Apply settings for a static interface - apparently because there's a change in 17.10 to netplan yaml config files. I've tried setting up the yaml config file using examples of static configs found by googling, but they all fail "netplan --debug generate" with syntax errors and don't bring up the wired interface on reboot

Can someone tell me either what tool to use for configuring a wired static interface, or post a working yaml configuration file for my configuration.

Thx, Gus

---

### Post by wyliecoyoteuk on 2018-02-06
Something like this.
Be aware that correct indentation is mandatory, and it won't let you use tabs, you must use spaces.
That caught me out when I tried it.

named /etc/netplan/01-systemd-networkd-eth.yaml
```

network:
version: 2
ethernets:
  enp0:
   match:
      name: enp0s3
        addresses: [192.168.0.128/24]
        gateway4: 192.168.0.1
        nameservers:
            addresses: [8.8.8.8,8.8.4.4]

```

This may help also.
[https://websiteforstudents.com/configuring-static-ips-ubuntu-17-10-servers/](https://websiteforstudents.com/configuring-static-ips-ubuntu-17-10-servers/)

---

### Post by wyliecoyoteuk on 2018-02-06
Here is my test web server's yaml

you can find your ethernet device name using  ifconfig

 /etc/netplan/01-netcfg.yaml

```

# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s20:
      dhcp4: no
      addresses: [192.168.0.116/24]
      gateway4: 192.168.0.1
      nameservers:
         addresses: [8.8.8.8,8.8.4.4]



```

---

### Post by chili555 on 2018-02-06
I believe that wyliecoyoteuk's answer is quite correct for a server. However, if you have and are trying to configure System Settings > Network Connections suggests that you have a desktop installation, not a server. In that case,  System Settings > Network Connections is the correct way to set a static IP address. Usually, the reason that you can't set and save the settings is that the system thinks one of the settings is either missing or wrong.

My configuration is this:

[ATTACH=CONFIG]278463[/ATTACH]
How does yours compare?

---

### Post by clepsdyrae on 2018-03-30
Kubuntu's NetworkManager appears to be buggy. See here: [https://www.kubuntuforums.net/showthread.php/72529-Network-Manager-bug](https://www.kubuntuforums.net/showthread.php/72529-Network-Manager-bug)

I could only set up a static IP by using nmtui, which was pretty painless.

---

