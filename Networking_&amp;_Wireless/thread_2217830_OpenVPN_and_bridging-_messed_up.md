---
title: "OpenVPN and bridging- messed up"
date: 2014-04-18
forum: Networking &amp; Wireless
---

### Post by risk3715 on 2014-04-18
So, I was toying around with my ubuntu machine... I setup OpenVPN from it to a client machine (mac) that I could access from outside my local network. This was strictly the basic of client to server setup- like mentioned here: [http://openvpn.net/index.php/open-source/documentation/howto.html](http://openvpn.net/index.php/open-source/documentation/howto.html)

PLEASE NOTE, I DID ALL OF THIS VIA SSH- WITHOUT PHYSICAL ACCESS TO THE MACHINE.

The next thing I wanted to do was to route web traffic through the client's VPN to the server and bridge it over from tun0 to eth0 and out the gateway on that local network. I was following this: [http://openvpn.net/index.php/open-source/documentation/miscellaneous/76-ethernet-bridging.html](http://openvpn.net/index.php/open-source/documentation/miscellaneous/76-ethernet-bridging.html)

> **Bridge Server on Linux**

[COLOR=#003366][FONT=Arial]First, make sure you have the **bridge-utils** package installed.[/FONT][/COLOR]
[COLOR=#003366][FONT=Arial]Edit the [bridge-start]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/76-ethernet-bridging.html#linuxscript") script below. Set the **br**, **tap**, **eth**, **eth_ip**, **eth_netmask**, and **eth_broadcast** parameters according to the physical ethernet interface you would like to bridge. Make sure to use an interface which is private and which is connected to a LAN which is protected from the internet by a firewall. You can use the Linux **ifconfig** command to get the necessary information about your network interfaces to fill in the **bridge-start** parameters.[/FONT][/COLOR]
[COLOR=#003366][FONT=Arial]Now run the **bridge-start** script. It will create a persistent **tap0** interface and bridge it with the active ethernet interface.[/FONT][/COLOR]
[COLOR=#003366][FONT=Arial]Next, we will edit the [OpenVPN server configuration file]("http://openvpn.net/index.php/open-source/documentation/howto.html#server") to enable a bridging configuration.[/FONT][/COLOR]
[COLOR=#003366][FONT=Arial]Comment out the line which says **dev tun** and replace it instead with:[/FONT][/COLOR][INDENT]**dev tap0**[/INDENT]


I changed the "bridge-start" script to reflect my network settings as mentioned above. Once I ran "bridge-start", I lost connectivity to the ubuntu machine via ssh. I remoted into another machine on the same network as the ubuntu machine and was able to ssh into it from there and I ran 'bridge-stop' thinking it'd reverse the damage I had caused. And then I lost ssh on the local network as well.


I will be checking the machine physically in person later today. My guess is it has to do with setting up the br0 and tun0 and eth0 wrong... IPtables or something maybe - and I need a way to reverse what I did.


Help and direction would be appreciated. I can post information specific to eh machine later upon request- as I'm sure I haven't given sufficient here.

---

### Post by risk3715 on 2014-04-18
I'm not sure what I did right or wrong which makes this a bad learning experience- but it is working again.
On the ubuntu machine, I started with: sudo ifconfig tun0 down
Next I rebooted. At first, I couldn't ssh into the machine without logging in on the actual machine first... but it has since started working as it had before allowing me remote control through ssh as well as the VPN working on my one client machine.

Regardless- I didn't follow instructions very well and left the config of 'bridge-start' and 'bridge-stop' defining the tun0 device as tap0.

Real lesson learned- read more carefully.  Cheers! :D

---

