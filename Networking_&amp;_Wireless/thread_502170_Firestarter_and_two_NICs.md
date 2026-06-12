---
title: "Firestarter and two NICs"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by Harley883 on 2007-07-16
I have a small home network with two broadband connections - one fast one provided by my employer but with limited bandwidth allowance (okay for browsing and updating not to be used for downloading!!!) and a slower unlimited account I pay for myself. The machine on my own broadband has two NICS 

Eth0
Automatic config (DHCP)
IP Address 192.168.0.4
Subnet mask 255.255.255.0
Gateway Address 192.168.0.1

this NIC connects to the internet for my personal downloading.

and 
Eth1
Static IP address
IP Address 192.168.1.64
Subnet mask 255.255.255.0
Gateway Address blank

this NIC allows me to connect from the other network and control this PC with VNC, transfer files etc.

This all works fine until I install Firestarter and then I can only have either internet access or network access but not both at once. 

My other Ubuntu machines both use Firestarter with a single NIC with no problems and I am quite happy with setting rules etc. but regardless of settings or preferences on the dual NIC machine if Firestarter is installed, unless the firewall is stopped, access is to one NIC only. All my machines are behind NAT router firewalls so are fairly safe but having come from a windows background I don't feel comfortable without a personal firewall running on each machine.

Please note, the two broadband connections must be kept seperate, internet sharing is definitely not required.

Any ideas?

Athlon XP3000 512m feisty

---

