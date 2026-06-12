---
title: "Wifi not renewing DHCP lease"
date: 2014-08-31
forum: Networking &amp; Wireless
---

### Post by ozsliver on 2014-08-31
Hi

I installed Lubuntu 14.04 and I have a strange problem.
If I leave the computer on for more than a day my WIFI connection loses Internet access (i.e. I'm still connected to the router but no Internet and I can't even see the main router page).

I believe this is caused by the DHCP lease expirying without being renewed properly, if I do

ifconfig wlan0

when the problem happens, I get:

wlan0     Link encap:Ethernet  HWaddr 00:13:02:9c:81:00  
          inet6 addr: fe80::213:2ff:fe9c:8100/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:245813 errors:0 dropped:0 overruns:0 frame:0
          TX packets:201724 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:212425325 (212.4 MB)  TX bytes:37080050 (37.0 MB)


i.e no IP address.

Disconnecting and reconnecting through the wifi applet does not work, only this command fixes it:

sudo dhclient wlan0

I then get a new address and everything works again.

I checked /var/log/syslog while the problem was occurring and I saw this strange log:

Aug 31 17:05:49 mondrian NetworkManager[873]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Aug 31 17:05:49 mondrian NetworkManager[873]: <info>   address 0.0.0.0
Aug 31 17:05:49 mondrian NetworkManager[873]: <info>   prefix 24 (255.255.255.0)
Aug 31 17:05:49 mondrian NetworkManager[873]: <info>   gateway 192.168.1.1
Aug 31 17:05:49 mondrian NetworkManager[873]: <info>   nameserver '192.168.1.1'
Aug 31 17:05:49 mondrian NetworkManager[873]: <info>   domain name 'home'
Aug 31 17:05:49 mondrian NetworkManager[873]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Aug 31 17:05:49 mondrian NetworkManager[873]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Aug 31 17:05:50 mondrian NetworkManager[873]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Aug 31 17:05:50 mondrian NetworkManager[873]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Aug 31 17:05:50 mondrian NetworkManager[873]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Aug 31 17:05:50 mondrian NetworkManager[873]: <info> NetworkManager state is now CONNECTED_GLOBAL
Aug 31 17:05:50 mondrian NetworkManager[873]: <info> Policy set 'OCEAN' (wlan0) as default for IPv4 routing and DNS.
Aug 31 17:05:50 mondrian NetworkManager[873]: <info> Writing DNS information to /sbin/resolvconf
Aug 31 17:05:50 mondrian dnsmasq[1073]: setting upstream servers from DBus
Aug 31 17:05:50 mondrian dnsmasq[1073]: using nameserver 192.168.1.1#53
Aug 31 17:05:50 mondrian NetworkManager[873]: <info> Activation (wlan0) successful, device activated.

Why is it trying to bind to 0.0.0.0? Any idea on how to correct this behaviour?

Thanks!

---

### Post by wildmanne39 on 2014-08-31
Thread moved to networking and wireless!

---

### Post by ozsliver on 2014-09-04
Any ideas?

The problem keeps happening, I'm now thinking to enable a cron job to issue sudo dhclient wlan0 every 12 hours...

---

