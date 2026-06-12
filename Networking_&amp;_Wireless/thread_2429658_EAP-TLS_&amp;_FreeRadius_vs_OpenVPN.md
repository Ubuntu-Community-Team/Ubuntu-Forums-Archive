---
title: "EAP-TLS &amp; FreeRadius vs OpenVPN"
date: 2019-10-21
forum: Networking &amp; Wireless
---

### Post by aljames2 on 2019-10-21
At home I have a Unifi access point on a separate physical interface than trusted LAN.  The AP is set up to operate on 2 subnets, 1 for IoT devices and a separate VLAN subnet intended for my trusted wireless laptops to gain access to the LAN for server administration.  All this is local, at home, no remote access.  My router is pfsense.

I’ve read that eap-tls with freeradius & firewall rules on the pfsense can be configured to allow only the laptop IPs via secure authentication & encryption.  I’m curious which is best, eap-tls, or using OpenVPN?  Thinking that later I may want to expand to allow remote VPN access.  For now though, the goal is to hop from my wireless AP into LAN securely without allowing everyone in.

---

### Post by Skaperen on 2019-10-21
this might be more of a security question.

---

