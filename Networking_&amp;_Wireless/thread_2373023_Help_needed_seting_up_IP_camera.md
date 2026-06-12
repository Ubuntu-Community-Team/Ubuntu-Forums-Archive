---
title: "Help needed seting up IP camera"
date: 2017-10-01
forum: Networking &amp; Wireless
---

### Post by conradin on 2017-10-01
Hello all, 
I have tried all weekend, and not succeeded to create a network I want to set up. It is time to ask for help. 
I have an IP camera, that I want to have a static address, on a local IP. 10.0.0.15 for example.
I have a wifi connection that I want to still be able to connect to my home wifi with. The computer has an ethernet port, and a wifi device. 

at one point I was able to have one or the other, but not both running at the same time. But I screwed it up real bad, and had to delete everything.

So I have been looking at /etc/network/interfaces, and /etc/dhcp/dhcp.conf, and /etc/default/isc-dhcp-server
At this point I am so confused about what to do. I deleted everything, and now i can connect to my home wifi. 
The ip camera is physically attached, but no longer picks up an address from the server. 

I am only trying to set up IPV4 addressing on the local network.

[B]cat /etc/defualt/isc-dhcp-server 
INTERFACESv4="eth0"
[/B]


/etc/network/interfaces reads:

[B]auto lo
iface lo inet loopback
auto wlan0

auto eth0
iface eth0 inet static
address 10.0.0.42
netmask 255.255.255.0
network 10.0.0.0
broadcast 10.0.0.255
gateway 10.0.0.1
dns-nameservers 10.0.0.1
[/B]

/etc/dhcp/dhcpd.conf reads:
[B]authoritative;

subnet 10.0.0.0 netmask 255.255.255.0 {
 range 10.0.0.1 192.168.0.254;
 option broadcast-address 192.168.0.255;
 option routers 192.168.0.1;
 default-lease-time 600;
 max-lease-time 7200;
 option domain-name "local-network";
 option domain-name-servers 8.8.8.8, 8.8.4.4;
}


host camera {
     hardware-address C4:D6:55:3E:43:72;
     fixed-address 10.0.0.15;
}
[/B]

Perhaps Im missing something silly, I've been trying and not getting it. I just want the local address to run and assign the IP cammera a fixxed static IP, and still be able to connect to the internet on my 
home network at the same time. What am I doing wrong here?

---

### Post by Kirboosy on 2017-10-02
Hi Conradin,

So it looks like you had a mistype in your reservation area on the camera. Everything else in your config for the DHCP server looks correct.

> **conradin said:**
> [B]
```

host camera {
     hardware ethernet C4:D6:55:3E:43:72;
     fixed-address 10.0.0.15;
}

```[/B]

Let me know if that changes anything for you!

Hope that helps!
~Caboose

---

