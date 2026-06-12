---
title: "[SOLVED] Internet Connection Sharing: can't ping"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by The Foz on 2008-11-19
I have been trying (and failing) to set up ICS (Internet Connection Sharing) on my server.

I have been using several How-To guides from the forums. Now I can no longer even ping on the Internet interface, and I can't work out how to undo whatever is causing the problem.

When I run 'ping -I ppp0 <ip_address>' I get the message "ping: sendmsg: Operation not permitted".

My network config is:
eth0: 192.168.0.1 static (currently disconnected for testing)
ppp0: dynamic (this is a Huawei E220 USB UMTS modem)

The PPP connection is established OK with wvdial and with Gnome-ppp. An IP address is assigned for ppp0, and DNS servers are set (they appear in my resolve.conf). When I started trying to set up ICS, I was able to connect to the internet once the pppd was started (browsing, email, ping, etc.).

I followed the How-To guides,and did as follows:
[LIST=1]
[*]iptables -A FORWARD -i eth0 -o ppp0 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
[*]iptables -A FOWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
[*]iptables -A POSTROUTING -t nat -j MASQUERADE
[/LIST]
Doing the above didn't get ICS working, but also didn't break anything. The entries in iptables are reset after a reboot, and after running '/etc/init.d/networking restart' so I have tested with and without these.

In addition I tried: 'route add default ppp0'. This also didn't get ICS working, but also didn't break anything.

I also set up forwarding:
'sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward" '
and added to /etc/sysctl.conf -
net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1

When I try to ping without specifying the interface to use, the ping attempts are going to ppp0, so it seems that ppp0 is my default route. I can ping to eth0 by specifying the interface, and this works without error.

Does anyone have any ideas why I can no longer ping or access the internet?

My next step will be to undo the changes to /proc/sys/net/ipv4/ip_forward" & /etc/sysctl.conf. After that, the system **should **be back to how it was before. If that doesn't work, I will probably try to flush iptables. Any other suggestions would be welcome.

---

### Post by SpaceTeddy on 2008-11-19
operation not permitted comes from your kernel blocking the packets. This means, that you have done more iptables rules than you have written down here. Most likely, your INPUT and OUTPUT chain are on DROP or REJECT. Open them up again and pinging will work again. At leat the loopback should be able to connect to itself :)

these are generic commands that will allow any traffic passing from, through and to your server:
```
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
```

and taking the ip_forwarding out again does not make a difference here :)

hope this helps :)

PS: if this fixes the problem at hand, you should read up on how iptables really works...

---

### Post by The Foz on 2008-11-21
I fixed it.

It was indeed a problem with the firewall.

I am using Firestarter. All I had to do was to go into the preferences and set the Network preferences for Internet Connection sharing & DHCP.

Cool.

---

