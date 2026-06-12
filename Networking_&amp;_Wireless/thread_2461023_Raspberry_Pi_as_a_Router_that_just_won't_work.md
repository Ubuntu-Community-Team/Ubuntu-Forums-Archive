---
title: "Raspberry Pi as a Router that just won't work"
date: 2021-04-22
forum: Networking &amp; Wireless
---

### Post by markcasazza on 2021-04-22
My Raspberry Pi 3 was a great router, but I never turned on DHCP. I upgraded to a 4 and want to make if better with DHCP but it refuses with both Raspberry Pi OS and Ubuntu. It seems I can get it to work as a router, but as soon as I set up a DHCP server it stops routing. 


This is my use case: I travel a lot in an RV and I want my Raspberry Pi to connect to the local WiFi and then share that connection over the wired ethernet connection with my router which then shares the connection with all my devices and provides a local area network where I can safely share resources. Because connections vary, I need the Pi to have a GUI so I can deal with all sorts of &#8220;authenticated&#8221; connections (i.e., Hotels with putting pass codes in the browser on first use, etc.). I also want the Pi&#8217;s GUI tools to work to scan for WiFi signals and make the connection.


The connection sequence looks like this:
Local Wifi <-> Pi &#8211; wlan0 <-> Pi eth0 <-> Local Router <-> Multiple connecting devices


I tried the Raspberry Pi OS (Full) and Ubuntu Desktop 20.10. The most recent and most successfully attempt was with Ubuntu. This was my process and results


Connecting the wlan0 adapter to a local WiFi signal with the GUI


Configure eth0 to be 192.168.10.1 via edits to /etc/netplan/10-rpi-ethernet-eth0.yaml
```
network:
  ethernets:
    eth0:
      # Rename the built-in ethernet device to "eth0"
      match:
        driver: bcmgenet smsc95xx lan78xx
      set-name: eth0
      dhcp4: no
      addresses:
        - 192.168.10.1/24
      optional: no

```

Turn on packet forwarding via /etc/sysctl.conf
Uncomment &#8220;# net.ipv4.ip forward=1&#8221;


Reboot and confirm the above looks good.
&#8220;ip a&#8221; shows eth0 configured as desired


Turn on Routing with these commands:
```
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
iptables -A FORWARD -i wlan0 -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i eth0 -o wlan0 -j ACCEPT
```


**At this point, if the router&#8217;s WAN port is configured with a 192.168.10.* address, all works!**


Install, configure, and turn on (isc-dhcp-server) DHCP server

Install DHCP server
```
apt install isc-dhcp-server
```


Configure (/etc/dhcp/dhcpd.conf)
```
option domain-name "Rasp.Pi";
option domain-name-servers 8.8.8.8, 8.8.4.4;
default-lease-time 600;
max-lease-time 7200;
ddns-update-style none;
authoritative;
subnet 192.168.10.0 netmask 255.255.255.0 {
  range 192.168.10.10 192.168.10.110;
  #option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
}
```


Configure (etc/default/isc-dhcp-server)
```
INTERFACESv4="eth0"
```


Restart the service
```
systemctl restart isc-dhcp-server.service

```

**I had everything working (with the router pre-configured with a 192.168.10.10 WAN address) until I turned on the DHCP server. Then all failed. **


**I then uninstall the DHCP server (apt remove isc-dhcp-server; init 6) and hard code the router&#8217;s WAN IP address and things work again. **


What am I doing wrong?


Thank you so much for your help. Crazy as is seems this working really helps me take pictures like you can see at [https://tinyurl.com/u5pmp2j9](https://tinyurl.com/u5pmp2j9)


Mark

---

### Post by slickymaster on 2021-04-23
Thread moved to **Networking & Wireless** for a better fit

---

### Post by Tadaen_Sylvermane on 2021-04-23
I think you need to have the dhcp server broadcast it's own ip as the router, 192.168.10.1. It's handing out dhcp but not telling anything where the gateway is. I use dnsmasq as it's vastly simpler for my needs, home lan. Still have to specify the router.

```
# dnsport=53
listen-address=::1,127.0.0.1,192.168.1.1
cache-size=1000
no-resolv
domain-needed
bogus-priv
strict-order
server=8.8.8.8
server=8.8.4.4


# dhcp
interface=enp2s0
bind-interfaces
domain=mylan.home
# here ! #
dhcp-option=option:router,192.168.1.1
dhcp-range=192.168.1.50,192.168.1.200,2h
```

Probably your issue.

---

### Post by markcasazza on 2021-04-25
Indeed! This change fixed it. Thank you

[COLOR=#000000]Configure (/etc/dhcp/dhcpd.conf)[/COLOR]
[COLOR=#000000]
```
option domain-name "Rasp.Pi";
option domain-name-servers 8.8.8.8, 8.8.4.4;
default-lease-time 600;
max-lease-time 7200;
ddns-update-style none;
authoritative;
subnet 192.168.10.0 netmask 255.255.255.0 {
    range 192.168.10.10 192.168.10.110;
  [COLOR=#800080]  option routers 192.168.10.1;[/COLOR]
}
```

[/COLOR]

---

