---
title: "How to set custom DNS servers and use DHCP on kubuntu 20.04 using netplan config?"
date: 2020-07-08
forum: Networking &amp; Wireless
---

### Post by codecando-x on 2020-07-08
I  am only able to set custom DNS servers using the  /etc/netplan/01-network-manager-all.yaml if i use the configuration below  with a static IP address:

 ```
d@a:~$ more /etc/netplan/01-network-manager-all.yaml 
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
  wifis:
    wlp3s0:
      dhcp4: false
      addresses: [10.0.0.49/24]
      gateway4: 10.0.0.1   
      access-points:
        accesspointename:
          password: passwordgoeshere
      nameservers:
        addresses: [8.8.4.4,8.8.8.8,1.1.0.0,1.1.1.1]
```

 The configuration above works, Network Manager restarts after issuing sudo netplan --debug apply, there is a new connection that is created with the same name as my original access point but prepended with netplan-wlp3s0.


 I would like not to use a static IP address. When i try the below  configuration to set custom DNS servers and have DHCP enabled. No new connection is created and the original one has the  service providers DNS servers.
```

 d@a:~$ more /etc/netplan/01-network-manager-all.yaml 
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
  wifis:
    wlp3s0:
      dhcp4-overrides:
        use-dns: no
      access-points:
        accesspointname:
          password: passwordgoeshere
      nameservers:
        addresses: [8.8.4.4,8.8.8.8,1.1.0.0,1.1.1.1]

d@a:~$ sudo netplan --debug apply
** (generate:11280): DEBUG: 22:03:24.251: Processing input file /etc/netplan/01-network-manager-all.yaml..
** (generate:11280): DEBUG: 22:03:24.251: starting new processing pass
** (generate:11280): DEBUG: 22:03:24.251: wlp3s0: adding wifi AP 'accesspointname'
** (generate:11280): DEBUG: 22:03:24.252: We have some netdefs, pass them through a final round of validation
** (generate:11280): DEBUG: 22:03:24.252: wlp3s0: setting default backend to 2
** (generate:11280): DEBUG: 22:03:24.252: Configuration is valid
** (generate:11280): DEBUG: 22:03:24.252: Generating output files..
** (generate:11280): DEBUG: 22:03:24.252: networkd: definition wlp3s0 is not for us (backend 2)
(generate:11280): GLib-DEBUG: 22:03:24.252: posix_spawn avoided (fd close requested) 
DEBUG:no netplan generated networkd configuration exists
DEBUG:netplan generated NM configuration changed, restarting NM
DEBUG:wlp3s0 not found in {}
DEBUG:Merged config:
network:
  bonds: {}
  bridges: {}
  ethernets: {}
  vlans: {}
  wifis:
    wlp3s0:
      access-points:
        accesspointname:
          password: passwordgoeshere
      dhcp4-overrides:
        use-dns: false
      nameservers:
        addresses:
        - 8.8.4.4
        - 8.8.8.8
        - 1.1.0.0
        - 1.1.1.1

DEBUG:Skipping non-physical interface: lo
DEBUG:Skipping non-physical interface: enp0s25
DEBUG:{}
DEBUG:netplan triggering .link rules for lo
DEBUG:netplan triggering .link rules for enp0s25
DEBUG:netplan triggering .link rules for wlp3s0
```

 How can i keep DHCP on and use custom DNS servers?

 Thanks

---

### Post by TheFu on 2020-07-08
dhcp4: true?
and remove all the connection-specific stuff.
But wifi connections are where the network-manager gui/tui would work better than a netplan-yaml file.

---

### Post by chili555 on 2020-07-08
> **TheFu said:**
> dhcp4: true?
and remove all the connection-specific stuff.
But wifi connections are where the network-manager gui/tui would work better than a netplan-yaml file.Indeed! If Network Manager is installed and running, it is trivial and simple to do what you want here. 

[IMG]https://i.postimg.cc/sfHq9qGP/Screenshot-from-2020-07-08-11-20-54.png[/IMG]

If so, revert the changes to netplan:

```
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
```If NM is not running here, if for example, this is a headless server, then you surely don't to declare NM as the renderer:

> renderer: NetworkManager



---

### Post by SeijiSensei on 2020-07-08
For recent versions that use systemd, I find it works best to add the nameserver IPs to the DNS and FallbackDNS lines in /etc/systemd/resolved.conf. Run "sudo systemctl restart systemd-resolved" after changing that file.

---

### Post by codecando-x on 2020-07-08
> **TheFu said:**
> dhcp4: true?
and remove all the connection-specific stuff.
But wifi connections are where the network-manager gui/tui would work better than a netplan-yaml file.

So i modified my netplan config to this:
```

network:
  version: 2
  renderer: NetworkManager
  wifis:
    wlp3s0:
      dhcp4: true
      access-points:
        accesspointgoeshere:
          password: passwordgoeshere
      nameservers:
        addresses: [8.8.4.4,8.8.8.8,1.1.0.0,1.1.1.1]
```

However then when i run: nmcli dev show | grep DNS
The service providers DNS servers are before the custom ones i have defined:
```
IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
IP4.DNS[3]:                             8.8.4.4
IP4.DNS[4]:                             8.8.8.8
IP4.DNS[5]:                             1.1.0.0
IP4.DNS[6]:                             1.1.1.1
```

I understand i could do it in Network Manager, i am however looking for a config file solution so that i can script it. Does netplan support this configuration?

Thanks

---

### Post by TheFu on 2020-07-08
Google found this: [https://bugs.launchpad.net/netplan/+bug/1759014](https://bugs.launchpad.net/netplan/+bug/1759014)
```
        ens3:
            dhcp4: true
            dhcp4-overrides:
                use-dns: false
```
There were complaints that doesn't work, though something was being passed to systemd-resolved.
Some people had it working.  Others did not.

---

### Post by SeijiSensei on 2020-07-09
> **codecando-x said:**
> I understand i could do it in Network Manager, i am however looking for a config file solution so that i can script it.
Why doesn't [rewriting the resolved.conf file](https://ubuntuforums.org/showthread.php?t=2446865&p=13971152&viewfull=1#post13971152) fulfill this requirement?  Your script could simply overwrite the default resolved.conf with a version that includes the servers' IP addresses, or it could use something like sed to rewrite the DNS= and FallbackDNS= lines in resolved.conf.

---

### Post by codecando-x on 2020-07-09
> **SeijiSensei said:**
> Why doesn't [rewriting the resolved.conf file]("https://ubuntuforums.org/showthread.php?t=2446865&p=13971152&viewfull=1#post13971152") fulfill this requirement?  Your script could simply overwrite the default resolved.conf with a version that includes the servers' IP addresses, or it could use something like sed to rewrite the DNS= and FallbackDNS= lines in resolved.conf.

It doesn't seem to work either, the only way so far i have been able to set custom servers is if i use a static IP address through netplan config or adding the DNS servers by hand into the Network Manager UI. Both of those scenarios are not scriptable, since i have to know the address ahead of time and then i also have to be able to automate the UI or look for the Network Manager config files.

```
$ sudo more /etc/systemd/resolved.conf #  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.
#
# Entries in this file show the compile time defaults.
# You can change settings by editing this file.
# Defaults can be restored by simply deleting this file.
#
# See resolved.conf(5) for details


[Resolve]
DNS=1.1.1.1 1.1.0.0 2606:4700:4700::1111 2606:4700:4700::1001
FallbackDNS=8.8.4.4 8.8.8.8 2001:4860:4860::8888 2001:4860:4860::8844
#Domains=
#LLMNR=no
#MulticastDNS=no
DNSSEC=yes
#DNSOverTLS=no
#Cache=yes
#DNSStubListener=yes
#ReadEtcHosts=yes

```
After i run:  ```
sudo systemctl restart systemd-resolved 

```

Then i run:  ```
nmcli dev show | grep DNS

IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
IP6.DNS[1]:                             2001:558:feed::1
IP6.DNS[2]:                             2001:558:feed::2





```

Nameservers are still set to the ISP defaults. :(

---

