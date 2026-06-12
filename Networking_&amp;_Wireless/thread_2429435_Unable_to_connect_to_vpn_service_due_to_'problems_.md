---
title: "Unable to connect to vpn service due to 'problems managing IPv6'"
date: 2019-10-18
forum: Networking &amp; Wireless
---

### Post by sleepyneon on 2019-10-18
Hi, I've recently switched to Linux and one of the first things I needed to do was to set up a VPN connection to gain access to most parts of the internet (because my country bans certain websites due to political or religious reasons). I have a ProtonVPN account which works fine on my Windows or Andriod systems, however when I try to connect to the service via Linux terminal, it says that:
[FONT=monospace][COLOR=#000000]
[!] Error connecting to VPN.[/COLOR]
[!] There are issues in managing IPv6 in the system. Please test the 
system for the root cause.
Not being able to manage IPv6 by protonvpn-cli may leak the system's 
IPv6 address.

[FONT=arial]I have contacted the customer support but they weren't able to fix the problem.
Does anyone have any idea on how to fix this? 
also, does anyone know any other FREE vpn services that are worth trying?  [/FONT][/FONT]

---

### Post by milesweb on 2019-10-18
Make sure you use the latest version of this script from github and try again
[https://github.com/ProtonVPN/protonvpn-cli](https://github.com/ProtonVPN/protonvpn-cli)

---

