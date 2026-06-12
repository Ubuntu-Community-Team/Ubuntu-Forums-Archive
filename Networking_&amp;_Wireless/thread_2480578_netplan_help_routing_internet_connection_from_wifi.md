---
title: "netplan help: routing internet connection from wifi to ethernet client"
date: 2022-11-02
forum: Networking &amp; Wireless
---

### Post by surelynot on 2022-11-02
Seeking some netplan assistance!

I have an Odroid C2 running Ubuntu 22.04.1 LTS (GNU/Linux 3.16.85-65 aarch64):

internet router <&#8211;> odroid c2's wifi <&#8211;> odroid c2's ethernet <&#8211;> client using fixed ip address

**(note: I have enabled ipv4 and ipv6 forwarding in /etc/sysctl.conf)**

The ip address from the router to the odroid is dynamically set, in the 192.168.0.0 network (currently 192.168.0.154)

The ip address of the client is fixed, in the 10.0.5.0 network (10.0.5.100).


Clients connected to the wifi network can all connect to the odroid via SSH (using either root@10.0.5.1 or root@192.168.0.154), the client on ethernet can ssh to the odroid too (using either root@10.0.5.1 or root@192.168.0.154), but there's no internet connection to it.


Below is the netplan setup I have tried, referencing the 'Configuring source routing' section here:
[https://netplan.io/examples/](https://netplan.io/examples/)


```

root@odroid:~# nano /etc/netplan/99_config.yaml

network:
  version: 2
  renderer: networkd
  ethernets:
    eth0:
        dhcp4: false
        dhcp6: false
        addresses:
         - 10.0.5.1/24
        routes:
         - to: default
           via: 10.0.5.1
         - to: 10.0.5.0/24
           via: 10.0.5.1 
           table: 101
        routing-policy:
         - from: 10.0.5.0/24
           table: 101
  wifis:
    wlan0:
        dhcp4: true
        access-points:
         "network.name":
           password: "network.pwd"
        routes:
         - to: 192.168.0.0/24
           via: 192.168.0.1
           table: 102
        routing-policy:
         - from: 192.168.0.0/24
           table: 102

```

I've also tried creating routes between the two subnets and used 'metric' values to rank them, also to no avail (but I'm not sure if I am getting my to: via: and from: settings all mixed up). Here's one combination as an example:

```

root@odroid:~# nano /etc/netplan/99_config.yaml

network:
 version: 2
 renderer: networkd
 ethernets:
   eth0:
       dhcp4: false
       dhcp6: false
       addresses:
        - 10.0.5.1/24
       routes:
        - to: default
          via: 10.0.5.1
          metric: 10
          table: 101
        - to: 10.0.5.0/24
          via: 10.0.5.1 
          metric: 50
          table: 101
        - from: 10.0.5.1
          to: 192.168.0.0/24
          via: 192.168.0.1
          metric: 100
          table: 101
      routing-policy:
        - from: 10.0.5.0/24
          table: 101
  wifis:
   wlan0:
       dhcp4: true
      access-points:
        "network-name":
      password: "network-pwd"
       routes:
        - to: default
          via: 192.168.0.1
          metric: 10
          table: 102
        - to: 192.168.0.0/24
          via: 192.168.0.1
          metric: 50
          table: 102
        - to: 10.0.5.0/24
          from: 192.168.0.1
          via: 10.0.5.1
          metric: 100
          table: 102
      routing-policy:
        - from: 192.168.0.0/24
          table: 102

```

Both netplan setups result in the same routing. 

The 10.0.5.100 client shows only the ethernet network:

```

root@odroid:~# ip route | column -t
10.0.5.0/24     dev  eth0         proto  kernel  scope  link    src  10.0.5.1               

```

A client in the 192.169.0.0 subnet shows both:

```

root@odroid:~# ip route | column -t
default         via  10.0.5.1     dev    eth0    proto  static                              
default         via  192.168.0.1  dev    wlan0   proto  dhcp    src  192.168.0.154  metric  600
10.0.5.0/24     dev  eth0         proto  kernel  scope  link    src  10.0.5.1               
192.168.0.0/24  dev  wlan0        proto  kernel  scope  link    src  192.168.0.154          
192.168.0.1     dev  wlan0        proto  dhcp    scope  link    src  192.168.0.154  metric  600

```

Any help would be much appreciated!

---

### Post by SeijiSensei on 2022-11-03
You must also edit /etc/sysctl.conf and enable IP packet forwarding. Remove the hash mark from the line
```
net.ipv4.ip_forward=1
```
then reboot or run "sudo sysctl -p" to reload the configuration file.

Disabling packet forwarding by default is a security precaution on Ubuntu and other distros.

---

