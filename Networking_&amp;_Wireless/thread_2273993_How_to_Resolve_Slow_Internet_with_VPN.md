---
title: "How to Resolve Slow Internet with VPN"
date: 2015-04-17
forum: Networking &amp; Wireless
---

### Post by forliberty on 2015-04-17
There have been quite a few threads on this issue of slow Internet while connected to a VPN, but none of them resolved my problem, and in reading the other threads, I noticed many other users who had tried the typical recommended solutions with no success. The problem in my case was that for some reason, my VPN connection acquired an incorrect subnet. Maybe this will help others. 

The root cause of the slow Internet problem often seems to be that for whatever reason, the local desktop is routing all Internet traffic through the VPN, so that, when browsing the Internet, you are actually using your VPN's Internet connection, rather than the local desktop's Internet connection. I was able to confirm this was true in my case by browsing to speedtest.net, which reported the name of my VPN's ISP, rather than my own ISP. 

The commonly recommended solutions are: 

1. Left-click your network connection tray icon, choose VPN Connections, then Configure VPN, then click on the VPN at issue and click Edit... 
2. Change one or all of the following settings in the IPv4 Settings tab:[INDENT]a.Change Method to Automatic (VPN) addresses only
b. Click the Routes button and then check "Use this connection only for resources on its network"
c. While in the Routes window, click "Add," and manually add the IP address(es) inside the VPN that you need to be able to access. (The metric does not seem to matter; Netmask is another name for Subnet.) 
[/INDENT]

I tried all of these recommended solutions, in varying combinations, but none of them worked. Either my Internet was still slow, or my VPN did not work. 

So finally I ran ifconfig from the terminal to check the status of all my network connections. Importantly, I ran ifconfig while connected to my VPN. What I found was that for some strange reason, the subnet for my VPN was incorrect. The solution was to manually add a route under the IPv4 Settings tab to the internal VPN address to which I needed access that had the CORRECT subnet. Voila! Fast Internet and no VPN problems.

---

