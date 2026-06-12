---
title: "syslog full of UFW BLOCK PROTO=ICMPv6"
date: 2014-10-06
forum: Networking &amp; Wireless
---

### Post by david144 on 2014-10-06
[Ubuntu Server 12.04.05 LTS]

Hi all, 
Hope you can help me with this

My syslog is full of these local link scope pings being blocked and I'd like to know what I have to do to allow them so it stops logging:
> 
Oct  6 13:56:26 servername kernel: [333021.138558] [UFW BLOCK] IN=eth0 OUT= MAC=33:33:00:00:00:01:80:3f:5d:87:e2:93:86:dd SRC=fe80:0000:0000:0000:823f:5dff:fe87:e293 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=76 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0


my /etc/default/ufw has:
```

[COLOR=#0000ff]# Set to yes to apply rules to support IPv6 (no means only IPv6 on loopback[/COLOR]
[COLOR=#0000ff]# accepted). You will need to 'disable' and then 'enable' the firewall for[/COLOR]
[COLOR=#0000ff]# the changes to take affect.[/COLOR]
IPV6=yes

```
(I'd prefer to leave it enabled)

I've tried adding a user rule:

```

sudo ufw allow from fe80::/10 to ff02::0001 proto icmpv6
sudo ufw allow from fe80::/10 to ff02::0001 proto ICMPv6

```

both fail with:
ERROR: Unsupported protocol 'icmpv6'
ERROR: Unsupported protocol 'ICMPv6'




I've also tried adding to the before.rules:
```

-A ufw-before-input -p icmpv6 --icmpv6-type echo-request -s fe80::/10 -j ACCEPT
&/or:
-A ufw6-before-input -p icmpv6 --icmpv6-type echo-request -s fe80::/10 -j ACCEPT

```

but then the service won't start:
> 
~$ sudo service ufw restart
ufw stop/waiting
start: Job failed to start
~$



I want to allow the link local scope to ping with ICMPv6 and I'm having a hard time searching for the proper way to allow it. The wiki's are slim on the subject
[https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)
I find nothing

[https://wiki.ubuntu.com/IPv6](https://wiki.ubuntu.com/IPv6)
```

**Tunneled IPv6**

[COLOR=#333333][FONT=Ubuntu Beta]If your uplink only passes IPv4 traffic, you will need to tunnel your IPv6 traffic to a compatible relay somewhere. Most tunnels use IPv4 protocol 41 encapsulation (6in4), where the data payload is just the IPv6 packet itself. Not all firewalls and NATs can properly pass protocol 41. Alternatively providers might provide AYIYA or TSP tunnels which send their tunneled packets over UDP, which is generally accepted by most firewalls and supported by most NATs**Note:** ICMP is protocol 1, IGMP is protocol 2, TCP is protocol 6, UDP is protocol 17.[/FONT][/COLOR]

```
(except I'm not worried about tunneled 4to1)

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
```

**Enable PING**

[COLOR=#333333][FONT=Ubuntu][FONT=inherit]_Note_[/FONT]: Security by obscurity may be of very little actual benefit with modern cracker scripts. **By default, UFW allows ping requests**. You may find you wish to leave (icmp) ping requests enabled to diagnose networking problems.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]In order to disable ping (icmp) requests, you need to edit **/etc/ufw/before.rules** and remove the following lines:[/FONT][/COLOR]

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

```
(do I have to duplicate these lines with ufw6-before-input?)

Thanks in advance for any help you can offer :)

---

### Post by david144 on 2014-10-06
I could just allow all with:
```

sudo ufw allow from fe80::/10 to ff02::1

```

but I'd rather not.

Seems like it should be possible I'm just not finding the right location or syntax somewhere.

again thanks if you can point me in the right direction :)

---

### Post by david144 on 2014-10-06
After looking into this a little more I realized this is my wireless bridge device I have connecting my non-wired bedroom htpc to my wired network.

The packets are Multicast Listener Query's (ICMPv6 Type 130) from the device looking for I'm guessing streaming devices on the network for some reason (there's nothing documented from the manufacturer as to why it's doing it, so I'm guessing)

I could of course allow all proto/ports from the specific IPv6 addresses of the two bridges but I'd like to learn how to break it down and allow the specific protocol & type.



After realizing I can't add "-A ufw6-before-input..." into the before.rules file rather than the before6.rules file... *kicks self*

Adding:
```

-A ufw6-before-input -p icmpv6 --icmpv6-type echo-request -s fe80::/10 -j ACCEPT

```
to before6.rules and restarting the service, UFW starts ok but the packets are still getting blocked, so type: [COLOR=#0000ff]echo-request[/COLOR] won't cover [COLOR=#0000ff]type=130[/COLOR] :-/

Is there any documentation about the before6.rules, and specifically the names of the [COLOR=#0000ff]--icmpv6-type[/COLOR] options?

---

### Post by david144 on 2014-10-09
turns out the [answer was simply 130]("https://answers.launchpad.net/ubuntu/+source/ufw/+question/255440"):

/etc/ufw/before6.rules
[quote=david144]
-A ufw6-before-input -p icmpv6 --icmpv6-type 130 -s fe80:0000:0000:0000:823f:5dff:fe87:e293/64 -j ACCEPT
[/quote]

```

sudo service ufw restart

```

I just didn't realize it could be a numeric value, I was assuming it had to be a word like [COLOR=#ff0000]multicast-listener[/COLOR] or something.

---

