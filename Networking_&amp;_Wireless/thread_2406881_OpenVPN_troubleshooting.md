---
title: "OpenVPN troubleshooting"
date: 2018-11-27
forum: Networking &amp; Wireless
---

### Post by pekka2 on 2018-11-27
Hi,
trying to connect to a VPN server (running on my home router). I can connect my iPhone to the VPN, so I know the server is working.
When i try to connect my Kubuntu 18.10 laptop to the server via the network manager gui (right-clicking the network icon in system tray), the connection looks to be working, but the network isn't working (can'r load webpages or ping google.com for example). i use the same .ovpn config file in iPhone and laptop.
When I try it via command line (sudo openvpn --config Documents/client.ovpn), the output looks like it's working, but my external ip is the same as without the vpn.

The output from terminal:
```
$ sudo openvpn --config Documents/client.ovpn 
[sudo] password for pekka: 
Tue Nov 27 15:32:12 2018 OpenVPN 2.4.6 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [LZ4] [EPOLL] [PKCS11] [MH/PKTINFO] [AEAD] built on Sep  3 2018
Tue Nov 27 15:32:12 2018 library versions: OpenSSL 1.1.1  11 Sep 2018, LZO 2.10
Enter Auth Username: **
Enter Auth Password: *******************
Tue Nov 27 15:32:22 2018 WARNING: --ns-cert-type is DEPRECATED.  Use --remote-cert-tls instead.
Tue Nov 27 15:32:22 2018 TCP/UDP: Preserving recently used remote address: [AF_INET]87.92.174.237:1194
Tue Nov 27 15:32:22 2018 UDP link local: (not bound)
Tue Nov 27 15:32:22 2018 UDP link remote: [AF_INET]87.92.174.237:1194
Tue Nov 27 15:32:22 2018 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Tue Nov 27 15:32:23 2018 [RT-N66U] Peer Connection Initiated with [AF_INET]87.92.174.237:1194
Tue Nov 27 15:32:24 2018 WARNING: INSECURE cipher with block size less than 128 bit (64 bit).  This allows attacks like SWEET32.  Mitigate by using a --cipher with a larger block size (e.g. AES-256-CBC).
Tue Nov 27 15:32:24 2018 WARNING: INSECURE cipher with block size less than 128 bit (64 bit).  This allows attacks like SWEET32.  Mitigate by using a --cipher with a larger block size (e.g. AES-256-CBC).
Tue Nov 27 15:32:25 2018 WARNING: cipher with small block size in use, reducing reneg-bytes to 64MB to mitigate SWEET32 attacks.
Tue Nov 27 15:32:25 2018 TUN/TAP device tun0 opened
Tue Nov 27 15:32:25 2018 do_ifconfig, tt->did_ifconfig_ipv6_setup=0
Tue Nov 27 15:32:25 2018 /sbin/ip link set dev tun0 up mtu 1500
Tue Nov 27 15:32:25 2018 /sbin/ip addr add dev tun0 local 10.8.0.6 peer 10.8.0.5
Tue Nov 27 15:32:25 2018 Initialization Sequence Completed
```

I can't find anything from syslog, and /var/log/openvpn is empty.

---

### Post by TheFu on 2018-11-27
What is the intent of the VPN?  Access to your LAN or access to the internet?

I don't run VPN software on my routing equipment.  IMHO, routers shouldn't be used for that purpose, but if you run openvpn on another system inside the LAN, 
LAN access requires setting up a bridge from the tun0 to the LAN interface.
Internet access requires setting up a few firewall forwarding rules.

Both require setting up appropriate routes and DNS settings to be pushed to the clients.

In short, enabling openvpn isn't sufficient. It must be properly configured too.

And if you are going to the effort to setup your own VPN, why not use AES-256?

---

### Post by pekka2 on 2018-11-27
Hi,
thanks for the reply.
I want to be able to access my LAN, but also secure my internet when on a public wifi.
Why isn't it a good idea to use my router for this? Should I maybe try to run a VPN server on a Pi or something? 
I'm wondering about why this isn't working for my laptop, as it works for my phone.
And regarding AES-256, I have no idea what that is or how to set it up.

---

### Post by TheFu on 2018-11-28
Why not run a VPN on your router?  Step back a little and consider some issues.

* Just because something "works", that doesn't mean it is secure.
* Systems are only as secure as the weakest part.
* Is your router firmware constantly patched?   Weekly?
* Is the VPN server software continuously patched?
* Does your router have excess CPU and hardware support for AES-256 encryption?
* What happens when the VPN fails?  Do all connections drop completely or do packets still flow without notification?
* During a DoS attack against the ovpn service, better to have just ovpn crash than the entire router.
* How can you bypass the VPN when needed for services that don't work through a VPN?

Most home routers aren't properly maintained, having to wait months before commonly fixed code is fixed, if ever.  Vendor support for their own routers usually ends after just a few years, well before the hardware dies.  Do you buy a new router every 3 yrs when the firmware updates end?  

The open source routing software can be much better or much worse for updates, it just depends on the specific hardware to have a champion inside the router firmware team.  But these are "router people" who are sorta like gamers constantly seeking the newest equipment.  Some move from router to router every few months. When they lose interest in the hardware, support ends, silently.

Having poor security is worse than having no security.  Behavior online will be different whenever we believe full, unbreakable, security is working, even when it isn't. Best to be a little afraid since no solution is 100%, all the time.  These are not setup and forget tools, unfortunately.

For openvpn issues, you'll need to post some facts to get help.  Config files for the client and server, routing tables, bridge setups. "It doesn't work on Ubuntu" isn't exactly helpful.  There are a few things to check, like is the same cert being used by all clients?  Is the server configured to allow different clients to use the same cert?

When it comes to security, always use common sense as the first consideration. I'm always amazed when people use a password manager that pushes/stores their data in the cloud and they think it is secure. What does common sense say about that?

---

### Post by xadder on 2019-01-10
I am having similar problems, but while trying to run pritunl VPN as a client (so, somebody else's server, should be very secure). As with the post above, it looks as though I get a VPN connection (and printunl tells me I have been connected for XXx seconds, which increases continuously), but I can't access any websides or ssh to other machines.

This used to work fine, until 18.10 (and on another computer it still does!)

---

### Post by joshpratt on 2019-01-10
Open the Activities overview and start typing Settings.
Click Settings. 192.168.0.1
In the left pane, select the network connection to set up then click Wi-Fi.
Make sure your wireless card enabled or a network cable is plugged in.
Click settings button
Click iPv4 or IPv6 and change the Addresses to Manual.
Type in the IP Address and Gateway and Netmask.
In the DNS section, switch Automatic to OFF. Enter the IP address of a DNS server you want to use. Enter additional DNS server addresses using the + button.
In the Routes section, switch Automatic to OFF. Enter the Address, Netmask, Gateway and Metric for a route you want to use. Enter additional routes using the + button.
Click Apply.

---

### Post by joshpratt on 2019-01-10
Open the Activities overview and start typing Settings.
Click Settings. [SIZE=1][[COLOR=#a9a9a9]192.168.0.1[/COLOR]]("https://www.19216801.page/")[/SIZE]
In the left pane, select the network connection to set up then click Wi-Fi.
Make sure your wireless card enabled or a network cable is plugged in.
Click settings button
Click iPv4 or IPv6 and change the Addresses to Manual.
Type in the IP Address and Gateway and Netmask.
In the DNS section, switch Automatic to OFF. Enter the IP address of a DNS server you want to use. Enter additional DNS server addresses using the + button.
In the Routes section, switch Automatic to OFF. Enter the Address, Netmask, Gateway and Metric for a route you want to use. Enter additional routes using the + button.
Click Apply.

---

### Post by TheFu on 2019-01-10
Josh - this doesn't make his VPN work AND allow access to the LAN.

---

### Post by xadder on 2019-01-11
Just one  more thing: I am running Xubunbtu, and don't see any 'Activities overview'. I have a settings menu but that isn't a place to type IP addresses. But, if TheFu is right, I manye don't need to worry about that anyway?

Just now I am in the office, where pritunl (also on Xubuntu 18.10) works perfectly. I there any info I can print out from here that I can compare with my non-working home notebook's data? Thanks.

---

### Post by TheFu on 2019-01-11
xadder, please don't hijack someone else's thread. Start your own.

---

### Post by xadder on 2019-01-11
Sorry, I thought OpenVPN troubleshooting fitted my problem pretty well. I can start another thread though.

---

