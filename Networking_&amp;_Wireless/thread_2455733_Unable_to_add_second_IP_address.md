---
title: "Unable to add second IP address"
date: 2020-12-26
forum: Networking &amp; Wireless
---

### Post by stupidquestionguy on 2020-12-26
I have an Ubuntu 20.04 machine with a static IP. I want to add several more IP addresses on the same network for various docker containers but Network Manager doesn't seem to be accepting the additional addresses. I can save changes but hostname -I doesn't show the new address and if I reopen the settings the gateway box of the new IP is yellow.

Basically when I add the address Network Manager shows:
[TABLE="width: 500"]
[TR]
[TD]Address[/TD]
[TD]Netmask[/TD]
[TD]Gateway[/TD]
[/TR]
[TR]
[TD]192.168.1.2[/TD]
[TD]24[/TD]
[TD]192.168.1.1[/TD]
[/TR]
[TR]
[TD]192.168.1.3[/TD]
[TD]24[/TD]
[TD]192.168.1.1[/TD]
[/TR]
[/TABLE]

After saving and reopening it shows
[TABLE="width: 500"]
[TR]
[TD]Address[/TD]
[TD]Netmask[/TD]
[TD]Gateway[/TD]
[/TR]
[TR]
[TD]192.168.1.2[/TD]
[TD]24[/TD]
[TD]192.168.1.1[/TD]
[/TR]
[TR]
[TD]192.168.1.3[/TD]
[TD]24[/TD]
[TD]<yellow>[/TD]
[/TR]
[/TABLE]

Does anyone know why it would be behaving like this?

---

### Post by TheFu on 2020-12-26
network-manager is a toy.
For complete control you'll need to use netplan or choose a different Linux Container tool.  I know that LXD will use any Linux bridge, thus it can control which IPs it uses inside the container.  Just another option.  Linux bridges are handled by netplan too.  [https://netplan.io/](https://netplan.io/)  

There might be some config examples in these forums. Beware that netplan uses YAML files which are indentation specific - do not use tabs. To get help with netplan config, you must post here using code-tags so spaces are retained or nobody can help. [https://ubuntuforums.org/showthread.php?t=2455733](https://ubuntuforums.org/showthread.php?t=2455733)

Also, when seeking network help, we need to see the route -n and ip addresses using CLI commands.
```
route -n # or **ip route |column -t**
ifconfig  # or **ip add**
```

An example from one of my subnets
```
$ ip route |column -t
default          via  172.22.22.1  dev    br0     onlink
10.161.241.0/24  dev  lxdbr0       proto  kernel  scope   link  src  10.161.241.1
172.22.22.0/24   dev  br0          proto  kernel  scope   link  src  172.22.22.6
```
^^^^ example code tag use ^^^^^ I use a bridge here.  Alas, it is on a 16.04 server, which doesn't use netplan. Sorry.

---

### Post by stupidquestionguy on 2020-12-27
Thanks, once the host has the necessary ip addresses I can do all of the docker networking stuff I need to with docker compose, my issue is just with getting the host to "grab" the additional addresses. The host isn't Ubuntu server so it comes with Network Manager by default and I don't have physical access so I'd like to avoid switching the networking stack if possible. The Network Manager GUI clearly indicates adding an additional address is something it's supposed to be able to do so I'm not sure why it isn't working.

For completeness here's the relevant output of ip route | column -t
```

default           via  192.168.233.1    dev    eno1    proto   static  metric  100
192.168.233.0/24  dev  eno1             proto  kernel  scope   link    src     192.168.233.2  metric    100

```

---

### Post by stupidquestionguy on 2020-12-29
In case anyone from Google finds this, rebooting solved the issue.

---

