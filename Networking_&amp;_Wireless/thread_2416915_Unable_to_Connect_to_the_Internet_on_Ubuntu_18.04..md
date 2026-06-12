---
title: "Unable to Connect to the Internet on Ubuntu 18.04.2 LTS Server (headless)"
date: 2019-04-17
forum: Networking &amp; Wireless
---

### Post by lankanmon2 on 2019-04-17
This server is running as a VM on Unraid and has been working fine until a recent power outage caused an unexpected shutdown.


All other VMs connect to the internet fine.


Since it is headless, I am only able to connect to it via Unraids built-in VNC viewer and am not able to ssh into it since it is not connected to the network.




ifconfig returns (sorry can't copy code because of vnc):
[IMG]https://i.stack.imgur.com/Liha5.png[/IMG]



ping 8.8.4.4 returns:
connect: Network is unreachable

Looking at the interfaces file (/etc/network/interfaces) shows:
[IMG]https://i.stack.imgur.com/enDfT.png[/IMG]


and due to the lack of internet, I am unable to install or reinstall packages...


**UPDATE:**

I have since found a post on StackOverflow that helped me get the internet running. But it appears to be temporary (until next restart). 

The command that made it work is:

  sudo dhclient -v -4[URL="http://https://askubuntu.com/a/1047291/"]
https://askubuntu.com/a/1047291/[/URL]

How can I make it permanent?


Any help would be greatly appreciated!

Thank you!

---

### Post by pcfan1234 on 2019-04-18
lo is the loopback interface.
18.04 uses Netplan.
Please show the content of the folder /etc/netplan/.
There should be a .yaml-file. Show the content of this file.

---

### Post by lankanmon2 on 2019-04-18
There is a file named:
50-cloud-init.yaml

>   GNU nano 2.9.3                                                                    50-cloud-init.yaml


# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    ethernets:
        enp2s1:
            addresses: []
            dhcp4: true
            optional: true
    version: 2


---

### Post by pcfan1234 on 2019-04-18
This is how my config looks like for DHCP and the other interface with static IPv4 with Netplan:
```

  network:
  version: 2
  renderer: networkd
  ethernets:
    enp5s0:
      addresses:
        - 192.168.0.37/24
      dhcp4: no
      gateway4: 192.168.0.1
      nameservers:
          addresses: [192.168.0.1,9.9.9.9]
    enp6s0:
       dhcp4: yes


```
Maybe try this with ```
netplan try
```
If the network isn't working the changes will be automacally undone,

---

### Post by lankanmon2 on 2019-04-18
I tried that, but it failed:

```

$ sudo netplan try
Error in network definition /etc/netplan/50-cloud-init.yaml line 5 column 10: expected mapping


An error occurred: the configuration could not be generated


Reverting.
Warning: Stopping systemd-networkd.service, but it can still be activated by:
  systemd-networkd.socket

```

---

### Post by pcfan1234 on 2019-04-18
Did you use the correct device name for the interface?

---

### Post by lankanmon2 on 2019-04-18
Sorry, I am not sure how to find that. Can you please explain?

---

### Post by pcfan1234 on 2019-04-18
Try the command ```
ip link
```

---

