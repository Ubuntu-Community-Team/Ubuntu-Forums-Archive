---
title: "tcpdump won't dump the wireless hotspot interface on a multihomed box"
date: 2023-12-31
forum: Networking &amp; Wireless
---

### Post by 0cs935-bill on 2023-12-31
Ubuntu 22.04LTS fully patched.
While investigating a routing issue, I tried to dump traffic on a wireless hotspot interface.
 
 [COLOR=#000000][FONT=&quot]tcpdump -i wlp1s0 -envs 128 host 192.168.2.1[/FONT][/COLOR]

A ping to the IP yielded no tcpdump output. I thought I made a mistake in setting up the tcpdump command until it suddenly output a few lines of who-has traffic. Did a ping against that IP from the box itself as well as another box and there is no tcpdump output for the pings. The only output is periodic who-has. Why is there no ping traffic output, and more important, how do I get a dump of  all traffic on a wireless interface set up as a hotspot?

BTW - the routing issue I'm trying to debug is no routing between two private networks (1 wired 192.168.1.0/24, 1 wireless 192.168.2.0/24) when both function fine through the 3rd network going to the public Internet with  cat /proc/sys/net/ipv4/ip_forward = 1

---

### Post by #&amp;thj^% on 2023-12-31
> **0cs935-bill said:**
> ** how do I get a dump of  all traffic on a wireless interface set up as a hotspot?**

BTW - the routing issue I'm trying to debug is no routing between two private networks (1 wired 192.168.1.0/24, 1 wireless 192.168.2.0/24) when both function fine through the 3rd network going to the public Internet with  cat /proc/sys/net/ipv4/ip_forward = 1

I would think a hostpad config would be needed for that set-up
One to browse over: [https://w1.fi/cgit/hostap/tree/hostapd/hostapd.conf?h=hostap_2_10#n539](https://w1.fi/cgit/hostap/tree/hostapd/hostapd.conf?h=hostap_2_10#n539)
What about Wireshark?

---

### Post by SeijiSensei on 2023-12-31
Is IP forwarding enabled on all machines? If not, give that a try.

---

### Post by #&amp;thj^% on 2023-12-31
> **SeijiSensei said:**
> Is IP forwarding enabled on all machines? If not, give that a try.

+1 Good point.
This is Off:
```
cat /proc/sys/net/ipv4/ip_forward
0

```
this is On
```
cat /proc/sys/net/ipv4/ip_forward
1

```
I set this at install for the OS
If you need here is a quick cli for On:
```
sudo sysctl -w net.ipv4.ip_forward=1

```

---

### Post by 0cs935-bill on 2023-12-31
I had completely forgotten about hostapd. I tried unsuccessfully to set that up many years ago and never thought about it since. I might give that another go if I can't figure out how to get a look at packets. I'm comfortable with tcpdump and never used wireshark but I'll give it a try to see if can show what's going on.

---

### Post by 0cs935-bill on 2023-12-31
All packets with source on N1 and destination not on N1 are automatically going to MASTER as part of the gateway mechanism, so I didn't see how setting  [FONT=Ubuntu Mono, monospace][COLOR=#000000]ip_forward=1 on an N1 box was going to do any good, but tried it. It didn't change anything. It was worth a shot, so thanks for the thought.[/COLOR][/FONT]

[FONT=Ubuntu Mono, monospace][COLOR=#000000]My understanding is that option only makes sense when more than one network exists on a box and my N1 boxes only have a single NIC configured.[/COLOR][/FONT]

[FONT=Ubuntu Mono, monospace][COLOR=#000000]The immediate issue is not being able to see packets hitting the wireless interface. I need to find out where a packet is just dropped. I can tcpdump MASTER's N1 interface and see the inbound packet, but I have no idea if it was routed to MASTER's N2 or not, so I don't know if it's actually a routing issue or it's hotspot code trashing packets for whatever reason.[/COLOR][/FONT]

---

### Post by #&amp;thj^% on 2023-12-31
Not exactly as your set-up, but suggests hostpad was needed: [https://superuser.com/questions/1699830/tcpdump-doesnt-capture-wifi-to-wifi-traffic](https://superuser.com/questions/1699830/tcpdump-doesnt-capture-wifi-to-wifi-traffic)

---

### Post by 0cs935-bill on 2023-12-31
Thanks for the reference. It would appear that the tcpdump thing is an old known deficiency, so beating a dead horse isn't going to get me anywhere. To satisfy my curiosity I'd still like to know if its a routing thing or if hotspot code gets the packet and trashes it somehow.

I really do hate to disturb my hotspot config to run all the wireless gadgets because WiFi is a "Rube Goldberg machine". I guess I'll turn the hotspot off and hope it just hangs out in the background and an install of hostapd doesn't step on it in case hostapd doesn't solve the problem.

Good catch on your part. Thanks a lot.

---

### Post by #&amp;thj^% on 2023-12-31
Good Luck, and please keep us posted my curiosity is peaked now. :)

---

### Post by 0cs935-bill on 2023-12-31
Well, that was quick. I discovered wireshark is an application that runs on that 'other' operating system that I haven't seen since 1999. 

Tried hostapd and it brought back the memories of why I didn't pursue it maybe 10 years ago. It seems that NetworkManager and hostapd aren't on speaking terms. I ran it at the console and it appears NM owns the NIC and won't share. The docs for hostapd are near nonexistent and what docs I found are so out of date that they're talking about things that haven't existed in many O/S releases.

I think hostapd is a vestigial relic of bygone days.

I'm back to square one.

---

### Post by Doug S on 2023-12-31
Please describe your network(s) in more detail.

> **0cs935-bill said:**
>  [COLOR=#000000][FONT=&quot]tcpdump -i wlp1s0 -envs 128 host 192.168.2.1[/FONT][/COLOR]

What is the IP address of w1p1s0?
Why are you only asking for packets to/from 192.168.2.1?

> **0cs935-bill said:**
> how do I get a dump of  all traffic on a wireless interface set up as a hotspot?
Well, delete the "host 192.168.2.1" filter as a start.

> **0cs935-bill said:**
> the routing issue I'm trying to debug is no routing between two private networks (1 wired 192.168.1.0/24, 1 wireless 192.168.2.0/24) when both function fine through the 3rd network going to the public Internet with  cat /proc/sys/net/ipv4/ip_forward = 1So, there is a NIC in the computer on the 192.168.1.0/24 network? What is the 3rd network?

Currently I am not at all following what packet flow should be and via what interfaces.

---

### Post by 0cs935-bill on 2023-12-31
[COLOR=#000000][I]wlp1s0 is 192.168.2.1
That's the interface all packets have to travel through to get to any other box on the 192.168.2.0/24 network from the N1 network at 192.168.1.0/24.
The traffic has to go through that interface to get to anywhere else so i want to see it land there as the next hop. The tcpdump utility doesn't even show ping traffic directed at that IP even though the pings work as expected. Something is preventing tcpdump from displaying the traffic.
The 3rd network is the Internet connection and really has nothing to do with traffic between the two private networks.[/I][/COLOR]

---

### Post by 0cs935-bill on 2024-01-01
Here is what I see on what I referred to as MASTER.

The ifconfig shows the interface wlp1s0 is 192.168.2.1
The tcpdump, now without any host specification displays nothing while the ping against that IP run on the same machine executes fine.

The issue is that I can't dump traffic on the wireless interface.

---

### Post by Doug S on 2024-01-01
No, tcpdump would not capture any packet traffic for the example in your screen shot.
That is the expected behaviour.
Why? Because no packets actually go anywhere. You are "ping"ing the NIC within the same computer itself.

I get the same on my test server, and expect to.
But if I ping such that I know traffic actually leaves the NIC, then tcpdump captures it.

---

### Post by 0cs935-bill on 2024-01-01
You're right.

However, when I set up a tcpdump on the wired interface of MASTER, no host, and ping it from my wired box, the traffic shows up.
When I set up a tcpdump on the wireless interface of MASTER, no host, and ping it from my wired box, the traffic doesn't show up.

This is with MASTER's IP_FORWARDING turned on and the symptoms from my wired box's perspective is: **Destination Port Unreachable** and it's MASTER's wired NIC reporting.

---

### Post by Doug S on 2024-01-01
I see your other post, with a lot more of the information I have been asking for. Readers also see [here]("https://ubuntuforums.org/showthread.php?t=2493975").

---

