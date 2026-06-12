---
title: "ipv6 causes slow download speeds, but if disabled cannot use vpn"
date: 2019-06-05
forum: Networking &amp; Wireless
---

### Post by sydbat on 2019-06-05
I posted this question on Ask Ubuntu but have not gotten any answers. Only an unhelpful "it's your router" comment that ignores what I have written there.

If anyone here can point me in the right direction...

Ubuntu 18.04 with low latency kernel.

I get horrible download speeds at times, especially with Steam, but also other streaming sites. I have found that if I manually disable ipv6, I get advertised download / upload speeds on my isp connection. If it is not disabled, things become really slow in a short period of time (like 2 Kbps). When I use my vpn service, everything runs fast because it disables the ipv6 stack, then re-enables it upon closing the vpn connection.

However, I got tired of having to manually disable when not using the vpn, so I permanently disabled ipv6 via grub. This completely disabled my vpn service. Even their support staff were unable to help. So I changed everything back to the way it was.

I have since disabled ipv6 in my router, which has helped increase overall speed when the network stack is at default (ipv6 enabled). Having both the router and Ubuntu ipv6 disabled increases my speed by several Mbps up and down.

To recap - ipv6, when enabled by default, slows down my Internet connection, but disabling it and only having ipv4 running makes everything faster. Disabling ipv6 in both the router and the OS makes things Speedy Gonzales. Disabling ipv6 permanently via grub kills vpn access.

Is there a way to permanently disable ipv6 so it does not break my vpn? Or some type of desktop script that can disable it manually with a click?

Thanks in advance!

How I disable ipv6 manually (checked with ip a):
```
sudo sysctl -w net.ipv6.conf.all.disable_ipv6=1
sudo sysctl -w net.ipv6.conf.default.disable_ipv6=1
```

How I permanently disabled ipv6:
```
FROM:
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""
TO:
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1"
GRUB_CMDLINE_LINUX="ipv6.disable=1"
```

---

### Post by Xian on 2019-06-05
I have nothing to test this against so I'm not promoting this as an answer. 

But it seems you might use the ifconfig command to determine your network interface. 

Then possibly create a script in the folder /etc/network/if-up.d. 
The idea would be that it should disable ipv6 when connected outside the VPN.

For example something like:

```
#!/bin/sh

if [ "$IFACE" = "eno1" ]; then
  sysctl -w net.ipv6.conf.all.disable_ipv6=1
  sysctl -w net.ipv6.conf.default.disable_ipv6=1
fi

```

---

### Post by drv9977 on 2019-06-06
I dont think using ipv6 or ipv4 can increase or decrease the internet speed, contact your ISP, there may be any technical issue on their side.

---

### Post by scimas on 2019-06-08
My issue isn't as sever as you, but it is similar. My connection speed remains as advertised by my ISP when I'm on Windows at all times, doesn't matter whether I'm watching streams on twitch, youtube videos, general internet browsing or downloading big/small files. But the connection speed does go down by a factor of 5-6 when I'm on ubuntu and watching twitch streams. This struck me as really weird and I came across some askubuntu questions, saying that disabling ipv6 helped with the "extremely slow internet". So I went ahead tested it with my wifi on ubuntu. Just went to the IPv6 tab in edit connection and selected the ignore option. Disconnected from the network and reconnected. And it actually worked...?! Now I have no speed drop when watching on Twitch.

So I know this post isn't giving you a solution, but the fact that disabling ipv6 increases speed is really strange. I would like to hear some explanation from someone that understands these things, too.

---

### Post by sydbat on 2019-06-10
This seems to work!! I have tested it a bit and every time so far, it disables ipv6. YAY!!!

> **Xian said:**
> I have nothing to test this against so I'm not promoting this as an answer. 

But it seems you might use the ifconfig command to determine your network interface. 

Then possibly create a script in the folder /etc/network/if-up.d. 
The idea would be that it should disable ipv6 when connected outside the VPN.

For example something like:

```
#!/bin/sh

if [ "$IFACE" = "eno1" ]; then
  sysctl -w net.ipv6.conf.all.disable_ipv6=1
  sysctl -w net.ipv6.conf.default.disable_ipv6=1
fi

```

---

### Post by sydbat on 2019-06-10
@drv9977 - Shouldn't effect things, but it does. I believe this is why there have been so many people asking how to disable ipv6 for years. It has to be some overlooked code in the kernel? some other part of the OS? in the network stack?? Because ipv6 is not really anywhere yet, I think no one has really noticed much, except for those having issue with download speeds.

@scimas - I would like to know why as well. I would also like them to fix it.

---

