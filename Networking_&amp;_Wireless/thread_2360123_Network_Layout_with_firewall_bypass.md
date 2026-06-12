---
title: "Network Layout with firewall bypass"
date: 2017-05-02
forum: Networking &amp; Wireless
---

### Post by sneh2 on 2017-05-02
I am in the process of building and setting up a server and firewall for my home network.

Im running Ubuntu server and want to run a PfSense firewall in a VM. The server has 3 NICs so I should be able to use them for PfSense WAN, PfSense LAN and server LAN hopefully.

Everything to the internet will be going out through a VPN. Ubuntu server will look after DHCP. WiFi on the Billion will be disabled and all WiFi connections will be done through the other two access points.

I would like to set it up so that all traffic EXCEPT for my Xbox One goes through the firewall and VPN, as I play FPS games and don't want to add any extra latency if I can help it.

I have one cat6 cable running from the lounge room to the other end of the house where the office is. Can I run the Xbox one with a static IP on a separate subnet through the current switch setup, as per the diagram below (red cables) to avoid going through the firewall and VPN?  

Am I on the right track?

[ATTACH=CONFIG]274904[/ATTACH]

Thanks!

---

### Post by ian-weisser on 2017-05-02
I don't put network infrastructure (firewall) and server on the same hardware.
The moment your server goes down --and they do!-- you lose your network, too.
Hard to search for a solution without network.

Opening a giant hole in your firewall for the Xbox seems unwise. 
When somebody penetrates your Xbox, they will pwn a machine behind your firewall - all your hardware and files on your LAN belongs to them.

Firewall latency should be far below the threshold that a human would notice.
If your latency is noticeable, then rethink and simplify your plan.

---

