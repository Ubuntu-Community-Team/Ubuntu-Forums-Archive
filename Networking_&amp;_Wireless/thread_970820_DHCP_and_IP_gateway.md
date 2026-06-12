---
title: "DHCP and IP gateway"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by thumper_e on 2008-11-04
Hi there,

I do appologise if a previous thread has been opened for this issue, I did look but couldn't see one.

Any way I am having an issue with Intrepid. I did a fresh install and all seemed to be ok, On however trying to set up a DHCP server I get a few issues. 

Firstly I have it running ok by using the command;
```
 sudo /etc/init.d/dhcp3-server restart
```

This does assign an IP address to the other computers on my network however none of them can connect to the internet, Yet they can ping the address that the internet is on! 

My dhcpd.conf setup is;

```
# A slightly different configuration for an internal subnet.
subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.1 192.168.0.10;
  option subnet-mask 255.255.255.0;

  option domain-name-servers 194.168.4.100, 194.168.8.100;
  #option domain-name "tm.net.my";
  option routers 192.168.0.1;
  option broadcast-address 192.168.0.255;
  default-lease-time 600;
  max-lease-time 7200;
}
```

Because I used to get error codes (No subnet mask on eth0) I assigned a static IP address through the network manager as;

```
 ip address 192.168.0.1
       Net Mask 255.255.255.0
       gateway 81.*.*.*

```

and eth1 is my internet connection and thus assigned automatically yet the IP for the gateway in eth0 is the same as the IP address of eth1.

There are two issues that I appear to get firstly is as I mentioned earlier where my LAN computers can talk to each other, file share and even ping the 81.*.*.* address, but when it comes to getting outside that, nothing!Have I missed the whole Idea of the DHCP and Gateway or is there something else I need to do.
And secondly, why do I have to re-assign my static IP address each time I reboot. (Is this a known issue with intrepid and Network manager) If so what is the workaround? I also have to do the same each time I reboot with;
```
 sudo /etc/init.d/dhcp3-server restart
```

I hope I have explained myself properly and look forward to any ideas that you may have.

Thanks

Ian

---

### Post by thumper_e on 2008-11-05
Bump

---

### Post by Iowan on 2008-11-05
My disqualifications: I'm not on Intrepid, and I'm not **really** familiar with DNS or routing.  However, your thread deserves a response - of SOME sort! I notice your DHCP range includes your eth1/gateway address (192.168.0.1). It shouldn't. If this DHCP server is also serving as a router, you might find useful information [here]("https://help.ubuntu.com/community/Internet/ConnectionSharing").

---

### Post by thumper_e on 2008-11-06
Thanks for the tips lowan my configuration changed caused several curious things to happen. I could connect to skype and I could ring people, I could also ping some (But not all web addresses. (So I force fed my ethernet connections a banana and left it for a while :) ).

I then started again and have managed to get it to work, including on rebooting the system, This is how (I think) I did it.

I purged the dhcp3-server and re-installed, to start a fresh
```
 sudo apt-get purge dhcp3-server 
```
```
 sudo apt-get install dhcp3-server 
```

I edited my new dhcpd.conf file
```
  sudo gedit /etc/dhcp3/dhcpd.conf 
```

to give;

```

...
# option definitions common to all supported networks...
#option domain-name "example.org";
#option domain-name-servers ns1.example.org, ns2.example.org;

#default-lease-time 600;
#max-lease-time 7200;

...

# A slightly different configuration for an internal subnet.
subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.2 192.168.0.10;
  option subnet-mask 255.255.255.0;

 option domain-name-servers 194.168.4.100, 194.168.8.100;
  #option domain-name "tm.net.my";
  option routers 192.168.0.1;
  option broadcast-address 192.168.0.255;
  default-lease-time 600;
  max-lease-time 7200;
}


```

I then edited my interfaces file, 
```
 sudo gedit /etc/network/interfaces 
```
```

auto lo
iface lo inet loopback
auto eth1
iface eth1 inet dhcp 
auto eth0
iface eth0 inet static
 address 192.168.0.1
 netmask 255.255.255.0
 network 192.168.0.0
 gateway 81.*.*.;-)

```

restarted both my network and dhcp server;

```

sudo /etc/init.d/networking start
sudo /etc/init.d/dhcp3-server start

```
and then tested. both computers appeared to be working on the net and not just the one of them.

To solve the issue of the dhcp server needing to be restarted I did the following
```

sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf dhcp3-server on

```

Hey presto all works on startup too!

---

