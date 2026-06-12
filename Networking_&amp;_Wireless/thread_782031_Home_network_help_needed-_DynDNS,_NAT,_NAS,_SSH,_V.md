---
title: "Home network help needed- DynDNS, NAT, NAS, SSH, VPN, etc"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by klineroger4 on 2008-05-04
Hi everyone...
I have been researching for quite a while, and its time I look for some help from the community. 
I am trying to redesign my home network, which consists of a cable modem running into my Linksys WRT54G wireless router: one laptop dual booting 8.04 and Vista, eee PC with eeeBuntu, and a Mac. All are wireless. In addition, a NAS device plugged directly into my router (and a printer attached via USB to my NAS). 

My goal is to allow the NAS to be reachable from remote sites via something like VPN or SSH (by me and other individuals) and from all computers on my LAN. My ISP has me NAT'd, so that throws a wrench into the process. The way I see it, I need to get my internal LAN onto static IPs (to allow the NAS device to be always reachable)- so I need to set static IPs for the three computers and the NAS, correct? Then, since I am NAT'd, sign up for DynDNS to get a static IP to allow for remote connections, right? Finally, set up a VPN or SSH server (probably on my Mac as its always on) to allow for remote access. Samba/CIFS for the NAS to allow internal LAN devices access, and CUPS for printer sharing across the LAN.  Looking for opinions and/or suggestions. Thanks everyone!

---

### Post by kwacka on 2008-05-04
There's DyDNS howto at [https://help.ubuntu.com/community/InternetAndNetworking#head-a686606](https://help.ubuntu.com/community/InternetAndNetworking#head-a686606)

plus VNC etc.

---

### Post by rscheideman on 2008-09-25
what kind of nas do you have?

---

### Post by doug-M on 2008-09-27
You could do almost all of this with your WRT54G if it is the right version.
Some newer ones don't have enough flash to hold the vpn software.

Load DD-WRT firmware with vpn onto your WRT54G.
Set up a dyndns account.
Set up the dyndns updater in the WRT54G.
Give all your computers static DHCP leases (you always assign the same DHCP IP address to a particular MAC address)
Set up /etc/hosts files as if you had static addresses.
Set up openvpn on the WRT54G.
Set up port forwarding on your cable modem to forward the incoming vpn connections to the WRT54G, if required.

I prefer setting the machines to use DHCP with static leases instead of static addresses, works better for me with laptops and virtual machines that move to different networks.

This seems to cover everything except the Samba/CIFS for the NAS and CUPS for printer.

---

