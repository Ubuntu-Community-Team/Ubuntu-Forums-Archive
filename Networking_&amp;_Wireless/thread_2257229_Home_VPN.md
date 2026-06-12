---
title: "Home VPN"
date: 2014-12-18
forum: Networking &amp; Wireless
---

### Post by Richard_Romick on 2014-12-18
Right now I am trying to set up a VPN connection to my house and could use some help.  

My setup is as follows
-------------------------
At my location: 
Ubuntu 14.10 laptop (Client)

At home:
Windows 8.1 Desktop
Ubuntu 14.04 server

Right now, I am using Teamviewer to remote into my Windows 8.1 computer and manage the Ubuntu server.  I would like to set up a VPN so, when I connect, it is as if I was connected to the LAN.  I have made some attempts to configure openVPN (I could establish a connection, but no traffic would go over the VPN), and pptpd (would not connect).  I eventually resorted to setting up a connection on my Windows 8.1 desktop to accept incoming pptp connections, but that failed to connect to.

My knowledge of VPNs is simple, but am willing to learn.  I know how to set up port forwarding on my router at least.  Does anyone know a relatively simple VPN solution I can use?

---

### Post by TheFu on 2014-12-18
pptp is the simple VPN (because it has been hacked numerous times). There are how-to videos for this on youtube ... hak5 has done one.

You can use ssh as a poor-mans VPN. It allows forwarding of ports thru a secure channel. It is really easy to get working and pretty much works, always, from anywhere.  The internet servers are maintained by admins like me over ssh connections and with tools that leverage those connections for thousands of servers.  Plus, most people don't really need a full VPN, they just want remote access to files and servers - ssh, scp and sftp are all part of the same server tools. These all work well and are secure from anywhere in the world if you use key-based authentication, never passwords.  There are great sftp clients for every platform that does networking.  WinSCP is nice on Windows.  Any file manager on Linux should support the sftp:// URL.
[http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html](http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html) might be eye opening.

OpenVPN can use a few different encryption methods. Most people deploy it with SSL-based encryption, but L2TP and IPSec are also available, which requires more overhead and configuration. Because openvpn is so very capable, there are thousands and thousands of options, decisions, and lots of learning to do before deployment.  Only you can decide how important security is, which leads to different OVPN configurations.

To me, the idea of trusting any 3rd party service when I'm not paying them for access to an internal network just-seems-WRONG, but that is me.

When I'm away from home, if I need access to a Windows machine, I securely connect to a Linux remote desktop (x2go) then from that, use rdesktop inside the LAN to the Windows machine. Works well enough for productivity apps and managing a media center (not watching videos).  x2go as a remote desktop is the fastest, by far, of the non-commercial options. Plus you don't need to trust any 2rd party, and it uses ssh for security and will honor ssh-keys, as all good clients should.  On 12.04 and earlier, I used freeNX for remote desktops, but x2go has replace it since 14.04.  This stuff basically works so well that I don't think about it at all.

In fact, I'm on a Win7 laptop now, remoted into an Ubuntu 14.04 desktop (running plain openbox, not Unity) writing this now.  On the LAN, video works, but over hotel wifi, only remote music and lower bandwidth stuff work well from pretty much any country in the world with broadband.

---

### Post by Richard_Romick on 2014-12-22
The SSH solution sounds good to me.  Just to be clear, will I be able to start the VPN and then browse my home network/internet as if I was really there?

---

### Post by TheFu on 2014-12-22
ssh is not a VPN, it is a secure connection.  That's why we call it a poor-man's VPN.
If you want to browse files on your home server, use winscp on Windows or any linux file browser with the sftp:// URL.  On the remote server, just having the ssh server running and the firewall port forwarding to that server open.  Try this stuff from inside your network to see that it all works.

Of course, you'll need to have standard network stuff setup - static IPs for the servers you want to access inside your LAN and a way to find your home when on the internet. There are many, many, many how-to guides for that - look for "dynamic DNS" or just check what the public IP is before you leave the house in the morning and use that. If this isn't clear, you will have to struggle and learn some networking stuff before it will work. After you understand it, that knowledge will work for you the rest of your life.  It is hard for me to tell how much of this stuff you understand.

Browsing files on the Widnows machine at the house directly will NOT be possible over sftp. You'll want to use samba-client to make those files available to the home Linux machine first, then sftp can access them just fine.  Windows does not include a secure file sharing technology like sftp and I don't thing any of the Windows ports are secure enough to use (they have been hacked). Best to just use the Linux sftp server that is built into openssh-server. Install openssh-server and fail2ban, to get started.

ssh itself is just a CLI tool - no GUI.  Don't expect to use most Windows tools. Do you use Windows at all outside your network?

---

### Post by houstonbofh on 2014-12-22
Since you tried on two devices and failed, I suspect it is your router or ISP which are the problems, and not Ubuntu.

---

### Post by TheFu on 2014-12-22
> **houstonbofh said:**
> Since you tried on two devices and failed, I suspect it is your router or ISP which are the problems, and not Ubuntu.

Perhaps.  Is the router ports that you need setup to forward from the WAN to the LAN to allow the VPN/ssh traffic from outside to the specific host inside?

---

### Post by houstonbofh on 2014-12-24
Yes.  And you may also need a "helper" in the router.

---

### Post by Richard_Romick on 2014-12-26
There were quite a few replies to my posting that I didn't see while I was trying a few things out.  Thanks for being so helpful.

Right now I am attempting to set up a SSH VPN.  When I manage to get that working, I plan on working my way towards more advanced VPN solutions.  My attempts so far have been met with relative success, I can connect to my network and interact with other devices as if I was there.  However, I run into problems when I try to route internet traffic through.  If anyone can figure out why, I would greatly appreciate it.

Remote location IP: 192.168.0.0/24          
Home IP: 192.168.8.0/24

Client:
sudo ssh -NTCf -w 0:0 [homeIP]             

Server:
ip link set tun0 up
                                                            ip addr add 192.168.8.100/32 peer 192.168.8.200 dev tun0

Client:
ip link set tun0 up
ip addr add 192.168.8.200/32 peer 192.168.8.100 dev tun0

#At this point I can ping the Server from the Client machine and vice versa.

Client:
ip route add 192.168.8.0/24 via 192.168.8.200

Server:
                                                            sudo arp -sD 192.168.8.200 p3p1 pub #for some reason, my eth0 interface is called p3p1
                                                            
#At this point, I can ping other machines on my home network and interact with my NAS

Client:
ip route add [homeIP]/32 via 192.168.0.1

ip route replace default via 192.168.8.1
    RTNETLINK answers: Network is unreachable

Client config:
senlis@senlis-Galago-UltraPro:/etc/network$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether 00:90:f5:ec:24:a1 brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 0c:8b:fd:6c:05:b6 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.35/24 brd 192.168.0.255 scope global wlan0
       valid_lft forever preferred_lft forever
    inet6 fe80::e8b:fdff:fe6c:5b6/64 scope link 
       valid_lft forever preferred_lft forever
4: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN group default qlen 500
    link/none 
    inet 192.168.8.200 peer 192.168.8.100/32 scope global tun0
       valid_lft forever preferred_lft forever

senlis@senlis-Galago-UltraPro:/etc/network$ ip route
default via 192.168.0.1 dev wlan0  proto static 
68.97.181.176 via 192.168.0.1 dev wlan0 
192.168.0.0/24 dev wlan0  proto kernel  scope link  src 192.168.0.35  metric 9 
192.168.8.0/24 via 192.168.8.200 dev tun0 
192.168.8.100 dev tun0  proto kernel  scope link  src 192.168.8.200 

Server config:
root@ubuntuServer:~# ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: p3p1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 10:bf:48:21:04:e4 brd ff:ff:ff:ff:ff:ff
    inet 192.168.8.21/24 brd 192.168.8.255 scope global p3p1
       valid_lft forever preferred_lft forever
    inet6 fe80::12bf:48ff:fe21:4e4/64 scope link
       valid_lft forever preferred_lft forever
3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 94:db:c9:af:51:c5 brd ff:ff:ff:ff:ff:ff
4: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN group default qlen 500
    link/none
    inet 192.168.8.100 peer 192.168.8.200/32 scope global tun0
       valid_lft forever preferred_lft forever

root@ubuntuServer:~# ip route
default via 192.168.8.1 dev p3p1
192.168.8.0/24 dev p3p1  proto kernel  scope link  src 192.168.8.21
192.168.8.200 dev tun0  proto kernel  scope link  src 192.168.8.100

---

### Post by TheFu on 2014-12-26
There are settings in your profile to get an email for subscribed threads. Very handy. Basically, only the topics you are interested in enough to create or reply.

---

### Post by Richard_Romick on 2014-12-26
> **TheFu said:**
> There are settings in your profile to get an email for subscribed threads. Very handy. Basically, only the topics you are interested in enough to create or reply.

I will have to look into my settings.  i used to get emails about replys on threads, but am not getting them now for some reason.  Maybe a casualty of me cleaning out my inbox and stopping email subscriptions, I cancelled this one.

To answer your earlier questions, I am forwarding traffic to my Ubuntu Server.  In this case, I am forwarding port 22 traffic to my Ubuntu Server at 192.168.8.21.

---

### Post by TheFu on 2014-12-27
What have you done, tried, exactly?  Please show commands.

Forget all the port forwarding stuff.
* can you ssh?
* can you use sftp?

If you need a full VPN, then use openvpn, not ssh. However, for 99% of the needs I've seen in 20+ yrs, ssh does it all.

---

### Post by Richard_Romick on 2014-12-28
> **TheFu said:**
> What have you done, tried, exactly?  Please show commands.

Forget all the port forwarding stuff.
* can you ssh?
* can you use sftp?

If you need a full VPN, then use openvpn, not ssh. However, for 99% of the needs I've seen in 20+ yrs, ssh does it all.

The answer to both questions is yes.  I recognize that openvpn is a better solution than ssh, and plan on pursuing it at some point after I get the ssh VPN working.

---

### Post by TheFu on 2014-12-28
> **Richard_Romick said:**
> The answer to both questions is yes.  I recognize that openvpn is a better solution than ssh, and plan on pursuing it at some point after I get the ssh VPN working.

openvpn is a better solution for "forward everything" requirements. It comes with significantly higher complexity.

ssh is enough for 
* secure remote access to files via sftp
* secure remote filesystem access via sshfs
* secure remote CLI/shell access to systems with plain ssh
* secure remote desktops via x2go/freenx
* secure remote file replication with rsync (ssh is the default rsync protocol)
* secure port forwarding of selected ports
* secure remote editing with vim/gvim and other editors
* pseudo-VPN with sshuttle <-- this may be helpful.

ssh really is the toolbox for remote connectivity.  More ssh tips: [http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html](http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html)

Anyway - just wanted you know give ssh more of a chance, if it might fit your needs. I think it is 10x easier than openvpn for a single-user environment.  

In a multiuser environment with different access needs for different groups of users, openvpn blows away ssh, once the configurations are setup. But like all pure-VPN solutions, it is really a one-trick pony.  Provides access to a subnet (or subnets), securely by routing all traffic there. Other tools are necessary to access files, remote desktops, editing, replicate, etc....

---

### Post by Richard_Romick on 2014-12-29
I'm going to check out sshuttle, that may be more of what I am looking for.  I would like to foward Netflix traffic through the SSH VPN, since at my deployed location region locking prevents me from watching it normally.  I also need to figure out why I can't log in via SSH using RSA certificates, even though it appears I have it configured right.

---

### Post by TheFu on 2014-12-29
For netflix - you need openvpn.  tcp has too much overhead. Cannot say anything more.

---

