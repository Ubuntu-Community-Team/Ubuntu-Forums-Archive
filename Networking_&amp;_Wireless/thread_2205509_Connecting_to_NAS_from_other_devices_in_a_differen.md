---
title: "Connecting to NAS from other devices in a different subnet?"
date: 2014-02-14
forum: Networking &amp; Wireless
---

### Post by tomcrawf90 on 2014-02-14
Hi,

I am wondering if anyone can help with my setup.

I have an Ubuntu server with 2 NICS. eth0 connects to the internal network and internet. eth1 connects to a switch with my NAS connected to it. (nothing else connects to this switch)

These are my basic settings.

eth0 ip address: 192.168.30.10
gateway: 192.168.30.1

eth1 ip address: 192.168.20.10

nas ip address: 192.168.20.20

This works fine from the Ubuntu server and it has full access to the nas but i would also like other devices on the 192.168.30.0 network to connect to the nas if required. Is there anyway of doing this?

Thanks in advance.

Tom


I would like to be able to directly connect to the NAS from all the devices on the network.

---

### Post by tgalati4 on 2014-02-14
You have set up a class C network.  Your network mask should be 255.255.0.0.  Make sure all of your machines have that netmask and then reboot everything including the routers/switches.

If this does not work out-of-the-box, then you may have to set up a static route on those machines that you are having trouble with using *route*.

```
man route
```

Excerpt:

       route add -net 192.56.76.0 netmask 255.255.255.0 dev eth0
              adds a route to the local network 192.56.76.x via "eth0".  The word "dev" can be omitted here.

So your command might be:

```
sudo route add -net 192.168.20.0 netmask 255.255.0.0
```

But you would only have to do that on machines that you are having trouble with connecting to your NAS.

For more complicated routing look at your dhcp server:  [https://help.ubuntu.com/community/isc-dhcp-server](https://help.ubuntu.com/community/isc-dhcp-server) or  [https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)

---

