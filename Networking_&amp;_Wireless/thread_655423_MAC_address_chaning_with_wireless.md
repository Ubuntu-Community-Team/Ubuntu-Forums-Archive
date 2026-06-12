---
title: "MAC address chaning with wireless"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by tim_wright on 2008-01-01
Hello, I'll get to business. The reason behing me wanting to change my MAC address is because I've had it blocked on my home network.

I can change my MAC successfully but the problem lies with getting things up and running again. I let network-manager sort out my conenctions but I do have a little experience with manually configuring conenctions for WPA-PSK (which still doesn't work)

The process which I use is the following:

1. Stop networking (sudo etc/init.d/networking stop)
2. Right click on network manager icon and deselect networking
3. sudo ifconfig ath0 down
4. sudo macchanger --mac=address here ath0
5. sudo ifconfig ath0 up
6. sudo dhclient ath0 which doesn't work, just keeps sending requests but gets no answers. 
7. Restart networking (with restart instead of stop)
8. Right click on network manager and select entworking
9. When I try and do anything with network manager it just crashes and burns.

WEP encryption, open system, signal strength good enough.

Appreciate any help!

Thanks

---

### Post by spd106 on 2008-01-02
Looks like you're using an Atheros based card with the Madwifi driver.

If that's true then have a look at this wiki page
[http://madwifi.org/wiki/UserDocs/ChangeMacAddress]("http://madwifi.org/wiki/UserDocs/ChangeMacAddress").

---

