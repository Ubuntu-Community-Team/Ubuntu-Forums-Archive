---
title: "Authentication Required for OpenVPN"
date: 2014-02-02
forum: Networking &amp; Wireless
---

### Post by MrPez on 2014-02-02
I'm trying to set up Vypr OpenVPN on 12.04.  I've followed all the instructions on their website: [https://www.goldenfrog.com/support/vyprvpn/vpn-setup/linux/openvpn](https://www.goldenfrog.com/support/vyprvpn/vpn-setup/linux/openvpn)
When I try and connect all I get is "Authentication Required" which stays for a while and eventually times out and goes back to my normal wifi.
I have tried on another computer which has what I thought was an identical set up and it works fine.  The only difference was that on that computer I was asked for my keychain password.  Once I put that in it connected up ok.
Any thoughts or suggestions?

---

### Post by MrPez on 2014-02-08
In case anyone comes across this thread, I got it working with pptp vpn.  My problem was I had PGL - peer guardian - running in the background and had forgotten about it.  Kinda obvious now but took a while to figure it out!

---

