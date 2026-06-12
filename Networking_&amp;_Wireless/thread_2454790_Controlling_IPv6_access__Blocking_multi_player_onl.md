---
title: "Controlling IPv6 access / Blocking multi player online gaming within office network"
date: 2020-12-06
forum: Networking &amp; Wireless
---

### Post by wowiesy2 on 2020-12-06
Hi,

I've setup a linux box with DNSMASQ and iptables to serve as a router / dhcp for a small office network. Setup is mostly done in IPv4.

Recently, I've discovered several dhcp leases to ipv6 devices (which I presume to be mobile devices). Somehow, some of our crew within the office, although not explicitly given access, has somehow hacked into the wifi password and obtained connectivity.  I have yet to study IPv6 so as to enable me to control access on this for now.  for IPv4, I have set up DNSMASQ to lease fixed IP addresses to known MAC addresses, while I only allow a limited number of IP addresses in the general pool to limit the possible "unknown" hosts.  I thought it was a good setup until I found that most mobile devices are now IPv6 capable...   Hope I can be pointed to the right direction on which IPv6 topics I need to get up to speed along this line... I believe I need to setup DNSMASQ and iptables as well for IPv6...  

Also recently discovered that certain authorized users within the network have been doing online multiplayer games through the company issued desktops, and I suppose perhaps tethering with their own mobile device/s.   I do not have specific knowledge as to which online player games these people do... I think if I just block UDP ports and just allow specific UDP ports that we use (through iptables) that should work..   will it?  It should right? Or is there any other items I need to be aware of when it comes to controlling access of network games?

---

### Post by TheFu on 2020-12-06
IPv6 has been enabled by default about 15 yrs on all devices.
If you aren't fully prepared to secure IPv6, you should disable it AND disable all attempts that devices (cough - Windows) will make to create a IPv6 tunnel through IPv4.

If end-user devices have direct access to the internet, then you've already failed.  No desktop should be able to ping google directly.  There should be a proxy server for all web-based access.  Your email server shouldn't allow any unauthenticated outbound messages and your WAN firewall should block all email traffic that doesn't go to or from your email server.  Don't allow any desktop to do dig lookups for internet locations.  Only gateway/proxy systems should have internet DNS capabilities.

If you want to go crazy, which is often necessary, make all proxy access authenticated, so each individual must authenticate 1 device at a time for access. Only 1 device, so the desktop has it by default.  Be prepared for managers and the C-suite people to complain. Getting some coverage from them would be good or at least find out whether they are willing to back the tighter security stance to better protect your network.

Where I've worked, we disabled all wifi. It wasn't allowed and 2x a day, we'd scan and pick up any unknown devices connected to the network. After a few weeks of this, people were missing their devices and finally learned not to enable wifi anywhere near work.

In short, don't let end devices have a default route to the internet, but only to a proxy server where all traffic is filtered.  This assumes you don't have a flat network.

---

