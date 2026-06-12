---
title: "iptables, dnsmasq, netflix and a vpn - advanced routing help!"
date: 2015-03-13
forum: Networking &amp; Wireless
---

### Post by sjhupp on 2015-03-13
Ok, getting beyond my ability here, so asking for some help from the better educated community please!
I have a VPN account already that I use, and just signed up for netflix. I'd like to do some type of DNS forwarding through my vpn.
I have an ubuntu 14.04 server and on it a virtual machine (10.0.0.17) that runs an openvpn client and connects to a US vpn, and provides a gateway function.
My cable modem is my regular default gateway on 10.0.0.1, and I'm not in the US.
So anyway, set up a PS3, android tablet and PC for netflix access, and set each to use the VM (.17) as the default gateway.
Netflix works fine, but I would really like a cleaner solution that only sends netflix related traffic via the VPN tunnel, leaving all other traffic to go via 10.0.0.1 as per normal.

So tried setting up another VM with ubuntu 14.04 server (10.0.0.13) and enabled v4 forwarding on it, gateway 10.0.0.1.
Then I edited /etc/iproute2/rt_tables and added a new table, 17 usvpn.
and made some rules:
        sudo ip rule add from all fwmark 17 table USVPN
        sudo ip route add default via 10.0.0.17 dev br0 table USVPN
        sudo ipset create netflix hash:ip
        sudo ipset add netflix 198.45.48.0/20 
        ... (added a few more ranges I found for it too)
        sudo iptables -A PREROUTING -t mangle -s 10.0.0.188 -m set --match-set netflix dst -j MARK --set-mark 17

So I tried to get my clients (both a PS3 with mac address, also tried an ubuntu desktop VM and it's IP .188 as source) to have a default gateway of the 10.0.0.13 VM, and get that VM to split traffic for me, but no go :(
I'm getting confused with all the googling I've done, and the options for iptables, so hoping someone can help.
Since the traffic (from netflix client) is coming into VM .13 I assume prerouting is the correct chain?

Looks like it's getting packets, but even when I added an IP for dnsleaktest.com into the ipset, client still didn't appear to go via the vpn tunnel.

sudo iptables -L -t mangle -nv
Chain PREROUTING (policy ACCEPT 1172 packets, 118K bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 MARK       all  --  *      *       10.0.0.188           0.0.0.0/0            match-set netflix dst MARK set 0x11

I also had a quick go at using dnsmasq to send netflix.com domain requests to 10.0.0.17 but no good either. 
Before I waste more time stabbing in the dark, wondering if anyone has some suggestions?

Have seen some blogs on using a US based VPS as a DIY solution, but as I already have a VPN, I'd love to make use of it rather than spend more money.
Thanks for reading anyway.
Cheers.

---

### Post by sandyd on 2015-03-14
Hi,

From the [Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules"):
> 
We do not support circumventing TOS, EULA, etc here

This including bypassing Netfix's TOS regarding the location of the viewer.
CLosed.

---

