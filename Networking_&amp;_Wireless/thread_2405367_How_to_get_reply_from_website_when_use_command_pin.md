---
title: "How to get reply from website when use command ping in terminal"
date: 2018-11-05
forum: Networking &amp; Wireless
---

### Post by yeulukem on 2018-11-05
Hello EV1

First, sorry for my english

I'm new with ubuntu and i have just installed ubuntu 18.04 LTS on my PC, in Windows, when i ping a website with command ping (ex: ping google.com) and i got reply from google like this image

[ATTACH=CONFIG]281544[/ATTACH]

But in ubuntu, when i use terminal to ping a website then it's display like this


[ATTACH=CONFIG]281545[/ATTACH]

Please tell me how to get reply by command ping in ubuntu

Tks

---

### Post by vidtek on 2018-11-05
> **yeulukem said:**
> Hello EV1

First, sorry for my english

I'm new with ubuntu and i have just installed ubuntu 18.04 LTS on my PC, in Windows, when i ping a website with command ping (ex: ping google.com) and i got reply from google like this image

[ATTACH=CONFIG]281546[/ATTACH]

But in ubuntu, when i use terminal to ping a website then it's display like this


[ATTACH=CONFIG]281547[/ATTACH]

Please tell me how to get reply by command ping in ubuntu

Tks


Yeulukem-

The reply you got is a bit weird, mine came back like this:```
tony@linuxmint:~$ ping google.com
PING google.com (216.58.198.174) 56(84) bytes of data.
64 bytes from lhr25s10-in-f14.1e100.net (216.58.198.174): icmp_seq=1 ttl=54 time=16.9 ms
64 bytes from lhr25s10-in-f14.1e100.net (216.58.198.174): icmp_seq=2 ttl=54 time=16.9 ms
64 bytes from lhr25s10-in-f14.1e100.net (216.58.198.174): icmp_seq=3 ttl=54 time=16.5 ms
64 bytes from lhr25s10-in-f14.1e100.net (216.58.198.174): icmp_seq=4 ttl=54 time=17.1 ms
64 bytes from lhr25s10-in-f14.1e100.net (216.58.198.174): icmp_seq=5 ttl=54 time=16.6 ms
64 bytes from lhr25s10-in-f14.1e100.net (216.58.198.174): icmp_seq=6 ttl=54 time=16.6 ms
^C
--- google.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5007ms
rtt min/avg/max/mdev = 16.563/16.814/17.122/0.226 ms
```

Maybe your isp has a "ping policy", or your router modifies the results.  I really have no idea.
The ping command gives very similar results in both Windows and Linux, the Windows ping command truncates the output to 4 instances, Linux will go forever.

Tony.

---

### Post by wyliecoyoteuk on 2018-11-05
That looks like an IPv6 address, which is a bit odd, as ping is ipv4, and ping6 is ipv6.
Try

 ```
ip-4 route
```
and
```
ip -6 route
```

---

### Post by slickymaster on 2018-11-05
@yeulukem

Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box

---

### Post by wyliecoyoteuk on 2018-11-05
pinging by hostname is the issue, the DNS serbver is returning ipV6 info, which ping can't use.
Try changing your DNS server to 8.8.8.8, or use 
```
ping6 google.com
```

---

### Post by yeulukem on 2018-11-05
> **vidtek said:**
> Yeulukem-

The reply you got is a bit weird, mine came back like this:```
tony@linuxmint:~$ ping google.com
PING google.com (216.58.198.174) 56(84) bytes of data.
64 bytes from lhr25s10-in-f14.1e100.net (216.58.198.174): icmp_seq=1 ttl=54 time=16.9 ms
64 bytes from lhr25s10-in-f14.1e100.net (216.58.198.174): icmp_seq=2 ttl=54 time=16.9 ms
64 bytes from lhr25s10-in-f14.1e100.net (216.58.198.174): icmp_seq=3 ttl=54 time=16.5 ms
64 bytes from lhr25s10-in-f14.1e100.net (216.58.198.174): icmp_seq=4 ttl=54 time=17.1 ms
64 bytes from lhr25s10-in-f14.1e100.net (216.58.198.174): icmp_seq=5 ttl=54 time=16.6 ms
64 bytes from lhr25s10-in-f14.1e100.net (216.58.198.174): icmp_seq=6 ttl=54 time=16.6 ms
^C
--- google.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5007ms
rtt min/avg/max/mdev = 16.563/16.814/17.122/0.226 ms
```

Maybe your isp has a "ping policy", or your router modifies the results.  I really have no idea.
The ping command gives very similar results in both Windows and Linux, the Windows ping command truncates the output to 4 instances, Linux will go forever.

Tony.

Hello Tony "Stark", thanks for your reply but i think it's not a ISP's policy or problem with router because i have some PCs could run well on Windows, as in my first post, i can ping in windows without any problem. (at my Office)

It's a bit weird because at my home, i have installed Linux Mint and i got same problem (without any problem in windows - dual boot)

Actually, it's not a big problem as i can use Linux Mint for my work (web, mail,....) but at my Office, my boss give me a new server and told me that i had to learn linux to secure my network and virus (ransomware) and i have installed ubuntu server and got this problem

> **wyliecoyoteuk said:**
> That looks like an IPv6 address, which is a bit odd, as ping is ipv4, and ping6 is ipv6.
Try

 ```
ip-4 route
```
and
```
ip -6 route
```

Hello Wyliecoyoteuk:
 ip -4 route
```
default via 192.168.1.1 dev wlp3s0 proto dhcp metric 600 
192.168.1.0/24 dev wlp3s0 proto kernel scope link src 192.168.1.10 metric 600
```
ip -6 route
```

2402:800:6313:c717::/64 dev wlp3s0 proto ra metric 600 pref medium
fe80::/64 dev wlp3s0 proto kernel metric 256 pref medium
fe80::/64 dev wlp3s0 proto kernel metric 600 pref medium
default via fe80::1 dev wlp3s0 proto ra metric 600 pref medium

```

> **slickymaster said:**
> @yeulukem

Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box

Hello Admin, sorry for that, actually, i don't know how to use GNU Image to crop and resize image, i'm sure this fault never come back

> **wyliecoyoteuk said:**
> pinging by hostname is the issue, the DNS serbver is returning ipV6 info, which ping can't use.
Try changing your DNS server to 8.8.8.8, or use 
I have change dns 8.8.8.8 at /etc/resolve.conf but no luck

```
ping6 google.com
```

Hello again
ping6 google.com and got same problem with ping google.com

---

### Post by wyliecoyoteuk on 2018-11-05
resolv.conf is no longer used in 18.04. Netplan is used now.

[https://www.techrepublic.com/article/how-to-set-dns-nameservers-in-ubuntu-server-18-04/](https://www.techrepublic.com/article/how-to-set-dns-nameservers-in-ubuntu-server-18-04/)

---

### Post by The Cog on 2018-11-05
That is indeed an IPv6 address that your Ubuntu is trying to ping. Google have both IPv4 and IPv6 addresses, and IPv6 is preferred if both are available.

Ping does indeed support both IPv4 and IPv6 these days. Here is a screenstrape from my PC:
```
steve@StevesPC:~$ ping 10.9.8.5
PING 10.9.8.5 (10.9.8.5) 56(84) bytes of data.
64 bytes from 10.9.8.5: icmp_seq=1 ttl=64 time=12.2 ms
64 bytes from 10.9.8.5: icmp_seq=2 ttl=64 time=21.8 ms
^C
--- 10.9.8.5 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 12.283/17.043/21.803/4.760 ms
steve@StevesPC:~$ ping fc00::5
PING fc00::5(fc00::5) 56 data bytes
64 bytes from fc00::5: icmp_seq=1 ttl=64 time=2.08 ms
64 bytes from fc00::5: icmp_seq=2 ttl=64 time=2.05 ms
^C
--- fc00::5 ping statistics ---
```

I can't show you ping of a public IPv6 address because my ISP is rubbish and doesn't yet provide any IPv6 connectivity. 
It would appear that your ISP is also rubbish, and provides both DNS resolution and a default route but not actual traffic connectivity. This should get your pings working:
```
ping -4 google.com
```
Since your IPv6 default gateway appars not to pass actual traffic, you may need to remove the default route before you can connect to web sites that have public IPv6 addresses, thereby forcing your server to use IPv4 instead.

P.S. Your windows box appears not to have discovered the IPv6 default gateway at all, so is using IPv4 which your ISP is actually supporting.

---

### Post by yeulukem on 2018-11-05
> **wyliecoyoteuk said:**
> resolv.conf is no longer used in 18.04. Netplan is used now.

[https://www.techrepublic.com/article/how-to-set-dns-nameservers-in-ubuntu-server-18-04/](https://www.techrepublic.com/article/how-to-set-dns-nameservers-in-ubuntu-server-18-04/)

Hello, Tks for your advice

> **The Cog said:**
> That is indeed an IPv6 address that your Ubuntu is trying to ping. Google have both IPv4 and IPv6 addresses, and IPv6 is preferred if both are available.

Ping does indeed support both IPv4 and IPv6 these days. Here is a screenstrape from my PC:
```
steve@StevesPC:~$ ping 10.9.8.5
PING 10.9.8.5 (10.9.8.5) 56(84) bytes of data.
64 bytes from 10.9.8.5: icmp_seq=1 ttl=64 time=12.2 ms
64 bytes from 10.9.8.5: icmp_seq=2 ttl=64 time=21.8 ms
^C
--- 10.9.8.5 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 12.283/17.043/21.803/4.760 ms
steve@StevesPC:~$ ping fc00::5
PING fc00::5(fc00::5) 56 data bytes
64 bytes from fc00::5: icmp_seq=1 ttl=64 time=2.08 ms
64 bytes from fc00::5: icmp_seq=2 ttl=64 time=2.05 ms
^C
--- fc00::5 ping statistics ---
```

I can't show you ping of a public IPv6 address because my ISP is rubbish and doesn't yet provide any IPv6 connectivity. 
It would appear that your ISP is also rubbish, and provides both DNS resolution and a default route but not actual traffic connectivity. This should get your pings working:
```
ping -4 google.com
```
Since your IPv6 default gateway appars not to pass actual traffic, you may need to remove the default route before you can connect to web sites that have public IPv6 addresses, thereby forcing your server to use IPv4 instead.

P.S. Your windows box appears not to have discovered the IPv6 default gateway at all, so is using IPv4 which your ISP is actually supporting.

Hello The Cog, work like charm, you are genius :)

Tks Ubuntuforums :)

---

