---
title: "Can't get persistent static route to work in /etc/network/interfaces - help please ?"
date: 2021-02-27
forum: Networking &amp; Wireless
---

### Post by radiance32 on 2021-02-27
Hi all,

I'm new here, just registered, My name is Terrence (aka radiance32).

I'm setting up Ubuntu LTS on an arm based SBC with 2 ethernet interfaces (one public connected to the internet, and one private, for backend SQL access and administration.
I've set everything up and it all works great,
but, I need to add a static route to one of my home networks so i can access the server via the 2nd interface for administration services.

If i add the route manually, it works and I can have access from my 10.0.0.0/24 network:

> > route add -net 10.0.0.0 netmask 255.255.255.0 gw 10.0.100.10

But, as you all know, static routes created with the route command aren't persistent and dissapear after a reboot.
So, according to the documentation, I added the static route with the "up" in front of it, to the end of my /etc/network/interfaces,
here is my /etc/network/interfaces:

> auto lo
iface lo inet loopback


# network interface eth0
allow-hotplug eth0
iface eth0 inet static
        address 10.0.200.30
        netmask 255.255.255.0
        gateway 10.0.200.10


# network interface eth1
allow-hotplug eth1
iface eth1 inet static
        address 10.0.100.30
        netmask 255.255.255.0
        gateway 10.0.100.10


up route add -net 10.0.0.0 netmask 255.255.255.0 gw 10.0.100.10



However, when I reboot, nothing happens, there is no route added,
and i have to add it manually.
All the other configuration stuff in the file that configures my eth0 and eth1 interfaces all works fine,
and these interfaces are all configured perfectly at boot.

I also tried changing it to:

post-up route add -net 10.0.0.0 netmask 255.255.255.0 gw 10.0.100.10

Which is saw somewhere in a thread found via google, but it does'nt do anything either...

What am I missing here ? How do i set my static route so it's automatically set at boot ???

Thanks,
Terrence

---

### Post by chili555 on 2021-02-27
> Ubuntu LTSUbuntu which? In versions 17.10 and later,  /etc/network/interfaces is deprecated in favor of netplan. Please see the netplan templates here:

```
ls /usr/share/doc/netplan/examples
```

---

### Post by radiance32 on 2021-02-27
> **chili555 said:**
> Ubuntu which? In versions 17.10 and later,  /etc/network/interfaces is deprecated in favor of netplan. Please see the netplan templates here:

```
ls /usr/share/doc/netplan/examples
```

Hi,

I'm using an image that came with my NanoPi R1S SBC called "nanopi-r1s-h3_sd_friendlycore-xenial_4.14_armhf_20191219.img",
and there is no netplan in /usr/share/doc ...

Any other ideas ?

Terrence

---

### Post by Doug S on 2021-02-27
I wonder if it is just a timing thing. Just as a hack job test, try a calling a script from a post-up with a sleep delay as its first command.
Also suggest sending a message to /var/log/kern.log (or does it go to syslog? can not recall, and it has been too long since a re-boot, everything has flushed.) indicating it ran. Example:

```
echo "doug_firewall $FWVER done..." >> /dev/kmsg
```

---

### Post by radiance32 on 2021-02-27
Yeah,

I was thinking about that too yesterday,
maybe it takes a bit for the interfaces to come up and the route command is executed too early and fails...

i'll give it a go and create a startup script...

Terrence

---

