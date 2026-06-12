---
title: "Wireless okay with DHCP problems with static IP"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by echo15 on 2007-03-28
Hi,

I'm new to Ubuntu and tried to configure an old PC with it.  I have an Edimax wireless card that I got running following the instructions from [http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980). I started with DHCP and everything was okay. I tried to switch to static IP but found that I couldn't browse the internet. I could ping the router/modem okay, but pinging google resulted in a destination cannot be reached message.

Can anyone help? How do I get static IP working?

Thanks!

---

### Post by spd106 on 2007-03-28
It sounds like you haven't specified a default gateway, you can check this by running ip route like this ```
$ ip route
192.168.0.0/24 dev wlan0  proto kernel  scope link  src 192.168.0.3 
default via 192.168.0.1 dev wlan0 

``` To fix this you should add the address of your router as the gateway. Either through network-admin or in the /etc/network/interfaces file.

---

