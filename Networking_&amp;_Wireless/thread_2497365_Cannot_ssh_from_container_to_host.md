---
title: "Cannot ssh from container to host"
date: 2024-05-02
forum: Networking &amp; Wireless
---

### Post by Jim_Lynch on 2024-05-02
This might not be the best forum but since it involves networking, I'm going to start here.

Running Ubuntu 20.04 on the host, Ubuntu 22.04 on the container. I installed lxd with snap. I used a macvlan profile to allow the container to get an IP from the local lan and I can reach other systems on the lan from the container and vice versa.

```

$ lxc profile list+---------+---------------------+---------+
|  NAME   |     DESCRIPTION     | USED BY |
+---------+---------------------+---------+
| default | Default LXD profile | 1       |
+---------+---------------------+---------+
| macvlan |                     | 1       |
+---------+---------------------+---------+
$ lxc profile show macvlan
name: macvlan
description: ""
config: {}
devices:
  eth0:
    nictype: macvlan
    parent: eno1
    type: nic
used_by:
- /1.0/instances/mailplus

```
 However I cannot ssh to the host. The host has a mysql database that I would like to be able to access from an app on the container. I’m trying to set up a ssh tunnel to port 3306 on the host. Any ideas? 

ssh: connect to host 192.168.2.25 port 22: No route to host
Thanks,
Jim.

---

### Post by TheFu on 2024-05-02
What are the IPs for the container and the host?
Can the container ping the host IP?

I've never used macvlan.  I use normal Linux bridges for my lxd managed lxc containers.  I have to admit, I've never tried to ssh OUT of a container to the host.  Seems to work, though I don't have any key's exchanged in that way.  Between the container and the host, why use ssh?  Why not just go direct to the MariaDB server port for the queries?  It isn't like security will be any better.  Plus, intra-machine the networking throughput should be 25-45 Gbps.

---

### Post by ian-weisser on 2024-05-02
> **Jim_Lynch said:**
> I cannot ssh to the host.

LXD containers using macvlan cannot access the host. That's just a baked-in limitation of using macvlan.
You seem to be using the wrong networking method for what you want to accomplish.

You can change to bridged networking, or you can put the host database into a different container, or you can redesign your setup some other way.

---

### Post by Jim_Lynch on 2024-05-02
The container has a dhcp furnished address of 192.168.2.105 and the host is 192.168.2.25.  Ping fails in both directions as does ssh.  I only know how to access the MariaDB port via a host:port method.  I haven't actually tried to connect the db via the port I'm guessing it won't be able to do so.  Or are you suggesting I can access the port some other way?  I'd be interested in how to share ports.  I'm not worried about security. 

Thanks,
Jim.

---

### Post by Jim_Lynch on 2024-05-02
Last time I did a bridged network it worked for a while and then  quit.  I never did figure out how to fix it or how to start over.  Seems like installing bridging is a one way street.  I had to re-image the system to get it back working.  Since then I've shied away from a traditional bridge.  

Thanks for the info on the limitations of macvlan.  

Can I share a port between  a host and a container?  I didn't think about that.  I'll have to search for that.
 
Jim.

---

### Post by TheFu on 2024-05-02
If you can't ping, then no other protocol will work either.

---

### Post by ian-weisser on 2024-05-02
Bridging and LXD became considerably easier a few years ago.

1. Set up the bridge in Netplan

In this example, the IP addresses are all set by the router (dhcp=true) merely to keep the example simple.
```

network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s7:           <---- Real-world name of the hardware interface
      dhcp4: false    <---- DON'T create a host IP address here. The host uses the Bridge IP address.
      dhcp6: false

  bridges:
    br0:                    <---- LXD needs to know this name
      interfaces: [enp0s7]  <---- Matches the name of the real hardware interface above
      dhcp4: true           <---- This bridge IP address will be used by the host
      dhcp6: true

```

2. Tell LXD to use the bridge by adding this to your LXD profile(s)

```

config: {}
devices:
  eth0:
    name: eth0       <----- Name inside the container. DON'T use the real-world interface name.
    nictype: bridged
    parent: br0      <----- Matches the actual real-world bridge name
    type: nic

```

---

### Post by TheFu on 2024-05-02
You can also set static IPs inside containers or VM, which is best to avoid DHCP failures. Those can prevent system-to-system configs from working.

---

### Post by Jim_Lynch on 2024-05-03
Thanks, I'll give that a try.  My proxy solutions don't seem to work.  Time to start over.
Jim

---

### Post by Jim_Lynch on 2024-05-03
I tend to assign static IPs from the router.  It just seems more convenient
Jim

---

### Post by TheFu on 2024-05-03
> **Jim_Lynch said:**
> I tend to assign static IPs from the router.  It just seems more convenient
Jim

Until your network is down because the router has failed.  I've seen this happen at home and in corporate environments.  Having 2000 workstations in a building down is bad. 

 Ever since that, I only use DHCP reservations for specific devices that have no other method of getting a static IP and for portable devices like tablets, phones, laptops.  Our TV tuners are network devices. They have DHCP reservations, since there's no way for my TV recording scripts to find them if they aren't at a known IP on the LAN.

I suppose everyone needs to learn this for themselves the hard way.

---

### Post by ian-weisser on 2024-05-09
> **TheFu said:**
> I suppose everyone needs to learn this for themselves the hard way.

Not at all!
My example above is intentionally simple (thereby easy for a beginner to reproduce)
I happily agree that the relying upon dhcp introduces a single-point-of-failure. A robust setup will indeed be more complex.

Folks are welcome to share more complex and robust examples. We all learn.

---

### Post by coolmike8902 on 2024-05-16
Thanks very much! I already had a bridge, but allowed it to make the new one when I ran init. Changing it to the original bridge solved the problem. Also, sorry for the late reply.

---

### Post by TheFu on 2024-05-16
If this is solved, please use the Thread Tools button and mark it SOLVED to help everyone else.

<DHCP and other Rant follows>  Mostly off-topic ... 

Just last Sunday at my local LUG, someone wasn't able to connect to his wife's computer using Samba.  He knew that the IP address had changed and wondered why.  

One of the other long-time, but Windows-centric members just said to update the IP in the /etc/hosts files across all the systems on his network and forget about.  In his mind, IP addresses don't change.

OTOH, the guy with the issue travels for multiple weeks at a time, so basically, every time he would return home, the IP addresses for the devices that left the house would change.  We tried using avahi (zeroconf) addresses, hostname.local, but those didn't work in his mixed OS environment.  

Because he's purely an end user AND they have 3 laptops used inside and outside the house, that's a perfect use of DHCP reservations.  He was comfortable editing the /etc/hosts files and completely understands the connections, so we didn't suggest using a pihole or the DNS that might be part of his router. 

We did show him how to setup DHCP reservations in the router - screen sharing the router pages so everyone learns.  We discussed his printer using a DHCP reservation and a few other devices too.  We also pointed out that if his router died, then all these systems wouldn't be able to communicate.  He set the IPs outside the DHCP range and understood why they couldn't be inside the normal DHCP range (I think).  He took notes with the caveats.  

Anyway, there are a number of networking tools for most needs.  Use them where they make sense.  For wired connections that don't move, just set the static IP inside the OS itself and either update your main /etc/hosts file or update your DNS with the IP.to ensure you don't accidentally double-use it.

I like to limit my DHCP range for guest devices to be 3x the number I ever expect - which is 2 per visitor.  So a family of 4 would need 8 DHCP guest IPs.  I also set this guest range to expire every 12 hours.  If they are still around and online, then their IPs won't change.
For my laptops/tablets/wifi devices, I have a 1 week reservation with static IPs.  These are on the needed network for the device.  IoT devices are on the "guest" network outside the secure network and firewalled off so they can't see anything else. Must be frustrating for the Roku not to see any other devices.  I know it can be frustrating for me that I can't use a tablet to interface with the roku for faster searches.  Privacy at some level has hassles and I'm willing to have those hassles.   The roku cannot see/access our other media. It is only used for DRM stuff.  Our Kodi systems are wired and on a different subnet.  Kodi doesn't send our data to any home office, unlike the roku.  We don't have any screens connected to any network. The last thing I need is a TV reporting what it hears or what we are watching to a big company.  The stand-alone roku does enough of that already.

---

