---
title: "Fix IP on wireless?"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by rlameiro on 2008-05-26
I would like to know how to configure my wireless to have always the same ip. I used the network manager and tried to change the ip from dhcp to a fixed IP inside the wifi router range. The ip I want is something 192.168.10.2. The range for the dsl router is 192,168.1.1 and wifi is 192.168.10.1.

when I tried the change, i couldn't connect.I have restarted the laptop and the 2 routers and the problem goes on.

---

### Post by Monicker on 2008-05-26
Ccheck your router configuration to see if it supports dhcp reservations.  That way the client can be set to dhcp, yet always receive the same ip address from the router.

---

### Post by mapes12 on 2008-05-26
Just to help me understand this, why do you need a static IP rather than have DHCP assign an address??

:confused:

---

### Post by rlameiro on 2008-05-26
I need it to allow ports for emule/torrent software

---

### Post by superprash2003 on 2008-05-26
once you configure it to 192.168.10.2 .. go to the terminal and type ping 192.168.10.1 and post output here

---

### Post by mapes12 on 2008-05-27
> check your router configuration to see if it supports dhcp reservations. That way the client can be set to dhcp, yet always receive the same ip address from the router.

You can usually get into your routers configuration settings via your web browser. Your user manual should give you the routers address to type into your browser menu. If you haven't got the user  manual post the make and model back here for us to help you out.

> once you configure it to 192.168.10.2 .. go to the terminal and type ping 192.168.10.1 and post output here

Check the output to ```
ifconfig
``` ahead of pinging to make sure you have the address how you want it and then ```
ping -c4 <IP address>
``` to stop it scrolling off the page.

---

