---
title: "setting up a static IP address for my server"
date: 2013-12-21
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2013-12-21
I am trying to setup a static IP address for my Ubuntu server.  I go to the admin page for my router, set the MAC address, and the IP address that I would like.  I then set it to static.  I then test it by turning off the server, and plugging in another device.  The other device comes online, takes the server's IP address, and changes the static MAC address to the new device that just came online.  Why would the IP address not be reserved if it was set to static?

---

### Post by steeldriver on 2013-12-21
it's hard to tell without knowing the particular router, but possibly by setting it to 'static' on the router, it thinks you intend to set up a true static IP on the client?  Normally when you reserve an IP on the router side that is not really classed as 'static', it is done via DHCP (i.e. the client still gets its IP via DHCP, but the router's DHCP server always hands out the same IP based on MAC)

---

### Post by TheFu on 2013-12-21
Setting a static IP through the router is called "DHCP Reservation" - it is tied to the MAC address used by the specific network card inside the server.

The server will need to be rebooted (or at least the network static will need to be restarted) for the new IP to take effect.

It is best to put the static IP outside the normal DHCP range of IPs. Could this be the issue?

It is unclear to me what you mean by "plugging in another device."

Ok, completely switching gears now ... the best way to setup a static IP for a server is NOT in the DHCP reservations on a router, rather, tell the server which IP address it should use and have it demand that address.  How to do this depends on whether you have any GUI installed or not. If you only have Ubuntu Server installed - no GUI, no Network Manager, then edit the /etc/network/interfaces file, restart the networking service and you are done.  I haven't a clue how to do it with a GUI involved. Sorry.  **man interfaces** will explain the options, but normally, something like this example will be used.

```
auto eth0
iface eth0 inet static
  address 192.168.1.xx
  gateway 192.168.1.x
  netmask 255.255.255.0
  dns-nameservers 192.168.1.x
  dns-search example.com example.lan
```

Your specific settings will be different, probably. All the 'x' characters need to be changed to your network - other parts will likely need to be changed as well. I think these are the bare minimal settings needed.

**DO NOT use a static IP in the range given out by your router for DHCP addresses.**

---

### Post by sniper8752 on 2013-12-21
I saved a few addresses, and saved 192.168.1.231 as my server address.  I setup my interfaces file like so:
```
[COLOR=#000000][FONT=Ubuntu Mono]auto wlan0[/FONT][/COLOR]iface wlan0 inet static
  address 192.168.1.231
  gateway 192.168.1.1
  netmask 255.255.255.0
  dns-nameservers 192.168.1.1[COLOR=#000000][FONT=Ubuntu Mono]  dns-search 192.168.1.1[/FONT][/COLOR]
```

When I ping it, it says that the destination host is unreachable.  The server does say it has that address.
Edit:  I turned off the server, and it says that 192.168.1.231 is still active on the router admin page.  Also, I could not ping 192.168.1.1 from the server.

---

### Post by TheFu on 2013-12-21
If you cannot ping the router, that is bad. Very bad.  Time to get a working network again and post some specific cmd results.

$ route
$ ifconfig

Those should be enough. Make certain that everything is working on your network BEFORE running those cmds.  
Also, please confirm that you are running Ubuntu Server - NO GUI. If you have a GUI, the steps are different.

Bedtime here. Bye.

---

### Post by chili555 on 2013-12-21
Just to humor an old Chili, please set up interfaces like this:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
  address 192.168.1.231
  netmask 255.255.255.0
  gateway 192.168.1.1
  dns-nameservers 192.168.1.1 
```Now get the system to re-read and use the changes:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```Any errors or warnings? How about?```
ping -c3 192.168.1.1
```

---

### Post by sniper8752 on 2013-12-21
I set it up like that, and got no error messages. still says that it can't reach the destination.

---

### Post by Iowan on 2013-12-21
Back to the previoius request, then...
results of:
**route -n**
**ifconfig**

---

### Post by sniper8752 on 2013-12-21
route:
destination/gateway/genmask
0.0.0.0     192.168.1.1     0.0.0.0
192.168.1.0     0.0.0.0      255.255.255.0

ifconfig
inet addr: 192.168.1.231
bcast: 192.168.1.255
mask: 255.255.255.0

---

### Post by chili555 on 2013-12-21
I am off for the evening, but one of the guys will help you set it to DHCP, and see what address, gateway, route, etc. you get.

---

### Post by Iowan on 2013-12-21
Another question...
Is the server using wireless or wired?

Reason for asking:
The above instructions should be altered for wlan0 or eth0.
(My laptop calls the wireless card eth1)

---

### Post by lisati on 2013-12-21
> **TheFu said:**
> 
**DO NOT use a static IP in the range given out by your router for DHCP addresses.**

I wish to repeat the warning: take care not to set an IP address on your Ubuntu box that could conceivably be handed out by your router's DHCP services, otherwise there is a risk that the router will assign the IP address to different machine to the one that you want to use the IP address.

---

### Post by sniper8752 on 2013-12-21
I think that it is set to DHCP, isn't it?  I did not define the gateway or IP.

---

### Post by sniper8752 on 2013-12-21
It is using a wireless usb adapter.
And I changed it so that the router only hands out up to 192.168.1.170.  My server's is 171.  
in my dhcp connections, I have then mac address of the server, the ip address, and the lease type.  i have it set to static, .171, and the mac address of the server.  what should this entry for the server look like?  wouldn't this not work since it can only go up to 170?

---

### Post by chili555 on 2013-12-22
I made a slight mistake in my suggestion above, I apologize. Please try:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
  address 192.168.1.231 
  netmask 255.255.255.0
  gateway 192.168.1.1
  dns-nameservers 192.168.1.1
  wpa-ssid <your_router_ssid>
  wpa-psk <your_secret_key>
```Now do:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```The -v switch makes the process verbose so you can see if there are any errors, warnings, oopsies, et al.```
ping -c3 www.google.com
```

---

### Post by sniper8752 on 2013-12-22
I apologize for the double post.  Thanks for your help, Chili!

---

