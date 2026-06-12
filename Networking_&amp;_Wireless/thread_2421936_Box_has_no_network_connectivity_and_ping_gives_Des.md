---
title: "Box has no network connectivity and ping gives Destination Host Unreachable"
date: 2019-06-29
forum: Networking &amp; Wireless
---

### Post by entwere on 2019-06-29
Hey, I'm hoping someone could help me as I'm quite new to Ubuntu and Linux in general.

I have Ubuntu box rented and I logged on the other day to discover there were DNS resolution issues so I followed the instructions here; [https://stackoverflow.com/questions/53687051/ping-google-com-temporary-failure-in-name-resolution](https://stackoverflow.com/questions/53687051/ping-google-com-temporary-failure-in-name-resolution) however after this the network did not appear to come back up.  When I logged in over KVM, Netplan appears to have reset the /etc/netplan/01-netcfg.yaml.  I've got the following information from my host;

[TABLE="width: 500"]
[TR]
[TD="align: center"]IP[/TD]
[TD="align: center"]Gateway[/TD]
[TD="align: center"]Subnet[/TD]
[TD="align: center"]Custom MAC[/TD]
[/TR]
[TR="class: rs-list-item"]
[TD="align: center"]199.127.61.221[/TD]
[TD="align: center"]199.127.61.1[/TD]
[TD="align: center"]255.255.255.0[/TD]
[TD="align: center"]-[/TD]
[/TR]
[TR="class: rs-list-item"]
[TD="align: center"]172.93.101.15[/TD]
[TD="align: center"]172.93.101.1[/TD]
[TD="align: center"]255.255.255.0[/TD]
[TD="align: center"]-[/TD]
[/TR]
[/TABLE]

I have the following YAML configuration;

```

network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s25:
      addresses: [ 199.127.61.221/24, 172.93.101.15/24 ]
      gateway: 199.127.61.1
      nameservers:
        addresses: [ 1.1.1.1, 1.0.0.1 ]
        search: [ dylanw.net ]

```

Since I can only access the box over KVM, I've got this by flicking between windows so although I've double checked it, it might have some small issues but netplan apply doesn't show any errors.

I can't ping anything, ping 8.8.8.8 gives

[IMG]https://i.imgur.com/nggnE3Q.png[/IMG]

and ping google.com gives;

[IMG]https://i.imgur.com/qCbrTzC.png[/IMG]

The result of ifconfig -a > out is;

[IMG]https://i.imgur.com/UdF5d3t.png[/IMG]

[IMG]https://i.imgur.com/YyGdw0N.png[/IMG]

route -n

[IMG]https://i.imgur.com/Um5RJXN.png[/IMG]

ip addr

[IMG]https://i.imgur.com/oqplgCz.png[/IMG]

Sorry if I've left out some important information, I've tried to get what I know will be needed I can give more information if that's needed.

Thanks in advance!

---

### Post by The Cog on 2019-06-29
Some of your command output seems to have disappeared. Still, let's go for some basics. Can you post the output of the commands "ip addr" and "ip route" to start the troubleshooting.

P.S. Welcome to the forums.

---

### Post by entwere on 2019-06-29
Hi there, thanks! :)

Below is the output to the commands;

[IMG]https://i.imgur.com/SPcmRcZ.png[/IMG]


[IMG]https://i.imgur.com/loUnTYQ.png[/IMG]

---

### Post by The Cog on 2019-06-29
OK, the link is up and you have a default route through it. The default gateway is 199.127.61.1. Looks good so far. But your ping says unreachable, and that seems to be coming from your own interface. Can you try these two commands:
```
ping 199.127.61.1
ip nei
```
Try the ping first, then list the neighbour information. If the ping doesn't work, I want to see if you have a good arp entry for it afterwards.

---

### Post by entwere on 2019-06-29
Thanks!  Here is the result of the ping command;

[IMG]https://i.imgur.com/MqP4y1m.png[/IMG]

...and here is the result of the neighbour information;

[IMG]https://i.imgur.com/t1n2KOS.png[/IMG]

---

### Post by The Cog on 2019-06-29
OK, so your default gateway is no longer there. You can't use it to forward packets if it's not there. I think you need to talk to the network admins (or whoever told you originally that should be the default gateway address) and find out what's going on.

---

### Post by entwere on 2019-06-29
Hi, thanks for your help.  I'll contact my host about this.

---

