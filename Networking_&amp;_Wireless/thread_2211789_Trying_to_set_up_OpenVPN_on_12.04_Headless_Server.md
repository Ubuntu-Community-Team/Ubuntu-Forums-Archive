---
title: "Trying to set up OpenVPN on 12.04 Headless Server"
date: 2014-03-17
forum: Networking &amp; Wireless
---

### Post by Howard_Perceval on 2014-03-17
Hello, this is my first post so apologies if I've not done this properly. 

I've got a number of virtual servers - all headless. I have set up squid on a proxyserver and now I'd like that server to connect to a VPN I subscribe to - so I can privately browse from my laptop and from all my servers. However, I don't seem able to set up OpenVPN, nothing seems to work. I created a test server and installed 13.10 Desktop on that and was able to connect using network manager (through a very slow remote desktop connection). However, I'm sure there must be a way to configure OpenVPN without having to use a GUI

My config file looks like this

client
remote *myvpn*.com
ca /etc/openvpn/ca.myvpn.com.crt
auth-user-pass
comp-lzo yes
dev tun
proto udp
nobind
auth-nocache
script-security 2
persist-key
persist-tun
user hperceval
group nogroup

(I've changed the remote ID and the CA Cert on the above). When I run it I get

hperceval@ProxyServer:~$ sudo openvpn /etc/openvpn/vyprvpn.conf
[sudo] password for hperceval:
Mon Mar 17 23:06:30 2014 OpenVPN 2.2.1 i686-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Feb 27 2013
Enter Auth Username:xxxxx123
Enter Auth Password:
Mon Mar 17 23:06:39 2014 WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Mon Mar 17 23:06:39 2014 NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Mon Mar 17 23:06:39 2014 LZO compression initialized
Mon Mar 17 23:06:39 2014 NOTE: UID/GID downgrade will be delayed because of --client, --pull, or --up-delay
Mon Mar 17 23:06:39 2014 UDPv4 link local: [undef]
Mon Mar 17 23:06:39 2014 UDPv4 link remote: [AF_INET]209.99.22.19:1194
Mon Mar 17 23:06:40 2014 [myvpn.com] Peer Connection Initiated with [AF_INET]209.99.22.19:1194
Mon Mar 17 23:06:42 2014 TUN/TAP device tun0 opened
Mon Mar 17 23:06:42 2014 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Mon Mar 17 23:06:42 2014 /sbin/ifconfig tun0 10.11.1.121 netmask 255.255.0.0 mtu 1500 broadcast 10.11.255.255
SIOCADDRT: File exists
Mon Mar 17 23:06:42 2014 ERROR: Linux route add command failed: external program exited with error status: 7
Mon Mar 17 23:06:42 2014 GID set to nogroup
Mon Mar 17 23:06:42 2014 UID set to hperceval
Mon Mar 17 23:06:42 2014 Initialization Sequence Completed

(I've tried to depersonalise the above!)

Once I get the Initialization message, the Putty session sits there without a command line until I kill the OpenVPN process through Webmin

I would be very grateful if anyone can help me with this - I've trawled the net but I just can't find an answer

Many thanks

---

