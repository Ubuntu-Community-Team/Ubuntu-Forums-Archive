---
title: "IP forwarding against a wireless hotspot fails in one direction; ports are closed."
date: 2024-01-01
forum: Networking &amp; Wireless
---

### Post by 0cs935-bill on 2024-01-01
Ubuntu 22.04LTS fully patched.
A multihomed box (zima) has 3 networks:
enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.100  netmask 255.255.255.0  broadcast 192.168.1.255


enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 148.255.34.244  netmask 255.255.255.128  broadcast 148.255.34.255


wlp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.1  netmask 255.255.255.0  broadcast 192.168.2.255


Kernel IP routing table
[TABLE="width: 1000"]
[TR]
[TD]Destination[/TD]
[TD]Gateway[/TD]
[TD]Genmask[/TD]
[TD]Flags[/TD]
[TD]Metric[/TD]
[TD]Ref[/TD]
[TD]Use[/TD]
[TD]Iface[/TD]
[/TR]
[TR]
[TD]default[/TD]
[TD] _gateway[/TD]
[TD] 0.0.0.0[/TD]
[TD]UG[/TD]
[TD]101[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]enp3s0[/TD]
[/TR]
[TR]
[TD]148.255.34.128[/TD]
[TD] 0.0.0.0[/TD]
[TD]255.255.255.128[/TD]
[TD]U[/TD]
[TD]101[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]enp3so[/TD]
[/TR]
[TR]
[TD]link-local[/TD]
[TD] 0.0.0.0[/TD]
[TD]255.255.0.0[/TD]
[TD]U[/TD]
[TD]1000[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]enp2s0[/TD]
[/TR]
[TR]
[TD]192.168.1.0[/TD]
[TD] 0.0.0.0[/TD]
[TD]255.255.255.0[/TD]
[TD]U[/TD]
[TD]100[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]enp2s0[/TD]
[/TR]
[TR]
[TD]192.168.2.0[/TD]
[TD] 0.0.0.0[/TD]
[TD]255.255.255.0[/TD]
[TD]U[/TD]
[TD]600[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]wlp1s0[/TD]
[/TR]
[/TABLE]


wlp1s0 is set up as a hotspot with nothing but Android devices on that network and all are capable of Internet traffic.
cat /proc/sys/net/ipv4/ip_forward = 1
Firewall (ufw) is disabled for testing.
ping 192.168.2.4 # when executed on zima works as expected, showing that the destination is capable of replying to icmp packets.
==========
My personal box is 192.168.1.173
Firewall (ufw) is disabled for testing.
ping 192.168.2.4 # when executed from my box outputs:
From 192.168.1.100 icmp_seq=1 Destination Port Unreachable


If I then turn IP forwarding off on zima via:
sudo sysctl -w net.ipv4.ip_forward=0 # on zima
ping 192.168.2.4 # when executed from my box outputs nothing; the ping fails as expected.


sudo sysctl -w net.ipv4.ip_forward=1 # on zima


I installed Termux on the Android tablet at 192.168.2.4 so I could issue a ping from that tablet.
ping 192.168.1.173 # from 192.168.2.4 works!
ping 192.168.2.4   # from 192.168.1.173 fails with Destination Port Unreachable .


Why is it **Port** Unreachable? 
How is it possible it works in one direction only?


I installed openssh on 192.168.2.4 and zima can ssh in but my box can't.


nmap -sV -p 8022 192.168.2.4 # executed from zima yields:
Starting Nmap 7.80 ( [https://nmap.org](https://nmap.org) ) at 2024-01-01 08:37 CST
Nmap scan report for 192.168.2.4
Host is up (0.087s latency).


PORT     STATE SERVICE VERSION
8022/tcp open  ssh     OpenSSH 9.6 (protocol 2.0)


nmap -sV -p 8022 192.168.2.4 # executed from my box yields:
Starting Nmap 7.80 ( [https://nmap.org](https://nmap.org) ) at 2024-01-01 08:39 CST
Nmap scan report for 192.168.2.4
Host is up (0.00059s latency).


PORT     STATE  SERVICE   VERSION
8022/tcp closed oa-system


Again, the port is closed when I know it's open, but nmap says the host is up.


Can anyone shed some light on this?

---

### Post by SeijiSensei on 2024-01-01
Sounds like a routing problem to me. All the boxes need static routes for 192.168.1.0/24 and 192.168.2.0/24. My guess is that the ping packets are arriving, but the returns are getting lost.

I've had this experience; it's very frustrating.

---

### Post by 0cs935-bill on 2024-01-01
I can see the packet arriving on the wired interface on zima when I ping the wireless device from my wired box. It never shows up on a tcpdump -i wlp1s0 -envs 128 executed on zima, but a ping from the zima console to the same wireless IP does show up. That tells me the packet is not getting routed when it's originating on the wired network outside of zima.

What I don't understand is how routing is working when the wireless box pings my box. How is routing working in only one direction?

It's my understanding that I shouldn't have to do anything to make this function because IP_FORWARDING is supposed to take care of it in both directions. I've tried adding manual routes using the Settings GUI, nmcli, nmtui and nothing I've tried has changed anything.

---

### Post by #&amp;thj^% on 2024-01-01
> **0cs935-bill said:**
> I can see the packet arriving on the wired interface on zima when I ping the wireless device from my wired box. It never shows up on a tcpdump -i wlp1s0 -envs 128 executed on zima, but a ping from the zima console to the same wireless IP does show up. That tells me the packet is not getting routed when it's originating on the wired network outside of zima.

What I don't understand is how routing is working when the wireless box pings my box. How is routing working in only one direction?

It's my understanding that I shouldn't have to do anything to make this function because IP_FORWARDING is supposed to take care of it in both directions. I've tried adding manual routes using the Settings GUI, nmcli, nmtui and nothing I've tried has changed anything.
I'm going to add a hotspot, but for now with Two Nic's going:
```
sudo  tcpdump -i wlp4s0 -envs 128
tcpdump: listening on wlp4s0, link-type EN10MB (Ethernet), snapshot length 128 bytes
10:58:04.325592 c8:99:b2:18:3b:98 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Ethernet (len 6), IPv4 (len 4), Request who-has 192.168.1.152 (ff:ff:ff:ff:ff:ff) tell 192.168.1.1, length 28
10:58:05.056527 54:af:97:17:e3:c4 > ff:ff:ff:ff:ff:ff, ethertype Realtek protocols (0x8899), length 60: 54:af:97:17:e3:c4 > ff:ff:ff:ff:ff:ff, Realtek unknown type 0x25
10:58:05.363671 c8:99:b2:18:3b:98 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Ethernet (len 6), IPv4 (len 4), Request who-has 192.168.1.151 (ff:ff:ff:ff:ff:ff) tell 192.168.1.1, length 28
10:58:05.670918 c8:99:b2:18:3b:98 > 33:33:ff:ad:46:27, ethertype IPv6 (0x86dd), length 86: (flowlabel 0x09e07, hlim 255, next-header ICMPv6 (58) payload length: 32) fe80::ca99:b2ff:fe18:3b98 > ff02::1:ffad:4627: [icmp6 sum ok] ICMP6, neighbor solicitation, length 32, who has fe80::5b93:6ec2:99ad:4627
	  source link-address option (1), length 8 (1): c8:99:b2:18:3b:98
10:58:05.978129 54:af:97:17:e3:c4 > ff:ff:ff:ff:ff:ff, ethertype Realtek protocols (0x8899), length 60: 54:af:97:17:e3:c4 > ff:ff:ff:ff:ff:ff, Realtek unknown type 0x25
10:58:06.899878 54:af:97:17:e3:c4 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Ethernet (len 6), IPv4 (len 4), Request who-has 192.168.1.1 tell 192.168.1.151, length 46
10:58:06.899967 54:af:97:17:e3:c4 > ff:ff:ff:ff:ff:ff, ethertype Realtek protocols (0x8899), length 60: 54:af:97:17:e3:c4 > ff:ff:ff:ff:ff:ff, Realtek unknown type 0x25
10:58:07.207021 c8:99:b2:18:3b:98 > 33:33:ff:fa:4c:3c, ethertype IPv6 (0x86dd), length 86: (flowlabel 0x78760, hlim 255, next-header ICMPv6 (58) payload length: 32) fe80::ca99:b2ff:fe18:3b98 > ff02::1:fffa:4c3c: [icmp6 sum ok] ICMP6, neighbor solicitation, length 32, who has 2600:100e:a102:e9c9:36af:d47c:c0fa:4c3c
	  source link-address option (1), length 8 (1): c8:99:b2:18:3b:98
10:58:07.207117 e0:0a:f6:81:81:91 > c8:99:b2:18:3b:98, ethertype IPv6 (0x86dd), length 86: (hlim 255, next-header ICMPv6 (58) payload length: 32) 2600:100e:a102:e9c9:36af:d47c:c0fa:4c3c > fe80::ca99:b2ff:fe18:3b98: [icmp6 sum ok] ICMP6, neighbor advertisement, length 32, tgt is 2600:100e:a102:e9c9:36af:d47c:c0fa:4c3c, Flags [solicited, override]
	  destination link-address option (2), length 8 (1): e0:0a:f6:81:81:91
10:58:07.821523 54:af:97:17:e3:c4 > ff:ff:ff:ff:ff:ff, ethertype Realtek protocols (0x8899), length 60: 54:af:97:17:e3:c4 > ff:ff:ff:ff:ff:ff, Realtek unknown type 0x25
10:58:08.929657 e0:0a:f6:81:81:91 > c8:99:b2:18:3b:98, ethertype IPv6 (0x86dd), length 86: (hlim 255, next-header ICMPv6 (58) payload length: 32) fe80::2c7a:762b:d0a5:37ce > fe80::ca99:b2ff:fe18:3b98: [icmp6 sum ok] ICMP6, neighbor solicitation, length 32, who has fe80::ca99:b2ff:fe18:3b98
	  source link-address option (1), length 8 (1): e0:0a:f6:81:81:91
10:58:09.050092 c8:99:b2:18:3b:98 > e0:0a:f6:81:81:91, ethertype IPv6 (0x86dd), length 78: (hlim 255, next-header ICMPv6 (58) payload length: 24) fe80::ca99:b2ff:fe18:3b98 > fe80::2c7a:762b:d0a5:37ce: [icmp6 sum ok] ICMP6, neighbor advertisement, length 24, tgt is fe80::ca99:b2ff:fe18:3b98, Flags [router, solicited]
^C
12 packets captured
12 packets received by filter
0 packets dropped by kernel

``` 

This really dose smell like a routing problem and as SeijiSensei states these are very frustrating to solve.

---

### Post by 0cs935-bill on 2024-01-01
My networks have been up for years. I've never had a need to try to get at wireless boxes from the wired side since they were just Android units that offer nothing; they aren't servers of information, they just consume it and only from the Internet. Now, however, I've started a home automation project where I'm going to implement sensors and I have to be able to transfer information from them and send control demands to them. This issue has probably been there for years and I just never had the need to stumble across the problem.

---

### Post by Doug S on 2024-01-01
Is the box called "zema" a router? I.E. is it what provides internet access to one or both of the local sub-nets, 192.168.2.0/24 and 192.168.1.0/24? If yes, how is the router implemented? Is it with an iptables rule set or nftables or?

---

### Post by SeijiSensei on 2024-01-01
How do client devices get IP information? Via DHCP? What default router address do machines in 192.168.1.0/24 and 192.168.2.0/24 get from the DHCP server? A machine at 192.168.1.27 needs to know where to send packets for 192.168.2.47 and vice versa. Is zima also running isc-dhcp-server? Separate instances on each internally facing interface? 

Using your data in the first post, machines that get addresses in the 192.168.1.0/24 network should use 192.168.1.100 as their default router. Machines in 192.168.2.0/24 should use 192.168.2.1.

---

### Post by 0cs935-bill on 2024-01-01
The zima box has 3 networks with one being to the Internet. The other 2 are private, one wired and one wireless. Therefore, it's functioning as a router.

I don't know how NetworkManager implements the actual internals. Everything I did was through the Settings/Wi-Fi amd Settings/Network components of the Settings utility. These are simple networks that have no additional routes, no bridges, no nothing past IP address, Netmask, Gateway & DNS.

However, I was also suspecting some iptables sleight of hand so I ran an experiment.

I turned zima's and my ufw firewalls on. Rule set are as follows:
sudo ufw status #zima
Status: active
To                         Action      From
--                         ------      ----
80/tcp                     ALLOW       Anywhere                  
192.168.1.100 22/tcp on enp2s0 ALLOW       192.168.1.173             
80/tcp (v6)                ALLOW       Anywhere (v6)             

Zima has a web server and I'm allowed to ssh into that box.


sudo ufw status # my box
Status: active
To                         Action      From
--                         ------      ----
192.168.1.173 22/tcp on eno2 ALLOW       192.168.1.100             
192.168.1.173 873/tcp on eno2 ALLOW       192.168.1.100  
Zima runs a backup server that comes in via ssh and rsync.

I put my box, 192.168.1.173 into tcpdump mode via :
tcpdump 'icmp[icmptype] == icmp-echo or icmp[icmptype] == icmp-echoreply' -i eno2 -envs 128

I then had the wireless tablet, IP 192.168.2.4 ping my IP address.

What I got was the following:
192.168.1.100 > 192.168.1.173: ICMP echo request, id 15, seq 11, length 64
13:14:41.668884 0c:9d:92:85:e2:a2 > 00:e0:4c:68:0e:69, ethertype IPv4 (0x0800), length 98: (tos 0x0, ttl 64, id 51549, offset 0, flags [none], proto ICMP (1), length 84)
192.168.1.173 > 192.168.1.100: ICMP echo reply, id 15, seq 11, length 64

I'm getting traffic as though the wired NIC in zima is the tablet; no mention of the tablet's IP address.

So, I dumped zima's iptables:
-P INPUT DROP
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-N ufw-after-forward
-N ufw-after-input
-N ufw-after-logging-forward
-N ufw-after-logging-input
-N ufw-after-logging-output
-N ufw-after-output
-N ufw-before-forward
-N ufw-before-input
-N ufw-before-logging-forward
-N ufw-before-logging-input
-N ufw-before-logging-output
-N ufw-before-output
-N ufw-logging-allow
-N ufw-logging-deny
-N ufw-not-local
-N ufw-reject-forward
-N ufw-reject-input
-N ufw-reject-output
-N ufw-skip-to-policy-forward
-N ufw-skip-to-policy-input
-N ufw-skip-to-policy-output
-N ufw-track-forward
-N ufw-track-input
-N ufw-track-output
-N ufw-user-forward
-N ufw-user-input
-N ufw-user-limit
-N ufw-user-limit-accept
-N ufw-user-logging-forward
-N ufw-user-logging-input
-N ufw-user-logging-output
-N ufw-user-output
-A INPUT -j ufw-before-logging-input
-A INPUT -j ufw-before-input
-A INPUT -j ufw-after-input
-A INPUT -j ufw-after-logging-input
-A INPUT -j ufw-reject-input
-A INPUT -j ufw-track-input
-A FORWARD -j ufw-before-logging-forward
-A FORWARD -j ufw-before-forward
-A FORWARD -j ufw-after-forward
-A FORWARD -j ufw-after-logging-forward
-A FORWARD -j ufw-reject-forward
-A FORWARD -j ufw-track-forward
-A OUTPUT -j ufw-before-logging-output
-A OUTPUT -j ufw-before-output
-A OUTPUT -j ufw-after-output
-A OUTPUT -j ufw-after-logging-output
-A OUTPUT -j ufw-reject-output
-A OUTPUT -j ufw-track-output
-A ufw-after-input -p udp -m udp --dport 137 -j ufw-skip-to-policy-input
-A ufw-after-input -p udp -m udp --dport 138 -j ufw-skip-to-policy-input
-A ufw-after-input -p tcp -m tcp --dport 139 -j ufw-skip-to-policy-input
-A ufw-after-input -p tcp -m tcp --dport 445 -j ufw-skip-to-policy-input
-A ufw-after-input -p udp -m udp --dport 67 -j ufw-skip-to-policy-input
-A ufw-after-input -p udp -m udp --dport 68 -j ufw-skip-to-policy-input
-A ufw-after-input -m addrtype --dst-type BROADCAST -j ufw-skip-to-policy-input
-A ufw-after-logging-input -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK] "
-A ufw-before-forward -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-forward -p icmp -m icmp --icmp-type 3 -j ACCEPT
-A ufw-before-forward -p icmp -m icmp --icmp-type 11 -j ACCEPT
-A ufw-before-forward -p icmp -m icmp --icmp-type 12 -j ACCEPT
-A ufw-before-forward -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A ufw-before-forward -j ufw-user-forward
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-input -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-input -m conntrack --ctstate INVALID -j ufw-logging-deny
-A ufw-before-input -m conntrack --ctstate INVALID -j DROP
-A ufw-before-input -p icmp -m icmp --icmp-type 3 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 11 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 12 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A ufw-before-input -p udp -m udp --sport 67 --dport 68 -j ACCEPT
-A ufw-before-input -j ufw-not-local
-A ufw-before-input -d 224.0.0.251/32 -p udp -m udp --dport 5353 -j ACCEPT
-A ufw-before-input -d 239.255.255.250/32 -p udp -m udp --dport 1900 -j ACCEPT
-A ufw-before-input -j ufw-user-input
-A ufw-before-output -o lo -j ACCEPT
-A ufw-before-output -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -j ufw-user-output
-A ufw-logging-allow -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW ALLOW] "
-A ufw-logging-deny -m conntrack --ctstate INVALID -m limit --limit 3/min --limit-burst 10 -j RETURN
-A ufw-logging-deny -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK] "
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny
-A ufw-not-local -j DROP
-A ufw-skip-to-policy-forward -j ACCEPT
-A ufw-skip-to-policy-input -j DROP
-A ufw-skip-to-policy-output -j ACCEPT
-A ufw-track-forward -p tcp -m conntrack --ctstate NEW -j ACCEPT
-A ufw-track-forward -p udp -m conntrack --ctstate NEW -j ACCEPT
-A ufw-track-output -p tcp -m conntrack --ctstate NEW -j ACCEPT
-A ufw-track-output -p udp -m conntrack --ctstate NEW -j ACCEPT
-A ufw-user-input -p tcp -m tcp --dport 80 -j ACCEPT
-A ufw-user-input -s 192.168.1.173/32 -d 192.168.1.100/32 -i enp2s0 -p tcp -m tcp --dport 22 -j ACCEPT
-A ufw-user-limit -m limit --limit 3/min -j LOG --log-prefix "[UFW LIMIT BLOCK] "
-A ufw-user-limit -j REJECT --reject-with icmp-port-unreachable
-A ufw-user-limit-accept -j ACCEPT

I don't see anything suspicious.

---

### Post by 0cs935-bill on 2024-01-01
Wireless devices get DHCP, but static assignments via their MAC addresses. The window for the number of DHCP leases is also only the number of wireless boxes I have.

Wired boxes are all static and each wired box gets an /etc/hosts file that defines IP to hostname. 
Your assumption about gateways is what I have.  
[COLOR=#000000]192.168.1.0/24 network -> 192.168.1.100
192.168.2.0/24 network -> 192.168.2.1

[/COLOR]

---

### Post by #&amp;thj^% on 2024-01-01
My return is different with a hotspot:
Fist check:
```
iw list | grep AP
	Device supports AP-side u-APSD.
		 * AP
		 * AP/VLAN
		HE Iftypes: AP
				Rx HE MU PPDU from Non-AP STA
		EHT Iftypes: AP
		HE Iftypes: AP
				Rx HE MU PPDU from Non-AP STA
		EHT Iftypes: AP
		 * AP/VLAN
		 * #{ managed } <= 1, #{ AP, P2P-client, P2P-GO } <= 1,
	Driver supports full state transitions for AP/GO clients
		 * AP: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
		 * AP/VLAN: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
		 * AP: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
		 * AP/VLAN: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0

```
Next the tdpdump:
```
sudo  tcpdump -i wlp4s0 -envs 128
tcpdump: listening on wlp4s0, link-type EN10MB (Ethernet), snapshot length 128 bytes

13:12:10.315468 e0:0a:f6:81:81:91 > 33:33:00:00:00:02, ethertype IPv6 (0x86dd), length 70: (hlim 255, next-header ICMPv6 (58) payload length: 16) fe80::e20a:f6ff:fe81:8191 > ff02::2: [icmp6 sum ok] ICMP6, router solicitation, length 16
	  source link-address option (1), length 8 (1): e0:0a:f6:81:81:91
^C
1 packet captured
1 packet received by filter
0 packets dropped by kernel

```

---

### Post by Doug S on 2024-01-01
> **0cs935-bill said:**
> I then had the wireless tablet, IP 192.168.2.4 ping my IP address.

What I got was the following:
192.168.1.100 > 192.168.1.173: ICMP echo request, id 15, seq 11, length 64
13:14:41.668884 0c:9d:92:85:e2:a2 > 00:e0:4c:68:0e:69, ethertype IPv4 (0x0800), length 98: (tos 0x0, ttl 64, id 51549, offset 0, flags [none], proto ICMP (1), length 84)
192.168.1.173 > 192.168.1.100: ICMP echo reply, id 15, seq 11, length 64

 O.K. so the 192.168.2.0/24 network is going to the 192.168.1.0/24 network via NAT (Network Address Translation). So now things make at little more sense.

Could you post the entire iptabes rule set (although I really hate trying to follow UFW generated iptables rule sets)? I'd like to see the outputs for "sudo iptables -xvnL" and "sudo iptables -t nat -xvnL" inside code tags.

---

### Post by 0cs935-bill on 2024-01-01
I was under the impression that translation was only used on the outbound Internet traffic so that an Internet site can reply to my public IP and internally it would get translate to the private non routable IP that originated the request. I had no idea translation was used on internal traffic.

The xvnL output:
```

Chain INPUT (policy DROP 2909 packets, 139666 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
   58240 644218258 ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   58240 644218258 ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   12944   829790 ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   10699   522285 ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   10699   522285 ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   10699   522285 ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain FORWARD (policy ACCEPT 125 packets, 7577 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
 5733049 5552077667 ufw-before-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 5733049 5552077667 ufw-before-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   32711 12744695 ufw-after-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   32711 12744695 ufw-after-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   32711 12744695 ufw-reject-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   32711 12744695 ufw-track-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain OUTPUT (policy ACCEPT 7 packets, 428 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
   44142  5164991 ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   44142  5164991 ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
     531    48176 ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
     531    48176 ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
     531    48176 ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
     531    48176 ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-after-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         


Chain ufw-after-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:137
       0        0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:138
       3      156 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:139
      26     1324 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:445
       3      988 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:67
       0        0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:68
     228    38155 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST


Chain ufw-after-logging-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         


Chain ufw-after-logging-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
    1115    50919 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "


Chain ufw-after-logging-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         


Chain ufw-after-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         


Chain ufw-before-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
 3160611 3001227693 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
       5      420 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
   15905  6839285 ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-before-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
     124    10487 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    1733   449283 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
      17      827 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
      17      827 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
    6551   277119 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp spt:67 dpt:68
    3491   205401 ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
     151    15021 ACCEPT     udp  --  *      *       0.0.0.0/0            224.0.0.251          udp dpt:5353
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            239.255.255.250      udp dpt:1900
    3340   190380 ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-before-logging-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         


Chain ufw-before-logging-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         


Chain ufw-before-logging-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         


Chain ufw-before-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
     124    10487 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    8831   586137 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
      99     9754 ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-logging-allow (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW ALLOW] "


Chain ufw-logging-deny (2 references)
    pkts      bytes target     prot opt in     out     source               destination         
      17      827 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID limit: avg 3/min burst 10
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "


Chain ufw-not-local (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
    3112   152225 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type LOCAL
     151    15021 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type MULTICAST
     228    38155 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST
       0        0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-reject-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         


Chain ufw-reject-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         


Chain ufw-reject-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         


Chain ufw-skip-to-policy-forward (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-skip-to-policy-input (7 references)
    pkts      bytes target     prot opt in     out     source               destination         
     260    40623 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-skip-to-policy-output (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-track-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
    2264   138367 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW
   13516  6693341 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW


Chain ufw-track-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         


Chain ufw-track-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       3      180 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW
      89     9146 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW


Chain ufw-user-forward (1 references)
    pkts      bytes target     prot opt in     out     source               destination         


Chain ufw-user-input (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
     169     9971 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80
       2      120 ACCEPT     tcp  --  enp2s0 *       192.168.1.173        192.168.1.100        tcp dpt:22


Chain ufw-user-limit (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 5 LOG flags 0 level 4 prefix "[UFW LIMIT BLOCK] "
       0        0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable


Chain ufw-user-limit-accept (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-user-logging-forward (0 references)
    pkts      bytes target     prot opt in     out     source               destination         


Chain ufw-user-logging-input (0 references)
    pkts      bytes target     prot opt in     out     source               destination         


Chain ufw-user-logging-output (0 references)
    pkts      bytes target     prot opt in     out     source               destination         


Chain ufw-user-output (1 references)
    pkts      bytes target     prot opt in     out     source               destination   

```      

The -t nat xvnL output:
```

Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


Chain POSTROUTING (policy ACCEPT 133 packets, 12352 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
   20011  9229825 MASQUERADE  all  --  *      enp3s0  192.168.1.0/24       0.0.0.0/0           
       0        0 MASQUERADE  all  --  *      enp3s0  192.168.1.0/24       0.0.0.0/0           
       0        0 MASQUERADE  all  --  *      enp3s0  192.168.1.0/24       0.0.0.0/0           
       0        0 MASQUERADE  all  --  *      enp3s0  192.168.1.0/24       0.0.0.0/0           

```

---

### Post by Doug S on 2024-01-01
> **0cs935-bill said:**
> I was under the impression that translation was only used on the outbound Internet traffic so that an Internet site can reply to my public IP and internally it would get translate to the private non routable IP that originated the request. I had no idea translation was used on internal traffic.Yes, that seems to be what the iptables rules say also, at least for the 192.168.1.0/24 LAN. The 192.168.2.0/24 LAN doesn't seem to have any NAT anywhere.
I must be missing something. If it were me, I would be adding a lot of logging rules to the iptables rule set to assist with debugging, and also watching the packet counters while doing the pings in an attempt to trace the paths traversed by the packets. I do not see specific icmp type 0 ACCEPT rules anywhere.
I'll keep looking.

---

### Post by 0cs935-bill on 2024-01-01
I do appreciate your attention to this anomaly. The last time I really understood iptables was about 20 years ago when I built a rudimentary firewall script in BASH. I haven't looked at it since. 

I need to do some more testing on a non wireless network to better understand what to expect when then looking at the wireless facsimile. When I saw the reply packets with no indication that they came from my wireless tablet but appeared to come from zima's wired NIC, that floored me. My first thought was is there some kind of bridging going on? I was always under the impression that every hop somehow encapsulated the traffic along a path and eventually the onion skins would be reversed to reveal the original payload. I've got a few machines lying around and can cobble together a reasonable test setup to better understand what's happening.

Here I was anxious to get a new box up and running with KVM installed, Home Assistant as VM, and then this networking issue shut everything down awaiting a resolution. One step forward two steps back.

---

### Post by SeijiSensei on 2024-01-02
Masquerading can screw up routing if you're not careful. You need IP tables rules for internal traffic. Something like
```

iptables -A INPUT -s 192.168.1.0/24 -d 192.168.2.0/24 -j ACCEPT
iptables -A INPUT -s 192.168.2.0/24 -d 192.168.1.0/24 -j ACCEPT

```
These rules should be near the top of the ruleset.

Masquerading rules by interface may also help.

```

iptables -i enp2s0 -o enp3s0 -j MASQUERADE
iptables -i wlp1s0 -o enp3so -j MASQUERADE

```
These rules explicitly apply masquerading only to traffic from the internal networks to the Internet. You most definitely do not want masquerading of local traffic.

---

### Post by Doug S on 2024-01-02
I am still not understanding why your ping from 192.168.2.4 seems to have gone through NAT (Network Address Translation) on it way to 192.168.1.173.

I also do not understand the Nmap latency times:
 
> **0cs935-bill said:**
> 
nmap -sV -p 8022 192.168.2.4 # executed from zima yields:
Starting Nmap 7.80 ( [https://nmap.org](https://nmap.org) ) at 2024-01-01 08:37 CST
Nmap scan report for 192.168.2.4
Host is up ([COLOR="#0000CD"]0.087s latency[/COLOR]).


PORT     STATE SERVICE VERSION
8022/tcp open  ssh     OpenSSH 9.6 (protocol 2.0)


nmap -sV -p 8022 192.168.2.4 # executed from my box yields:
Starting Nmap 7.80 ( [https://nmap.org](https://nmap.org) ) at 2024-01-01 08:39 CST
Nmap scan report for 192.168.2.4
Host is up ([COLOR="#0000CD"]0.00059s latency[/COLOR]).


PORT     STATE  SERVICE   VERSION
8022/tcp closed oa-system
as I would have expected the latency time from your box (192.168.1.173) to be greater than from zima.

It shouldn't make any difference but: I always specify the NIC when doing NAT; For your application I would use SNAT instead of MASQUERADE.
So, I am saying instead of this:
```
Chain POSTROUTING (policy ACCEPT 133 packets, 12352 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
   20011  9229825 MASQUERADE  all  --  *      enp3s0  192.168.1.0/24       0.0.0.0/0
```
something like this:
```

Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
      0          0     SNAT       all  --  *     enp3s0  0.0.0.0/0            0.0.0.0/0            to:148.255.34.128

```

EDIT 1: I was writing this post when Seiji posted some good suggestions.
EDIT 2: the SNAT rule in source syntax:

```
sudo iptables -t nat -A POSTROUTING -o enp3so -j SNAT --to 148.255.34.128
```

---

### Post by SeijiSensei on 2024-01-02
> **Doug S said:**
> It shouldn't make any difference but: I always specify the NIC when doing NAT; For your application I would use SNAT instead of MASQUERADE.
In his case, with a multi-homed router, the interface matters a great deal. And, yes, I prefer SNAT to MASQUERADE. As I wrote above, he needs to specify the interfaces involved so that only outbound traffic is NATted.

Using your suggestions, I'd make sure he has
```
iptables -A POSTROUTING -o enp3so -j SNAT --to 148.255.34.128
```

---

### Post by 0cs935-bill on 2024-01-02
I'm in the process of setting up a new box from scratch as a test case where I can experiment with traffic and setting up the wireless interface. I want to see if I can reproduce the same situation as on my current zima box.

As far as iptables rules, I've checked the logs and nothing has stopped the icmp packets from traversing the system. The suggested two rules to allow 1.0 & 2.0 to allow all traffic between them would be fixing something that's not broken, as I can't find any denied packets.

I'll hold off on the other suggestions on zima because I want its idiosyncratic behavior left alone so I can compare the new box with it. If I see the new box do the same thing, then there's a bug in setup somewhere. If not, then the comparison should zero in on what's broken on zima.

---

### Post by Doug S on 2024-01-02
O.K., but please eventually report back your findings.We would appreciate it very much.

By the way, in your iptables rules posting, there are a great many packets that were DROPped without a log entry.

---

### Post by 0cs935-bill on 2024-01-02
Set up a box 'hostname=ha' with a fresh install of Ubuntu 22.04LTS and fully patched it. My internet connection on the island is a whole 1 Mbps so patching takes a long time.
Wired NIC = 192.168.1.101 and wireless hotspot was set up using the script below:
```

#!/bin/bash


declare -r ifname='wlp3s0'
declare -r conname='wireless'
declare -r ssid='haap'
declare -r ipv4addr='192.168.3.1/24'
declare -r password='XXXXXXX'


nmcli connection add type wifi ifname "${ifname}" con-name "${conname}" ssid "${ssid}" autoconnect yes
nmcli connection modify "${conname}" 802-11-wireless.mode ap 802-11-wireless.band bg ipv4.method shared ipv6.method disabled ipv4.addresses "${ipv4addr}"
nmcli connection modify "${conname}" wifi-sec.key-mgmt wpa-psk wifi-sec.psk "${password}"
nmcli connection up "${conname}"
nmcli connection modify "${conname}" connection.autoconnect yes
nmcli con show --active

```

I wrote the script so I could execute one line at a time by commenting things and see what that did to /etc/NetworkManager/system-connections/wireless.nmconnection . It turned out almost identical to the wireless setup that started this whole adventure. It also provides repeatability which is also what I was after.


Installed isc-dhcp-server and configured a minimal /etc/dhcp/dhcpd.conf:
```

default-lease-time 28800;
max-lease-time 86400;
authoritative;
subnet 192.168.3.0 netmask 255.255.255.0 {
option routers 192.168.3.1;
option domain-name-servers 8.8.8.8, 8.8.4.4;
option domain-name "private.xyz";
}


host BillTablet {
hardware ethernet 24:CC:13:4F:F1:B9;
fixed-address 192.168.3.4;
}

```


Checked /proc/sys/net/ipv4/ip_forward and it was already on (1).


I never started ufw.
iptables -S shows :
-P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT


Fixed my person box @ 192.168.1.173 to gateway to the new box @ 192.168.1.101


Got my tablet to connect to the new wireless network and ifconfig shows it to be at 192.168.3.4


Opened terminals on ha to tcpdump both networks on ha simultaneously via 
tcpdump 'icmp[icmptype] == icmp-echo or icmp[icmptype] == icmp-echoreply' -i eno2 -envs 128 -i eno1
tcpdump 'icmp[icmptype] == icmp-echo or icmp[icmptype] == icmp-echoreply' -i eno2 -envs 128 -i wlp3s0


From my box, issued
ping -c 1 192.168.3.4
Only the wired network shows traffic for 192.168.1.173 > 192.168.3.4 with no reply
the wireless network shows no traffic.
My ping fails with Destination Port Unreachable


From the Android tablet, via Termux console, issued
ping -c 1 192.168.1.173
wireless shows 192.168.3.4 > 192.168.1.173
reply of 192.168.1.173 > 192.168.3.4
wired shows 192.168.1.101 > 192.168.1.173
reply of 192.168.1.173 > 192.168.1.101


Ping works in one direction but not the other.

Journalctl show nothing. I can't find any log of where traffic was dropped.

---

### Post by Doug S on 2024-01-03
Well, I am out of ideas. I am a server person and do not use network manager, so I don't know if it is contributing to your issues or not.

At my home, I only have one LAN, with the wireless devices on the same sub-net as the wired devices. I do not have any wireless NIC in my main linux server/router/gateway/firewall/dhcp-server. Wireless devices communicate with the wired part of the LAN via a store bought wireless router configured as a switch.

---

### Post by 0cs935-bill on 2024-01-04
Resumed testing this morning.
Set up a constant 
ping 192.168.3.4
on my box and discovered this in /var/log/syslog on the ha box. The rtw89_8852be is the Realtek wireless adapter on the mobo.   
Notice the time between the first and second message. It took a while for this to appear after I started traffic to the wireless adapter. Further, notice the 960s retry spec. It might as well be never.
```

Jan  4 11:13:11 ha ubuntu-report[1755]: level=error msg="data were not delivered successfully to metrics server, retrying in 960s"
Jan  4 11:14:39 ha kernel: [ 1101.319165] rtw89_8852be 0000:03:00.0: FW status = 0xbb001100
Jan  4 11:14:39 ha kernel: [ 1101.319181] rtw89_8852be 0000:03:00.0: FW BADADDR = 0x99
Jan  4 11:14:39 ha kernel: [ 1101.319189] rtw89_8852be 0000:03:00.0: FW EPC/RA = 0x0
Jan  4 11:14:39 ha kernel: [ 1101.319196] rtw89_8852be 0000:03:00.0: FW MISC = 0xb8900635
Jan  4 11:14:39 ha kernel: [ 1101.319203] rtw89_8852be 0000:03:00.0: R_AX_HALT_C2H = 0x1000
Jan  4 11:14:39 ha kernel: [ 1101.319209] rtw89_8852be 0000:03:00.0: R_AX_SER_DBG_INFO = 0x1000000
Jan  4 11:14:39 ha kernel: [ 1101.319220] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a033
Jan  4 11:14:39 ha kernel: [ 1101.319244] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a037
Jan  4 11:14:39 ha kernel: [ 1101.319264] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a0d7
Jan  4 11:14:39 ha kernel: [ 1101.319283] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a01d
Jan  4 11:14:39 ha kernel: [ 1101.319302] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a0ff
Jan  4 11:14:39 ha kernel: [ 1101.319321] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a025
Jan  4 11:14:39 ha kernel: [ 1101.319340] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb8989fff
Jan  4 11:14:39 ha kernel: [ 1101.319359] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a037
Jan  4 11:14:39 ha kernel: [ 1101.319378] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a01f
Jan  4 11:14:39 ha kernel: [ 1101.319397] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a0ff
Jan  4 11:14:39 ha kernel: [ 1101.319416] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a027
Jan  4 11:14:39 ha kernel: [ 1101.319435] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb8989ffd
Jan  4 11:14:39 ha kernel: [ 1101.319454] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a035
Jan  4 11:14:39 ha kernel: [ 1101.319472] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a0ff
Jan  4 11:14:39 ha kernel: [ 1101.319491] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a025
Jan  4 11:14:39 ha kernel: [ 1101.319508] rtw89_8852be 0000:03:00.0: --->
Jan  4 11:14:39 ha kernel: [ 1101.319508] err=0x1000
Jan  4 11:14:39 ha kernel: [ 1101.319515] rtw89_8852be 0000:03:00.0: R_AX_SER_DBG_INFO =0x01000000
Jan  4 11:14:39 ha kernel: [ 1101.319524] rtw89_8852be 0000:03:00.0: R_AX_DMAC_ERR_ISR=0x00000040
Jan  4 11:14:39 ha kernel: [ 1101.319531] rtw89_8852be 0000:03:00.0: R_AX_DMAC_ERR_IMR=0x00000000
Jan  4 11:14:39 ha kernel: [ 1101.319538] rtw89_8852be 0000:03:00.0: R_AX_WDE_ERR_FLAG_CFG=0x00000000
Jan  4 11:14:39 ha kernel: [ 1101.319544] rtw89_8852be 0000:03:00.0: R_AX_PLE_ERR_FLAG_CFG=0x83190000
Jan  4 11:14:39 ha kernel: [ 1101.319552] rtw89_8852be 0000:03:00.0: R_AX_WDE_ERR_IMR=0xffffffff
Jan  4 11:14:39 ha kernel: [ 1101.319558] rtw89_8852be 0000:03:00.0: R_AX_WDE_ERR_ISR=0x00000000
Jan  4 11:14:39 ha kernel: [ 1101.319565] rtw89_8852be 0000:03:00.0: R_AX_PLE_ERR_IMR=0xffffffdf
Jan  4 11:14:39 ha kernel: [ 1101.319571] rtw89_8852be 0000:03:00.0: R_AX_PLE_ERR_FLAG_ISR=0x02000000
Jan  4 11:14:39 ha kernel: [ 1101.319578] rtw89_8852be 0000:03:00.0: R_AX_WD_CPUQ_OP_0=0x00000000
Jan  4 11:14:39 ha kernel: [ 1101.319584] rtw89_8852be 0000:03:00.0: R_AX_WD_CPUQ_OP_1=0x00d00000
Jan  4 11:14:39 ha kernel: [ 1101.319591] rtw89_8852be 0000:03:00.0: R_AX_WD_CPUQ_OP_2=0x00000000
Jan  4 11:14:39 ha kernel: [ 1101.319598] rtw89_8852be 0000:03:00.0: R_AX_WD_CPUQ_OP_STATUS=0x80000002
Jan  4 11:14:39 ha kernel: [ 1101.319605] rtw89_8852be 0000:03:00.0: R_AX_PL_CPUQ_OP_0=0x00000000
Jan  4 11:14:39 ha kernel: [ 1101.319611] rtw89_8852be 0000:03:00.0: R_AX_PL_CPUQ_OP_1=0x00000000
Jan  4 11:14:39 ha kernel: [ 1101.319618] rtw89_8852be 0000:03:00.0: R_AX_PL_CPUQ_OP_2=0x00000000
Jan  4 11:14:39 ha kernel: [ 1101.319624] rtw89_8852be 0000:03:00.0: R_AX_PL_CPUQ_OP_STATUS=0x00000000
Jan  4 11:14:39 ha kernel: [ 1101.319631] rtw89_8852be 0000:03:00.0: R_AX_RXDMA_PKT_INFO_0=0x80008168
Jan  4 11:14:39 ha kernel: [ 1101.319638] rtw89_8852be 0000:03:00.0: R_AX_RXDMA_PKT_INFO_1=0x80008000
Jan  4 11:14:39 ha kernel: [ 1101.319644] rtw89_8852be 0000:03:00.0: R_AX_RXDMA_PKT_INFO_2=0x8127812a
Jan  4 11:14:39 ha kernel: [ 1101.319655] rtw89_8852be 0000:03:00.0: R_AX_CMAC_ERR_ISR [0]=0x00000000
Jan  4 11:14:39 ha kernel: [ 1101.319663] rtw89_8852be 0000:03:00.0: R_AX_CMAC_FUNC_EN [0]=0xf000803f
Jan  4 11:14:39 ha kernel: [ 1101.319670] rtw89_8852be 0000:03:00.0: R_AX_CK_EN [0]=0xffffffff
Jan  4 11:14:39 ha kernel: [ 1101.319677] rtw89_8852be 0000:03:00.0: R_AX_CMAC_ERR_IMR [0]=0x00000000
Jan  4 11:14:39 ha kernel: [ 1101.319684] rtw89_8852be 0000:03:00.0: R_AX_RPQ_RXBD_IDX =0x006d006d
Jan  4 11:14:39 ha kernel: [ 1101.319690] rtw89_8852be 0000:03:00.0: R_AX_DBG_ERR_FLAG=0x00000000
Jan  4 11:14:39 ha kernel: [ 1101.319697] rtw89_8852be 0000:03:00.0: R_AX_LBC_WATCHDOG=0x00000081
Jan  4 11:14:39 ha kernel: [ 1101.319702] rtw89_8852be 0000:03:00.0: <---
Jan  4 11:14:39 ha kernel: [ 1101.319706] rtw89_8852be 0000:03:00.0: SER catches error: 0x1000
Jan  4 11:14:39 ha kernel: [ 1101.319955] rtw89_8852be 0000:03:00.0: FW status = 0xbb001100
Jan  4 11:14:39 ha kernel: [ 1101.319961] rtw89_8852be 0000:03:00.0: FW BADADDR = 0x99
Jan  4 11:14:39 ha kernel: [ 1101.319965] rtw89_8852be 0000:03:00.0: FW EPC/RA = 0x0
Jan  4 11:14:39 ha kernel: [ 1101.319970] rtw89_8852be 0000:03:00.0: FW MISC = 0xb8900635
Jan  4 11:14:39 ha kernel: [ 1101.319974] rtw89_8852be 0000:03:00.0: R_AX_HALT_C2H = 0x1001
Jan  4 11:14:39 ha kernel: [ 1101.319978] rtw89_8852be 0000:03:00.0: R_AX_SER_DBG_INFO = 0x1000000
Jan  4 11:14:39 ha kernel: [ 1101.319986] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a0f5
Jan  4 11:14:39 ha kernel: [ 1101.320002] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a013
Jan  4 11:14:39 ha kernel: [ 1101.320018] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a0dd
Jan  4 11:14:39 ha kernel: [ 1101.320032] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a0f7
Jan  4 11:14:39 ha kernel: [ 1101.320047] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a0fd
Jan  4 11:14:39 ha kernel: [ 1101.320061] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a0e7
Jan  4 11:14:39 ha kernel: [ 1101.320076] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a0dd
Jan  4 11:14:39 ha kernel: [ 1101.320091] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a0d5
Jan  4 11:14:39 ha kernel: [ 1101.320107] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a01f
Jan  4 11:14:39 ha kernel: [ 1101.320122] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a0f7
Jan  4 11:14:39 ha kernel: [ 1101.320136] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a0d9
Jan  4 11:14:39 ha kernel: [ 1101.320152] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a009
Jan  4 11:14:39 ha kernel: [ 1101.320167] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a005
Jan  4 11:14:39 ha kernel: [ 1101.320182] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a025
Jan  4 11:14:39 ha kernel: [ 1101.320198] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb898a023
Jan  4 11:14:39 ha kernel: [ 1101.320213] rtw89_8852be 0000:03:00.0: SER catches error: 0x1001
Jan  4 11:14:39 ha kernel: [ 1101.320347] rtw89_8852be 0000:03:00.0: FW status = 0xbb008100
Jan  4 11:14:39 ha kernel: [ 1101.320353] rtw89_8852be 0000:03:00.0: FW BADADDR = 0x99
Jan  4 11:14:39 ha kernel: [ 1101.320357] rtw89_8852be 0000:03:00.0: FW EPC/RA = 0x0
Jan  4 11:14:39 ha kernel: [ 1101.320361] rtw89_8852be 0000:03:00.0: FW MISC = 0xb898828b
Jan  4 11:14:39 ha kernel: [ 1101.320365] rtw89_8852be 0000:03:00.0: R_AX_HALT_C2H = 0x1002
Jan  4 11:14:39 ha kernel: [ 1101.320368] rtw89_8852be 0000:03:00.0: R_AX_SER_DBG_INFO = 0xf1000000
Jan  4 11:14:39 ha kernel: [ 1101.320375] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb89a8df3
Jan  4 11:14:39 ha kernel: [ 1101.320390] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb8935f3d
Jan  4 11:14:39 ha kernel: [ 1101.320405] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb8935dcd
Jan  4 11:14:39 ha kernel: [ 1101.320420] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb89a8dfb
Jan  4 11:14:39 ha kernel: [ 1101.320434] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb8935f0f
Jan  4 11:14:39 ha kernel: [ 1101.320449] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb89acab7
Jan  4 11:14:39 ha kernel: [ 1101.320464] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb89a8dc3
Jan  4 11:14:39 ha kernel: [ 1101.320478] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb8935ea7
Jan  4 11:14:39 ha kernel: [ 1101.320493] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb897d1ff
Jan  4 11:14:39 ha kernel: [ 1101.320508] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb892768f
Jan  4 11:14:39 ha kernel: [ 1101.320522] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb89a3c39
Jan  4 11:14:39 ha kernel: [ 1101.320537] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb897d14f
Jan  4 11:14:39 ha kernel: [ 1101.320552] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb892768f
Jan  4 11:14:39 ha kernel: [ 1101.320567] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb89a3807
Jan  4 11:14:39 ha kernel: [ 1101.320581] rtw89_8852be 0000:03:00.0: [ERR]fw PC = 0xb897d13f
Jan  4 11:14:39 ha kernel: [ 1101.320594] rtw89_8852be 0000:03:00.0: SER catches error: 0x1002
Jan  4 11:14:40 ha kernel: [ 1101.389621] rtw89_8852be 0000:03:00.0: c2h class 1 func 3 not support

```

Does this look like there's a bug in the driver for the hardware?

---

### Post by #&amp;thj^% on 2024-01-04
> **0cs935-bill said:**
> 

Does this look like there's a bug in the driver for the hardware?

possibly, but what dose this show you:
```
modinfo rtw89_8852be
```
Along with:
```
lsmod | grep -i 8852

```

---

### Post by 0cs935-bill on 2024-01-04
I'm going to do some testing on the original zima box to see if I can find something similar. The length of time this took to show up in syslog meant that when I was looking, it wasn't there yet. It never occurred to me to take a delay into consideration.

[COLOR=#FFFFFF][FONT=ui-monospace]modinfo rtw89_8852be
[/FONT][/COLOR]
```

filename:       /lib/modules/6.2.0-39-generic/kernel/drivers/net/wireless/realtek/rtw89/rtw89_8852be.ko
license:        Dual BSD/GPL
description:    Realtek 802.11ax wireless 8852BE driver
author:         Realtek Corporation
srcversion:     87FC3D1B28540DD0400027C
alias:          pci:v000010ECd0000B85Bsv*sd*bc*sc*i*
alias:          pci:v000010ECd0000B852sv*sd*bc*sc*i*
depends:        rtw89_pci,rtw89_8852b
retpoline:      Y
intree:         Y
name:           rtw89_8852be
vermagic:       6.2.0-39-generic SMP preempt mod_unload modversions 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        36:0C:63:63:C0:63:25:78:65:13:0F:0C:CD:7D:C3:5E:97:5F:55:40
sig_hashalgo:   sha512
signature:      05:58:25:BA:87:3D:AB:6D:60:B3:62:10:5E:07:C6:29:06:D7:B2:5A:
		93:38:8F:F4:21:C8:DF:71:F5:95:7D:AB:4E:C2:4B:30:60:D2:DB:B6:
		53:BF:7B:68:36:6B:FA:AA:92:42:C3:97:E5:04:57:80:87:A2:49:3A:
		EE:0C:1A:BD:F7:83:D8:5E:47:CC:75:37:B0:4F:62:59:64:E5:2E:A0:
		A7:81:EC:44:56:20:A4:AD:C8:10:C3:14:3C:9D:C7:43:09:A8:AD:27:
		A2:5B:69:89:A1:3C:D8:41:6E:92:3B:E4:F8:A1:D6:4C:DC:EC:06:0F:
		A3:1A:A2:C5:A4:CA:9B:DA:70:91:71:E6:84:AE:DE:A2:BC:59:71:59:
		7B:AF:36:53:28:F9:6E:08:6D:FC:58:47:47:EF:04:30:76:B5:BD:AA:
		36:E2:1F:AE:EF:37:0F:3E:7B:D4:60:E0:3A:B7:04:DE:52:EC:B0:22:
		40:B0:4B:C6:3C:55:13:CD:8D:68:E0:41:E6:C7:08:02:E3:85:AF:A0:
		95:71:C5:5B:16:2D:65:76:2D:09:81:F7:BF:C6:87:AB:79:0E:A0:3E:
		14:92:3C:E3:EC:87:5D:39:FC:FE:E0:9C:82:17:89:57:AB:07:99:9B:
		E2:F8:D3:62:3B:45:30:51:92:27:B6:0E:8B:F4:1A:F0:3E:C7:22:FC:
		4C:85:67:53:9E:5F:06:80:48:DB:46:A9:33:D8:0C:19:B7:8C:BF:B8:
		1F:F1:8D:DD:20:AB:E6:F4:55:B4:31:53:94:99:9F:E4:BF:5F:2C:29:
		A8:5A:14:4B:D6:6F:48:F7:91:E8:95:48:58:67:8D:0E:75:57:EA:3E:
		A4:37:C5:6E:89:D1:4F:D2:6D:95:BC:95:BC:9A:9D:5C:3E:FD:01:D5:
		2C:C1:60:39:9C:A4:BD:22:73:A9:42:F6:D3:AF:37:0D:94:C6:D8:59:
		16:25:B5:CB:6D:D9:77:1A:35:E6:45:12:18:99:52:28:F4:62:95:83:
		9F:84:D3:D6:4C:8E:92:E1:EC:1E:6D:B6:34:AE:1A:62:DB:EC:86:EB:
		04:3A:B6:43:B6:29:95:ED:6C:9A:13:78:3B:C6:3F:88:B3:92:BA:49:
		9F:08:87:7A:17:34:19:EC:EA:EC:15:B7:04:FC:5F:7B:5F:AC:84:66:
		11:E5:2A:A6:0C:C5:D6:F4:F4:28:E2:A8:2B:67:F6:6D:78:08:97:AE:
		C2:AC:EC:01:E2:0A:A8:90:90:11:63:96:87:FA:7C:CE:F4:56:5D:67:
		26:72:63:B6:38:28:AB:01:F3:4A:0E:ED:51:C8:8E:5F:6F:BD:42:0E:
		A0:B1:AE:27:1E:AB:20:5D:1F:35:E7:43



```

[COLOR=#FFFFFF][FONT=ui-monospace]lsmod | grep -i 8852
[/FONT][/COLOR]
```

rtw89_8852be           16384  0
rtw89_8852b           385024  1 rtw89_8852be
rtw89_pci              73728  1 rtw89_8852be
rtw89_core            561152  2 rtw89_8852b,rtw89_pci
cfg80211             1241088  3 rtw89_8852b,rtw89_core,mac80211



```

---

### Post by #&amp;thj^% on 2024-01-04
With my Hotspot in action, I too had a small time delay before showing my dump.

---

### Post by Doug S on 2024-01-04
> **0cs935-bill said:**
> 
```

Jan  4 11:13:11 ha ubuntu-report[1755]: level=error msg="data were not delivered successfully to metrics server, retrying in 960s"

```


I wonder if a problem with ubuntu-report might be unrelated to the subject of this thread. I would disable it for this work (but I don't recall how to at the moment).

---

### Post by #&amp;thj^% on 2024-01-04
> **Doug S said:**
> I wonder if a problem with ubuntu-report might be unrelated to the subject of this thread. I would disable it for this work (but I don't recall how to at the moment).

great idea.
More on that: [https://github.com/ubuntu/ubuntu-report/](https://github.com/ubuntu/ubuntu-report/)

When I do it I want to be sure it is disabled So I run:
```
sudo apt purge ubuntu-report popularity-contest apport whoopsie -s

```
The "-s flag is a dry run."

---

### Post by Doug S on 2024-01-04
> **0cs935-bill said:**
> 
Does this look like there's a bug in the driver for the hardware?

Not sure. There is a lot of revision activity in the kernel source tree at "drivers/net/wireless/realtek/rtw89" and also specifically a driver change for "rtw8852be.c" that was only introduced after kernel 6.2., and as of 6.3-rc1. Reference: 7f495de6ae7d

It's a long shot, but just as a test try the mainline [kernel 6.7-rc8]("https://kernel.ubuntu.com/mainline/v6.7-rc8/").

---

### Post by 0cs935-bill on 2024-01-04
I went back to the zima box and it has an Intel WiFi chip and no hint of any errors anywhere.
The ha box is brand new, so probably has very recent hardware and I may be looking at a different error situation using that box, so it was probably a waste of time.


I'm going to rework an older box tomorrow to be a test bed for this so drivers, hardware, etc shouldn't be an issue.

---

### Post by 0cs935-bill on 2024-01-06
I have made some progress after I spun up a third box for testing, but no solution yet. I've worked on this continuously for days now.

Unbeknownst to me, NetworkManager starts dnsmasq with no discernable configuration information. The GUI used to configure NetworkManager has no facilities to provide or in any way configure dnsmasq. 

Years ago, I installed isc-dhcp-server and configured it not knowing an unconfigured dnsmasq was already involved. For years, this worked without a problem, except for no forwarding between networks. It's the clash between these two system that I suspect gave me the odd traffic results.

I completely eliminated isc-dhcp-server from the zima box and if I accept the default dhcp things work but not quite what's expected. Any attempt I've made so far at configuring the dnsmasq when it's a subsystem under NetworkManager has so far not worked. I'm starting a new incident on this site and think this incident is at end; at least I hope so.

---

