---
title: "Where / How to change DNS Servers in v18.04"
date: 2020-03-05
forum: Networking &amp; Wireless
---

### Post by Rick St. George on 2020-03-05
I'm trying to figure out how to change and get rid of Google tracking crap and Mozilla's change to utilize ONLY CloudFlare DNS servers. So much conflicting info, and there is nothing in my NetPlan folder. So just how can we find out what is changing, modifying, utilizing other cross-scripts etc. on our computers?  Ran the following;  

```
 
~$ nmcli device status DEVICE  TYPE      STATE        CONNECTION  wlan0   wifi      connected    FBIvan7     eth0    ethernet  unavailable  --          lo      loopback  unmanaged    --           

~$ ip r default via 192.168.20.1 dev wlan0 proto dhcp metric 600  192.168.20.0/24 dev wlan0 proto kernel scope link src 192.168.20.57 metric 600

~$ nmcli device show wlan0 | grep IP4.DNS IP4.DNS[1]:                             204.194.234.200 IP4.DNS[2]:                             68.28.195.135   

~$ sudo dpkg -s netplan.io Package: netplan.io Status: install ok installed Priority: optional Section: net Installed-Size: 242 Maintainer: Ubuntu Developers  Architecture: amd64 Multi-Arch: foreign Version: 0.98-0ubuntu1~18.04.1 Replaces: nplan (= 2.27), libglib2.0-0 (>= 2.33.14), libsystemd0 (>= 221), libuuid1 (>= 2.16), libyaml-0-2, iproute2, python3, python3-yaml, python3-netifaces, systemd (>= 235-3ubuntu3) Suggests: network-manager | wpasupplicant Breaks: network-manager 
```

---

### Post by SeijiSensei on 2020-03-06
[https://ubuntuforums.org/showthread.php?t=2437948&p=13937037&viewfull=1#post13937037](https://ubuntuforums.org/showthread.php?t=2437948&p=13937037&viewfull=1#post13937037)

---

