---
title: "configuring network"
date: 2006-09-26
forum: Networking &amp; Wireless
---

### Post by wittyguysuku on 2006-09-26
How can I configure my network permanantly? I mean, for temporary, whenever I execute the following command, the network is configured properly and I could connect to the network/internet etc.,

> 
ifconfig eth0 192.168.3.51 netmask 255.255.255.0
route add default gw 192.168.3.1


Then I added the **nameservers** to **/etc/resolv.conf** also.

It's working fine now. But once I reboot, all the above configuration goes off. Again I need to give the above command to configure my network.

So is there any thing I could do to make all these configuration permanant whenever I boot?

thanks,
Wg

---

### Post by fstab on 2006-09-26
If you have a graphical desktop, you could go to System->Administration->Networking, highlight the eth0 device, click Properties and then change the configuration to static and enter the info that you posted.

---

### Post by wittyguysuku on 2006-09-26
Thanks for your reply!
But I'm using terminals to work. So is any configuration files need to be edited?

---

### Post by fstab on 2006-09-26
I believe the file is /etc/network/interfaces but I don't know how you'd set yours up.  Check the man page for interfaces as recommended inside the file:  

```
root@pago:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp

auto eth0
```

---

### Post by wittyguysuku on 2006-09-26
Or should I edit > /etc/dhcp3/dhclient.conf?

This is how my dhclient.conf file looks like:
> #       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}


---

### Post by mips on 2006-09-26
Edit your /etc/network/interfaces file.

---

### Post by Iowan on 2006-09-26
As mentioned, the network setup will be done from **/etc/network/interfaces** (Although you appear to be using a static address, even DHCP setup must be done in **/etc/network/interfaces**)

---

### Post by wittyguysuku on 2006-09-27
Thank you buddies for all your help!

As you said, I edited my **/etc/network/interfaces** like: > cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.3.51
    netmask 255.255.255.
    gateway 192.168.3.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

But still it could not add the gateway information to it's route table. But if I explicitly give **route add default gw 192.168.3.1**, it's able to connect to the internet. So only issue pending for me is where to add this route info?

---

### Post by mips on 2006-09-27
This is a workaround but you could try adding the route to youe init.d file

---

### Post by nolim on 2008-04-19
add this line to /etc/network/interfaces

```
up route add default gw YOUR_GATEWAY
```

---

### Post by MianoSM on 2008-04-25
> **nolim said:**
> add this line to /etc/network/interfaces

```
up route add default gw YOUR_GATEWAY
```

After recently upgrading a server to 8.04 LTS I was unable to connect remotely to my server (from machines on a different gateway), however could connect to my server remotely via other servers on the same gateway.

After including this line:

```
up route add default MY_GATEWAY
```

The machine was again accessible via any other machine on any network. Thank you for the advice/assistance.

---

