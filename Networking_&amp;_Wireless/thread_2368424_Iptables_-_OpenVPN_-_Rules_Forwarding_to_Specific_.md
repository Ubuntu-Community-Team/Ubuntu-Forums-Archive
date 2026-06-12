---
title: "Iptables - OpenVPN - Rules Forwarding to Specific Interface in Tunnel"
date: 2017-08-10
forum: Networking &amp; Wireless
---

### Post by endtimes on 2017-08-10
Hi everyone!  I need some assistance with writing iptables.  My environment consists of mixed linux flavors but I just need help with the iptables.  Any help would be greatly appreciated.


Here is my environment.

[LIST]
[*]AsusWRT-Merlin FW 380.67 on Asus RT-AC88U
[*]OpenVPN Client setup on my router using AirVPN
[*]OpenVPN Server enabled with 10.8.0.0/24
[*]Internal home LAN with 192.168.x.x/24
[*]I have a FreeNAS server running multiple jails
[LIST]
[*]192.168.1.26 = Transmission going through the OpenVPN client out to the internet
[/LIST]
[/LIST]
I'm having issues accessing only the Transmission jail at 192.168.1.26 on my home internal LAN when I VPN in. Transmission in my Freenas server is going through the a VPN configured on OpenVPN Clients page. As [Jack Yaz]("https://www.snbforums.com/members/jack-yaz.53009/") kindly pointed out, this is happening because under the 'OpenVPN Clients' tab in the router page, under 'Redirect Internet Traffic' option, I'm using 'Policy Rules Strict' setting. When I change it to just 'Policy Rules', I can ping and reach the Transmission server. Using the strict option increases security but requires a rule to be used that specifically targets the tunnel's interface to allow traffic to be forwarded. Please help em write this rule. Here is Merlin's explanation from his [changelog]("https://asuswrt.lostrealm.ca/changelog") for 380.66 (12-May-2017),


> NEW: Added new Internet redirection mode to OpenVPN clients
called "Policy Rule (Strict)". The difference from the
existing "Policy Rule" mode is that in strict mode,
only rules that specifically target the tunnel's
interface will be used. This ensures that you don't
leak traffic through global or other tunnel routes,
however it also means any static route you might have
defined at the WAN level will not be copied either.&#8203;

This brings me to iptables. Here is my nat-start script. My goal is to have a semi simple script with some security while allowing me to access the Trasmission IP. You'll see from my script that I tried different lines and when they didn't work, I just commented them out.
```
#!/bin/sh

iptables -I FORWARD -i br0 -o tun11 -j ACCEPT
iptables -I FORWARD -i tun11 -o br0 -j ACCEPT
iptables -I FORWARD -i br0 -o vlan1 -j DROP
#iptables -I INPUT -i tun11 -j REJECT
iptables -t nat -A POSTROUTING -o tun11 -j MASQUERADE
#iptables -t nat -A POSTROUTING -o tun21 -j MASQUERADE

iptables -t nat -I PREROUTING -i tun11 -p tcp --dport xxxxx-j DNAT --to-destination 192.168.1.26
iptables -t nat -I PREROUTING -i tun11 -p udp --dport xxxxx-j DNAT --to-destination 192.168.1.26
iptables -I FORWARD -i tun11 -p udp -d 192.168.1.26 --dport xxxxx--state RELATED,ESTABLISHED -j ACCEPT
iptables -I FORWARD -i tun11 -p tcp -d 192.168.1.26 --dport xxxxx--state RELATED,ESTABLISHED -j ACCEPT

```
Any help is very much appreciated.

[IMG]http://i.imgur.com/9DpQHg0.png[/IMG]

---

