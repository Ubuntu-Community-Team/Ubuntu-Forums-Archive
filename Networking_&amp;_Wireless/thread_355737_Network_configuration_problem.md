---
title: "Network configuration problem?"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by eekrazyk on 2007-02-07
I've recently installed Kubuntu on my newest PC at work. I have been running Gentoo on my old box for about 3 years now. I have two ethernet drops in my cubicle, but only one had been connected, so I hooked a hub up to connect my new PC to the network and install Kubuntu. Everything had been working great, so I took the hub out and had IT connect my second ethernet drop. Now I'm having problems....

The network connection is extremely slow. Painfully slow. It had not been slow on the hub.

```

# cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

....
[\CODE]


If I attempt to ping one of our unix servers, I get something like 20% packet loss:

[CODE]
# ping razor 
ping razor (ip removed) 56(84) bytes of data. 
64 bytes from razor (ip removed): icmp_seq=1 ttl=255 time=2.97 ms 
64 bytes from razor (ip removed): icmp_seq=4 ttl=255 time=0.152 ms 
64 bytes from razor (ip removed): icmp_seq=5 ttl=255 time=0.166 ms 
64 bytes from razor (ip removed): icmp_seq=6 ttl=255 time=0.153 ms 
64 bytes from razor (ip removed): icmp_seq=7 ttl=255 time=0.156 ms 
64 bytes from razor (ip removed): icmp_seq=8 ttl=255 time=0.153 ms 
64 bytes from razor (ip removed): icmp_seq=9 ttl=255 time=0.155 ms 
64 bytes from razor (ip removed): icmp_seq=10 ttl=255 time=0.245 ms 

- - - razor ping statistics 
10 packets transmitted, 8 received, 20% packet loss, time 900.ms 
rtt min/avg/max/mdev = 0.152/0.518/2.970/0.927

```

If I try to connect to the internet, it's REAL slow. I called IT and they said I'm getting all sorts of errors on that port.

checking dmesg:

```

[17182408,664000] tg3: eth0: Link is up at 100Mbps, full duplex 
[17182408,664000] tg3: eth0: Flow control is off for Tx and off for Rx. 
[17182424,132000] tg3: eth0: Link is down. 
[17182425,772000] tg3: eth0: Link is up at 100Mbps, full duplex 
[17182425,772000] tg3: eth0: Flow control is off for Tx and off for Rx. 

.... 
repeated numerous times 
.... 

[17182843,460000] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[17182845,436000] tg3: eth0: Link is up at 100Mbps, full duplex 
[17182845,436000] tg3: eth0: Flow control is off for Tx and off for Rx. 
[17182843,440000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready 
[17182856,400000] eth0: no IPv6 routers present

```


Any ideas? I'm not sure what's going on.... Need me to drop any other files on here?

Thanks for your help.

---

### Post by lloyd_b on 2007-02-07
Is there a link LED on the ethernet?  If so, try watching it for a while (with no activity) and see if it's blinking on and off.  That "Link up/Link down" stuff looks like you've got a cable with intermittent problems.

You can try sticking the hub on the new cable, and see what happens, but I suspect it'll be the same.

Lloyd B.

---

### Post by eekrazyk on 2007-02-08
Yep, both the green and orange LEDs are lit up.  The green is flickering quite rapidly.

I just tried a different cable and the green LED still flickers.  Still having problems with packet loss.

And a third cable produces the same results.  Maybe it's somewhere between my drop and the first switch?

Any other ideas?

---

### Post by mips on 2007-02-08
Check to see if you have speed & duplex mismatches on that port. Ask the IT guys what speeds and duplexes the switch supports and then configure your eth for 100mbs/full-duplex if the switch supports its. Sometimes autoconfig does not work that great but it is rare.

---

### Post by eekrazyk on 2007-02-08
I think it may be the connection between the drop in my cube and the switch.  I switched my cable over to the drop in the vacant cube next to me and it works great!

Thanks for the help!

---

### Post by mips on 2007-02-08
> **eekrazyk said:**
> I think it may be the connection between the drop in my cube and the switch.  I switched my cable over to the drop in the vacant cube next to me and it works great!

Thanks for the help!

lol, tell them to get out the Fluke and start re-terminating.

---

