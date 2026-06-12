---
title: "Netplan config correct for Wireguard and Vxlan?"
date: 2024-01-19
forum: Networking &amp; Wireless
---

### Post by gwinterboer on 2024-01-19
I recently set this up on server 23.10 and it's the first time I've worked with netplan. 

Does this config and syntax look correct? Can I expect this to work? 

[https://pastebin.com/zz9x2q30](https://pastebin.com/zz9x2q30)

Thanks.

---

### Post by TheFu on 2024-01-19
Please don't setup a new server on a non-LTS release like 23.10.  Use 22.04 or wait until 24.04 is released.

Netplan isn't involved in wireguard configuration to my knowledge.  I've been setting up wireguard server and clients for multiple years now.  

I have a personal restriction against clicking unknown links, so I didn't look at that pastebin. netplan files usually are 20 lines, at most, so easily posted to these forums. Just use forum code-tags to maintain the spacing if you expect any help.
[Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) is a code-tag how-to.  Just use the advanced editor/reply and the (#) like you would for bold/underline/quote tags.

---

### Post by gwinterboer on 2024-01-19
Thanks for the advice. 

Here are the netplan configs. 

```

Computer 1 
network:
  version: 2
  renderer: networkd
  ethernets:
    enp1s0:
      dhcp4: true
    enp4s0:
      addresses:
        - xxx.xxx.xxx.xxx/24
      routes: 
        - to: default 
          via: 10.0.0.1
  tunnels:
    wg0:
      mode: wireguard
      port: 51820
      key: XXX
      addresses:
        - 10.0.0.1/24
      peers:
        - allowed-ips: [10.0.0.0/24]
          endpoint: xxx.xxx.xxx.xxx:51820
          keys:
            public: XXX
    vxlan0:
      mode: vxlan
      id: 100
      local:  10.8.0.1
      remote: 10.8.0.2
      port: 4789
      link: enp4s0
 
Computer 2 
 
network:
  version: 2
  renderer: networkd
  ethernets:
    enp1s0:
      dhcp4: true
    enp4s0:
      addresses:
        - xxx.xxx.xxx.xxx/24
      routes: 
        - to: default 
          via: 10.0.0.2
  tunnels:
    wg0:
      mode: wireguard
      port: 51820
      key: XXX
      addresses:
        - 10.0.0.1/24
      peers:
        - allowed-ips: [10.0.0.0/24]
          endpoint: xxx.xxx.xxx.xxx:51820
          keys:
            public: XXXX
    vxlan0:
      mode: vxlan
      id: 100
      local:  10.8.0.2
      remote: 10.8.0.1
      port: 4789
      link: enp4s0

```

---

### Post by TheFu on 2024-01-19
Does the **netplan generate** command create any warnings or errors?

As it looks, assuming those settings are supported in the netplan version  installed, [https://netplan.readthedocs.io/en/stable/examples/#how-to-connect-two-systems-with-a-wireguard-vpn](https://netplan.readthedocs.io/en/stable/examples/#how-to-connect-two-systems-with-a-wireguard-vpn) , the question now becomes is the netplan version you have one that does support it?  

Lots of specific tags in the YAML were added to different releases of netplan.  For example, the "port" in the vxlan mode section wasnt added until 0.105, which my servers don't have. They are still on 0.104.
May want to check the documentation for when each tag type was added to netplan to ensure what you are using is supported.
[https://netplan.readthedocs.io/en/stable/netplan-yaml/](https://netplan.readthedocs.io/en/stable/netplan-yaml/)

---

### Post by gwinterboer on 2024-01-19
Your first link is what I used to base this config on. 

netplan generate, and netplan apply generate returns no warnings or errors.

---

### Post by TheFu on 2024-01-19
Non-LTS Ubuntu releases, are like debian testing.  If you need a server to be solid, only deploy on an LTS and maybe even wait until the .1 LTS release if stability and having most early release bugs is critical for your needs.

Newer isn't better.

---

### Post by gwinterboer on 2024-01-28
Downgraded - netplan generate, and netplan apply generate returns no warnings or errors on 22.04.3 LTS.

---

