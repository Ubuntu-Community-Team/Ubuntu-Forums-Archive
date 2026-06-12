---
title: "Network bridge: physical adapter gets an IP via DHCP - but shouldn´t"
date: 2020-05-29
forum: Networking &amp; Wireless
---

### Post by crazydoc on 2020-05-29
/etc/netplan/config.yaml

```

network:
        version: 2
        renderer: networkd

        ethernets:
                enp2s0:
                        dhcp4: no
                        dhcp6: no

        bridges:
                br0:
                        interfaces: [enp2s0]
                        dhcp4: no
                        dhcp6: no
                        addresses: [10.0.0.111/24]
                        gateway4: 10.0.0.1
                        nameservers:
                                addresses: [1.0.0.1,1.1.1.1]

```

Although dhcp[46] is set to "no", the physical adapter enp2s0 gets an IP from DHCP. Dirty work-around was to purge dhcpcd5. What is the correct solution?

---

### Post by TheFu on 2020-05-30
Did you remember to run:
```
sudo netplan generate
sudo netplan apply --debug
```

The only thing I have different is ```

     parameters:
       forward-delay: 0
```
under the br0

---

### Post by crazydoc on 2020-05-30
I just did
```
netplan try
```
and then
```
netplan apply
```
as mentioned here: [http://https://www.linux.com/topic/distributions/how-use-netplan-network-configuration-tool-linux/]("http://https://www.linux.com/topic/distributions/how-use-netplan-network-configuration-tool-linux/"). Why do I need 
```
netplan generate
```

I also found this in the manual:

[B]netplan generate converts netplan YAML into configuration files understood by the backends
(systemd-networkd(8)  or  NetworkManager(8)).    It   does   not   apply   the   generated
configuration.

You  will  not  normally  need to run this directly as it is run by netplan apply, netplan
try, or at boot.[/B]

---

### Post by TheFu on 2020-05-30
And with the --debug?  Does that show issues?

---

