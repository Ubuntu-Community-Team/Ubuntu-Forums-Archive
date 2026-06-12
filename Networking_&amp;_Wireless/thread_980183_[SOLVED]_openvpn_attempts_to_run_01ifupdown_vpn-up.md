---
title: "[SOLVED] openvpn attempts to run 01ifupdown vpn-up"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by ragtag on 2008-11-12
I'm trying to set up openvpn on 8.10. It actually works if I put my config file in /etc/openvpn, but what I want to do is use the NetworkManager.

I've got everything configured in the NetworkManager and the connection is established. I can ping the vpn server at 10.0.x.x and the server sends domain and dns info (seen by watching the log). But it fails running /etc/NetworkManager/dispatcher.d/01ifupdown vpn-up because there is no vpn-up option in that script, so resolvconf never gets run.

/etc/openvpn/update-resolve-conf seems to contain the code. Except it's bash and 01ifupdown is a sh script. I tried copying the code and adding vpn-up and vpn-down options to the case in 01ifupdown, but that did not work.

Has anyone solved this in some clever way? I guess I could write code in 01ifupdown that does the same as update-resolve-conf, but I'm not particularly good at shell scripting. :)

---

### Post by ragtag on 2008-11-12
I found a solution that works, even though 01ifupdown vpn-up still gets called and gets an error in return.

Go into System>Preferences>Network Configuration (or Configure VPN in the NetworkManager applet). In the vpn edit the settings for your VPN connection.

Hit the IPv4 Settings tab.
Hit the Routes... button at the bottom.
Check "Ignore autmoatically obtained routes."

That's it. Now it gets all the DNS settings right. Why this works I have no idea.

:-\"

---

