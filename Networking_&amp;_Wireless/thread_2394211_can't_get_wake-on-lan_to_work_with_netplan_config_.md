---
title: "can't get wake-on-lan to work with netplan config file"
date: 2018-06-14
forum: Networking &amp; Wireless
---

### Post by paulgj on 2018-06-14
Hello,

installed Ubuntu Server 18.04.   Trying to set up my network card for WOL.   I changed the 50-cloud-init.yaml file in /etc/netplan to include the [FONT=Courier New]wakeonlan: true[/FONT] line but after rebooting still not getting the "g" option in the *Wake-on* attribute when I do sudo ethtool on the adapter (the Supports Wake-on line indicated that "g" is supported).

also tried [FONT=Courier New]sudo netplan apply[/FONT] after changing the file with no change

I've had WOL working in an older release of Ubuntu Server when the method involved adding the [FONT=Courier New]**up ethtool -s eth0 wol g**[/FONT] command to /etc/network/interfaces

stumped as what to try next.

Any help gratefully accepted
-Paul

---

### Post by paulgj on 2018-06-15
I tried creating a new config.yaml file in /etc/netplan with the following content, but still refuses to give the adapter the wol "g" attribute. 

```
network:
    version 2:
    renderer: networkd
    ethernets:
       enp2s0:
          dhcp4: true
          wakeonlan: true
```

Am hoping someone with expertise in netplan could update the [wakeonlan help page]("https://help.ubuntu.com/community/WakeOnLan") to show how to do this under netplan instead of ifupdown.

Thanks!

---

### Post by cariboo on 2018-06-15
It looks like your spacing may be off. yaml files are space sensitive. Try:

```
network:
  version 2:
  renderer: networkd
  ethernets:
    enp2s0:
      dhcp4: true
      wakeonlan: true
```

I use[ Sublime Text]("https://www.sublimetext.com/") to edit .yaml files

---

### Post by paulgj on 2018-06-16
thanks for the suggestion. I deleted and recreated the config file as 01-netcfg.yaml and just using the up and down keys made sure that the file exactly matched your suggestion.  

Unfortunately still no luck in getting the WOL attribute set in the adapter. Not sure what to look at next.  Is there a log that would show if netplan parsed the file correctly?

Thanks!

---

### Post by paulgj on 2018-06-19
FYI, I got it working by adding the **macaddress **match lines, here is the full .yaml file:

```

network:
  version: 2
  renderer: networkd
  ethernets:
    enp2s0:
      match:
        macaddress: 50:e5:49:b3:fc:97
      dhcp4: true
      wakeonlan: true

```

---

