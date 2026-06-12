---
title: "Unable to establish SSH Connection through Router"
date: 2019-06-19
forum: Networking &amp; Wireless
---

### Post by dillius2 on 2019-06-19
I know there are a ton of these posts, but I've done a number of the intermediate steps and am just unable to figure out where to go next.

I have an ISP provided modem, performing IP Passthrough to my router. My router is then set to forward my ssh port (21212) to a machine on my network. (I have also tried enabled DMZ, no change in behavior).

I have no issues connecting from within the network using multiple machines.

The IP Tables list output on the server is as follows:

```
iptables -L
```

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

Using a VPN and attempting to connect while watching tcpdump (ignoring my local device which is already established) I see the following: 

```
tcpdump port 21212 and host not 10.0.0.12 -n -Q inout
```

```
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
20:04:23.090426 IP 193.37.253.114.59549 > 10.0.0.219.21212: Flags [S], seq 1460164534, win 64240, options [mss 1360,nop,wscale 8,nop,nop,sackOK], length 0
20:04:24.089083 IP 193.37.253.114.59549 > 10.0.0.219.21212: Flags [S], seq 1460164534, win 64240, options [mss 1360,nop,wscale 8,nop,nop,sackOK], length 0
20:04:26.087920 IP 193.37.253.114.59549 > 10.0.0.219.21212: Flags [S], seq 1460164534, win 64240, options [mss 1360,nop,wscale 8,nop,nop,sackOK], length 0
20:04:30.060631 IP 193.37.253.114.59549 > 10.0.0.219.21212: Flags [S], seq 1460164534, win 64240, options [mss 1360,nop,wscale 8,nop,nop,sackOK], length 0
20:04:38.057957 IP 193.37.253.114.59549 > 10.0.0.219.21212: Flags [S], seq 1460164534, win 64240, options [mss 1360,nop,wscale 8,nop,nop,sackOK], length 0
```

I'm not sure what's going on, I don't know tcpdump as well as I should. It seems like the packets are getting received but dropped, making me think it has something to do with my SSHD configuration, but I can't find anything there which would cause such an issue.

Does anyone have any suggestions for next steps? Any ideas would be appreciated.

---

### Post by again? on 2019-06-19
Only have a basic knowledge of ssh but for me your tcdump command only works on port 22, even when 22 is forwarded to a different port in the router.
Connected via ssh from my phone over WAN.

---

### Post by SeijiSensei on 2019-06-19
First step is to use "ssh -vvv hostname" to increase the verbosity of the SSH client.

---

### Post by dillius2 on 2019-06-19
Verbose output of SSH attempt:

```
OpenSSH_7.9p1, OpenSSL 1.1.1a  20 Nov 2018
debug1: Reading configuration data /etc/ssh/ssh_config
debug2: resolve_canonicalize: hostname 172.6.126.69 is address
debug2: ssh_connect_direct
debug1: Connecting to 172.6.126.69 [172.6.126.69] port 21212.
debug1: connect to address 172.6.126.69 port 21212: Connection timed out
ssh: connect to host 172.6.126.69 port 21212: Connection timed out
```

It really does seem to just be ignoring the packets. Maybe there is an issue with how my router is forwarding the port... Or do I need to allow another range of ports in for after the connection is established with SSH?

---

### Post by TheFu on 2019-06-19
ssh uses 1 port.
Many routers can use port translation to convert the WAN port to an IP:port on the LAN.  On the LAN, I use the default 22/tcp port for ssh. On the WAN, I use some high, not standard port outside any likely-to-be-used ranges.

WAN:63099/tcp --> LAN:22/tcp

So, I can access the the LAN system via ssh and use my public domainname to access the same machine through the WAN port.  This way I can test the WAN access from inside the LAN. Not all routers will allow the WAN port to be accessed from inside. It is a security feature.

So I never need to know the actual port, my ~/.ssh/config file has different stanzas for each connection. Both documentation AND automatically fills in the port, userid, and other settings for the connection.  Different aliases for different sorts of connections through different ports. 

My troubleshooting steps: [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections) but starting with extra verbosity as SeijiSensei suggested is a good first step.  Looks like the sshd on the machine isn't being touched, so the router is the likely issue.

---

### Post by dillius2 on 2019-06-20
I reconfigured my sshd to run on 21212, so my port forward on the router is just 21212 -> 21212. I am able to successfully connect locally, so that part at least I know is correct.

I believe the port forward itself is working because tcpdump shows traffic being received on that port when I do it. However a connection is never established and I don't see anything in the system logs unless I'm just missing one... I tailed the entire contents of /var/log.

---

### Post by TheFu on 2019-06-20
Did you work through the troubleshooting steps in the link?
Does the client know the server by the name you are using to access it?

If so, I'd create new accounts on both systems and leave the defaults for everything. Create a new key and use ssh-copy-id.

Are there any match address stanzas?
Any TCP wrappers preventing access via hosts.allow/deny?

---

### Post by Doug S on 2019-06-20
Show us the output as per below (in my case it's port 22):

```
doug@s15:~/ubuntu-help/16.04/serverguide$ [COLOR="#FF0000"]sudo netstat -tlunp[/COLOR]
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.122.1:53        0.0.0.0:*               LISTEN      2659/dnsmasq
tcp        0      0 10.0.3.1:53             0.0.0.0:*               LISTEN      2188/dnsmasq
[COLOR="#FF0000"]tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      2028/sshd[/COLOR]
udp        0      0 192.168.122.1:53        0.0.0.0:*                           2659/dnsmasq
udp        0      0 10.0.3.1:53             0.0.0.0:*                           2188/dnsmasq
udp        0      0 0.0.0.0:67              0.0.0.0:*                           2659/dnsmasq
udp        0      0 0.0.0.0:67              0.0.0.0:*                           2188/dnsmasq
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1576/dhclient

```I like to use tcpdump to help with debugging also, but never used the "-Q" option before.

---

### Post by dillius2 on 2019-06-20
```
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      492/rpcbind
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN      700/dnsmasq
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      16595/cupsd
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      9809/smbd
tcp        0      0 0.0.0.0:873             0.0.0.0:*               LISTEN      27936/rsync
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      32692/mysqld
tcp        0      0 0.0.0.0:21212           0.0.0.0:*               LISTEN      9724/sshd
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      9809/smbd
tcp6       0      0 :::111                  :::*                    LISTEN      492/rpcbind
tcp6       0      0 :::80                   :::*                    LISTEN      15408/apache2
tcp6       0      0 :::53                   :::*                    LISTEN      700/dnsmasq
tcp6       0      0 ::1:631                 :::*                    LISTEN      16595/cupsd
tcp6       0      0 :::3128                 :::*                    LISTEN      875/(squid-1)
tcp6       0      0 :::3129                 :::*                    LISTEN      875/(squid-1)
tcp6       0      0 :::3130                 :::*                    LISTEN      875/(squid-1)
tcp6       0      0 :::445                  :::*                    LISTEN      9809/smbd
tcp6       0      0 :::873                  :::*                    LISTEN      27936/rsync
tcp6       0      0 :::21212                :::*                    LISTEN      9724/sshd
tcp6       0      0 :::139                  :::*                    LISTEN      9809/smbd
udp        0      0 0.0.0.0:631             0.0.0.0:*                           16597/cups-browsed
udp        0      0 0.0.0.0:668             0.0.0.0:*                           492/rpcbind
udp        0      0 0.0.0.0:35563           0.0.0.0:*                           7963/openvpn
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           523/avahi-daemon: r
udp        0      0 0.0.0.0:46480           0.0.0.0:*                           523/avahi-daemon: r
udp        0      0 0.0.0.0:53              0.0.0.0:*                           700/dnsmasq
udp        0      0 0.0.0.0:68              0.0.0.0:*                           613/dhclient
udp        0      0 0.0.0.0:111             0.0.0.0:*                           492/rpcbind
udp        0      0 10.0.0.255:137          0.0.0.0:*                           9857/nmbd
udp        0      0 10.0.0.219:137          0.0.0.0:*                           9857/nmbd
udp        0      0 0.0.0.0:137             0.0.0.0:*                           9857/nmbd
udp        0      0 10.0.0.255:138          0.0.0.0:*                           9857/nmbd
udp        0      0 10.0.0.219:138          0.0.0.0:*                           9857/nmbd
udp        0      0 0.0.0.0:138             0.0.0.0:*                           9857/nmbd
udp        0      0 0.0.0.0:39175           0.0.0.0:*                           875/(squid-1)
udp6       0      0 :::53798                :::*                                875/(squid-1)
udp6       0      0 :::668                  :::*                                492/rpcbind
udp6       0      0 :::5353                 :::*                                523/avahi-daemon: r
udp6       0      0 :::53                   :::*                                700/dnsmasq
udp6       0      0 :::111                  :::*                                492/rpcbind
udp6       0      0 :::49265                :::*                                523/avahi-daemon: r

```

---

### Post by dillius2 on 2019-06-20
> **TheFu said:**
> ssh uses 1 port.
Many routers can use port translation to convert the WAN port to an IP:port on the LAN.  On the LAN, I use the default 22/tcp port for ssh. On the WAN, I use some high, not standard port outside any likely-to-be-used ranges.

WAN:63099/tcp --> LAN:22/tcp

So, I can access the the LAN system via ssh and use my public domainname to access the same machine through the WAN port.  This way I can test the WAN access from inside the LAN. Not all routers will allow the WAN port to be accessed from inside. It is a security feature.

So I never need to know the actual port, my ~/.ssh/config file has different stanzas for each connection. Both documentation AND automatically fills in the port, userid, and other settings for the connection.  Different aliases for different sorts of connections through different ports. 

My troubleshooting steps: [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections) but starting with extra verbosity as SeijiSensei suggested is a good first step.  Looks like the sshd on the machine isn't being touched, so the router is the likely issue.

Yes I went through the steps, everything works except accessing from the internet. I have tried both with a DDNS domain name, and the direct ip address.

---

### Post by TheFu on 2019-06-20
Can you please show the EXACT command used with the output?  I'm not seeing the same stuff here, but I'm using 16.04.6 systems. Might help to have 3-4 -vvvv in the option.  Also, running the sshd in debug mode would probably help too.

---

### Post by Doug S on 2019-06-21
> **dillius2 said:**
> The IP Tables list output on the server is as follows:

```
iptables -L
```

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```That is not sufficient to know for sure that there are not any rules getting in the way. There probably aren't, but this is a weird one, so better check. Do:

```
sudo iptables-save -c
```

---

### Post by The Cog on 2019-06-21
The tcpdump trace in #5 clearly shows TCP SYN packets (the [s] flag) trying to start a connection. They are addressed to 10.0.0.219 port 21212, which judging by post #9 is the correct address.
I can only think of 2 reasons why there might be no reply to these requests. Either there is a firewall rule blocking the request or reply, or the host has no route (or a different route) for replying back to the caller.

For the firewall elimination, and also for checking the route, please post the result of these three commands (nft may just error, not a problem if it does):
```
sudo iptables-save
sudo nft list ruleset
ip route get 193.37.253.114

```

---

### Post by dillius2 on 2019-06-22
This once again seems to have just been a router being mysterious.

When I made my changes to Port Forwarding I even rebooted the router afterwards to try to force the change to take effect.

I ended up rebooting it again yesterday for another reason, and now it appears to be working fine.

---

### Post by TheFu on 2019-06-22
PLease mark this port SOLVED - thread tools button near top. Help out the community.

---

### Post by Doug S on 2019-06-22
> **dillius2 said:**
> This once again seems to have just been a router being mysterious.

When I made my changes to Port Forwarding I even rebooted the router afterwards to try to force the change to take effect.

I ended up rebooting it again yesterday for another reason, and now it appears to be working fine.As long as you realize that this explanation is inconsistent with your tcpdump data.

---

