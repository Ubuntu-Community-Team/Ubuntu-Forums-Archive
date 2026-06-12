---
title: "ubuntu server 22.04 netplan conf does not apply, no internet access"
date: 2024-04-30
forum: Networking &amp; Wireless
---

### Post by relikhunter on 2024-04-30
hi, i've already installed locally on my company an internal server and i wanna try monitoring other devices with some suites...
I started first with the official docs but i know sometimes lacks a bit... and my objective now is trying to connect on a mirror to download packages for a mail server, but pinging google.com it says "ping: [www.google.it:](www.google.it:) Temporary failure in name resolution".
If you are interested in my setup of Netplan, here it is:

------------------------
network:
  version: 2
  renderer: networkd
  ethernets:
    enp2s0:
    # dhcp4: true
      dhcp4: false
      addresses:
        - 192.168.100.96/16
      routes:
        - to: default
          via: 192.168.1.254
      nameservers:
        addresses:
          - 192.168.1.211
          - 8.8.8.8
-------------------------

and it's applied well as I check by "netplan get" but when i call " ip a " what i see is a default configuration with dhcp enabled, which i don't want obviously, so netplan does not apply my conf.
Does Ubuntu server allows to prioritise or switch trough network configuration systems?

Thanks

---

### Post by TheFu on 2024-04-30
You must post netplan files using forum code tags.  Otherwise, it is useless. [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)

BTW, that's a huge subnet. Inside a company, I've never seen won that large. It will make for a slow network to allow 65K IPs in the subnet.  Typically, companies use a /20 subnet per building, which is still big - 4096 IPs.  When something bad happens, it will be hard to segment off the problem so the rest of the company can keep working.

These are the required netplan commands to have it applied after any changes:
```
sudo netplan generate --debug
sudo netplan apply
```

---

### Post by relikhunter on 2024-05-06
seems to be a mix of configurations like netplan and systemd-resolved at the moment , it's weird how much it's messy trying to learn into web, thousand of tutorials which arise thousand of problems ahahha
Hard to find someone with a little of experience on field.
Anyway i cannot manage the entire network, that's it folks! btw everything works now, next step will be installation and testing of a mail server....
Byebye.

[https://wiki.archlinux.org/title/systemd-resolved#](https://wiki.archlinux.org/title/systemd-resolved#)

[https://www.howtoforge.com/ubuntu-22-04-minimal-server/](https://www.howtoforge.com/ubuntu-22-04-minimal-server/)

---

