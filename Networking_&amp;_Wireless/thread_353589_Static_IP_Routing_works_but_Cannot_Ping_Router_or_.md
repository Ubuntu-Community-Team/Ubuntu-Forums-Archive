---
title: "Static IP Routing works but Cannot Ping Router or resolve hostname"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by drupii on 2007-02-04
I have almost tried everything and read all posts trying to resolve this issue but have not found a fix/solution yet so now I turn to you experts... Please Help!

I recently installed Ubuntu Server 6.10 on my P4 box, following is what I can and cannot do:

**I cannot**:
Ping other computers using the hostname (Ping LAN IP address works fine)
Ping external (WAN) IP Addresses or Hostnames (eg. [www.yahoo.com](www.yahoo.com))

**I can**:
Successfully SSH to the Linux box using IP from another windows machine on the LAN
Successfully ping hostname of linux box from itself


cat of my **/etc/network/interfaces** file
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.106
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.1

```


cat of my **/etc/dhcp3/dhclient.conf**
```

send host-name "ubuntu";

```


cat of my **/etc/hosts**
```

127.0.0.1       localhost
192.168.0.106   ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```


I am not sure if this is an issue with my router but I would assume that if it can resolve other windows machine hostnames correctly it should do the same for my linux box. It can't be OS Dependent correct?

I should also add that I am a Linux newbie :) I am trying to switch from MS to Linux it just seems difficult but I am not giving up! Please help Linux Gurus...

---

### Post by amohanty on 2007-02-04
Ok,

some basics about hostnames and ips.
To resolve hostnames to ips os's use dns. So when you type in google.com., your boxen doesnt know it maps to an ip, it asks its dns server for that. In a LAN if you dont have a DNS server you cannot refer to a machine by name, you have to use your IP. Windows can do it because it bypasses this using NetBIOS and other MS workspace-y stuff (I am not a network person, so cant explain it to you). 

TO do so in linux you will need to add the hostname/ip pair to /etc/hosts. See the file for instructions as to how to do so.

HTH
AM

---

### Post by drupii on 2007-02-04
So does that mean every website I want to access I need to add it to my /etc/hosts file? Also I dont know if this means anything I cannot ping the IP address of yahoo.com (66.94.234.13)

Thank you for the quick reply :)

---

### Post by Mavvy on 2007-02-04
point it to your router or isp dns server.. it should resolve for you...

dhcp auto push down dns.. but static doesn't.. so manually key it in.

---

### Post by amohanty on 2007-02-04
> So does that mean every website I want to access I need to add it to my /etc/hosts file? Also I dont know if this means anything I cannot ping the IP address of yahoo.com (66.94.234.13)


No thats done for you by your ISPs DNS server. However addresses in teh 192.168.*.* and a bunch of other ranges are reserved for internal networks and cannot be resolved by the ISPs DNS server because:
a. they dont know where it is (only your router knows)
b. there are multiple instances because a whole bunch of your ISPs users have routers.

HTH
AM

---

### Post by drupii on 2007-02-04
could you please post an example?

based on the /etc/hosts file I need a IP/hostname pair but my router does not have a hostname, what can I use as a IP/hostname pair?

```

**[COLOR="Red"]192.168.0.1       whatgoeshere?[/COLOR]**
127.0.0.1       localhost
192.168.0.106   ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by amohanty on 2007-02-04
So usually unless your router is a desktop itself, you dont need to hit it via a name. ( for eg its one of those dinky little things). In theory you could put any name there, because most routers afaik dont really publish a hostname. You just hit the IP in a browser. 

The solution I provided only applies to other hosts in your internal LAN.

AM

---

### Post by drupii on 2007-02-04
So far I have been successful in doing the following:

add following to my /etc/hosts file

192.168.0.102      windowshostname

and now when i do: ping windowshostname it works successfully.

but my main problem is when i do ping 192.168.0.1 which is my router and it does not work! not sure why!!! but I can ping all other machines on my network via the IP address.

Sorry if I wasnt clear about my problem before... Thanks for looking into this

---

### Post by amohanty on 2007-02-04
Can you post the output of 
arp -a

AM

---

### Post by drupii on 2007-02-04
Here you go:

> 
root@ubuntu:/cdrom# arp -a
? (192.168.0.101) at 00:90:96:A3:B5:F6 [ether] on eth0
my-router (192.168.0.1) at 00:13:46:3F:5E:D4 [ether] on eth0


---

### Post by amohanty on 2007-02-04
Your router is online. Now some routers have the option of rejecting pings. So you might want to check the options in your router config and make sure that any such option is turned off.

AM

---

### Post by drupii on 2007-02-04
I verified router settings I am using DI-524 router and there were no settings which disables a ping from the LAN however there was a setting to Disable ping from the WAN.

I am able to ping from my windows machine to the router thou I dont knwo if that means anything. 

I still cannot ping yahoo.com or the ipaddress for yahoo.com. Gosh I feel really dumb now!

---

### Post by drupii on 2007-02-04
I tried installing ubuntu on a different older machine I have and everything works great. I am guessing something to do with the ethernet card, but it just doesnt make much sense that I am able to connect to the network but just not browse the internet!

---

### Post by amohanty on 2007-02-05
On the router do you have MAC filtering on?
Also can you make sure that the IP you assigned is in the IP range specified in the router LAN setup?

What happens if you switch to DHCP?

AM

---

### Post by drupii on 2007-02-05
OMG! that is the stupidest thing I've ever done in my whole life!!! can't believe it.. I had the MAC Filtering on! I am up and running now!

amohanty I can't thank you enough for helping out a fool like me...

---

