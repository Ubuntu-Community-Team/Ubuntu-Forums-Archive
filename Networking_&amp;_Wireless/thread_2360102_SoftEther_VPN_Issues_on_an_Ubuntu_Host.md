---
title: "SoftEther VPN Issues on an Ubuntu Host"
date: 2017-05-01
forum: Networking &amp; Wireless
---

### Post by keith_s2 on 2017-05-01
Having some issues using a virtual Ubuntu 16.04 server to host a SoftEther VPN.

[COLOR=#242729][FONT=Arial]I'm trying to setup a sandbox infrastructure within virtual box VMs for development purposes. Right now, there's only 3 servers - the VPN Gateway Server., the Sentora Webserver (which also serves as the DNS Server for the VPN), and the API Development Server.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]All three servers are connected to eachother using a VirtualBox internal network named "protonet." The VPN server has one other connection as a Bridged Adapter so that outside computers can access it. That bridged connection is the primary one on the VPN Server.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The VPN hub is a SecureNAT HUB with a local bridge going to the 'protonet' VBox internal network. Promiscuous Mode is enabled across all VMs and all networking interfaces.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The subnet for the internal network is 10.1.0.1-255, and the subnet for the SecureNAT DHCP server is 10.1.1.2-255. The VPN server sits at 10.1.0.2, the API Development server at 10.1.0.3, and the DNS Server at 10.1.0.4. The gateway for all servers, except for the VPN Server, is set to be 10.1.0.1. The VPN server uses the gateway for the Bridged Adapter... 192.168.1.1. Right now, I'm testing this with two clients... one sitting at 10.1.1.2 and the other at 10.1.1.3 - the SecureNAT host server is sitting at 10.1.1.1. Clients are configured to take 10.1.1.1 as the gateway, 10.1.0.4 as the primary DNS Server, and then 8.8.4.4 as the secondary DNS Server.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Basically, this is what's happening. When the VPN Virtual Hub first starts up/goes "Online," there's no issue. I can ping the servers successfully from the client machine, and can access the various resources.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]After about 15-30 seconds, this all stops, and I can get various errors from a simple timeout, ranging to a flat-out connection refused error (Firewalls are opened as needed on the servers, and the firewall is shut off on the VPN Server). The only "error" message in the logs when this occurs is:[/FONT][/COLOR][INDENT]2017-04-28 22:02:26.564 [HUB "myFirstHUB"] SecureNAT: It has been detected that the Kernel-mode NAT for SecureNAT can be run on the interface "ipv4_rawsocket_virtual_router". The Kernel-mode NAT is starting. The TCP, UDP and ICMP NAT processings will be performed with high-performance via Kernel-Mode hereafter. The parameters of Kernel-mode NAT: IP Address = "10.171.7.254", Subnet Mask = "255.255.255.252", Default Gateway = "10.171.7.253", Broadcast Address = "10.171.7.255", Virtual MAC Address: "DA-3C-D5-82-9D-0E", DHCP Server Address: "10.171.7.253", DNS Server Address: "192.168.1.1"
[/INDENT]
[COLOR=#242729][FONT=Arial]What's even more odd is that, even while this is all working, the client IPs can *not* be pinged from the VPN Gateway, nor from any of the servers behind it... even while they can be pinged and successfully used by the clients themselves. After the connection breaks down, the client can still ping the host machine - but only because it's also sharing the 192.168.1.1 network with it, most likely.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I've tried pretty much everything at this point: - Deleting the server configuration and starting from scratch - Verifying that the clients are still connected to the hub itself (they are) - Checked Windows Event Viewer for Logs (The only logs shown are for complaining that the PC is not the master browser, but these are inconsistent with when functionallity actually stops) - Tried opening the server in forced user mode (ie., instead of service vpnserver start, using cd /usr/local/vpnserver;./vpnserver start) - Rebooting the VMs within the infrastructure as well as the physical machine itself (done this multiple times, actually) - Tried creating a new Virtual HUB completely - Tried changing the entire SecureNAT subnet - Tried removing the Local Bridge[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Could anyone potentially have some further insight as to what is causing this weird issue? I strongly suspect it has something to do with it going into kernel mode automatically, and getting those strange 10 dot IPs, but I don't know if that occurs due to something else that's also causing thee connection issues, or if that's causing it, I'm not finding anything on Google as to what I should be doing to prevent it from happening/taking the proper SecureNET IP Addresses as setup in SecureNAT.

I attached a diagram of my configuration to hopefully show my setup a bit better.

[IMG]https://i.stack.imgur.com/oji2c.png[/IMG]

Also posted asking for help here as well. [https://superuser.com/questions/1204606/softether-vpn-exhibits-bizarre-behavior](https://superuser.com/questions/1204606/softether-vpn-exhibits-bizarre-behavior)

Anyone have any ideas?

E: So not 10 minutes after I posted this, [/FONT][/COLOR][COLOR=#242729][FONT=Arial]I finally found the answer. [/FONT][/COLOR][COLOR=#242729][FONT=Arial]The solution was to change the setting DisableIpRawModeSecureNAT to true/1 in the Virtual HUB Configuration settings. Very relieved I got this all figured out now.[/FONT][/COLOR]

---

