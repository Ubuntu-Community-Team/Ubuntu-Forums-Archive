---
title: "Steam cannot contact the server for the update"
date: 2021-06-19
forum: Networking &amp; Wireless
---

### Post by davoudi on 2021-06-19
So I installed steam and try to run it. As usual steam starts by searching for update but it fails and gives an error: [COLOR=#24292E][FONT=-apple-system]Fatal Error: Steam needs to be online to update. Please confirm your network connection and try again. I try to ping the server, [/FONT][/COLOR][COLOR=#24292E][FONT=-apple-system]media.steampowered.com and I get:

[/FONT][/COLOR]> [COLOR=#24292E][FONT=-apple-system]PING a1843.b.akamai.net (23.58.223.171) 56(84) bytes of data.[/FONT][/COLOR]
[COLOR=#24292E][FONT=-apple-system]^C[/FONT][/COLOR]
[COLOR=#24292E][FONT=-apple-system]--- a1843.b.akamai.net ping statistics ---[/FONT][/COLOR]
[COLOR=#24292E][FONT=-apple-system]8 packets transmitted, 0 received, 100% packet loss, time 7160ms[/FONT][/COLOR][COLOR=#24292E][FONT=-apple-system]
[/FONT][/COLOR][COLOR=#24292E][FONT=-apple-system]
 So I don't understand what is wrong.[/FONT][/COLOR]

---

### Post by chili555 on 2021-06-19
Are you actually connected to the internet? Check:

```
ip addr show
```

Do you have a valid IP address?

```
3: wlp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    <snip>
    inet **192.168.0.220/24 **brd 192.168.0.255 scope global noprefixroute wlp3s0
       <snip>
```Can you reach the internet?

```
ping -c3 8.8.8.8
```

Can you resolve names to numbers?

```
ping -c3 www.ubuntu.com
```

---

### Post by davoudi on 2021-06-19
> **chili555 said:**
> 
Are you actually connected to the internet? Check:

```
ip addr show
```

Do you have a valid IP address?

```
3: wlp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    <snip>
    inet **192.168.0.220/24 **brd 192.168.0.255 scope global noprefixroute wlp3s0
       <snip>
```

 This is the out put of ip addr show:
> 
[FONT=monospace][COLOR=#000000]1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000[/COLOR]
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host  
       valid_lft forever preferred_lft forever
2: ens130: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default ql
en 1000
    link/ether 00:ea:01:28:23:82 brd ff:ff:ff:ff:ff:ff
    altname enp4s0
    inet 192.168.1.107/24 brd 192.168.1.255 scope global dynamic noprefixroute ens130
       valid_lft 248862sec preferred_lft 248862sec
    inet6 fe80::59fc:e4f5:98a8:7aff/64 scope link noprefixroute  
       valid_lft forever preferred_lft forever
[/FONT]

> **chili555 said:**
> 
Can you reach the internet?
```
ping -c3 8.8.8.8
```
 This is the output.
> 
[FONT=monospace][COLOR=#000000]PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.[/COLOR]
64 bytes from 8.8.8.8: icmp_seq=1 ttl=112 time=60.5 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=112 time=58.1 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=112 time=58.0 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 57.968/58.872/60.534/1.176 ms
[/FONT]

> **chili555 said:**
> 
Can you resolve names to numbers?
```
ping -c3 www.ubuntu.com
```

 This is the output.
[QUOTE]
[FONT=monospace][COLOR=#000000]PING [www.ubuntu.com](www.ubuntu.com) (91.189.88.181) 56(84) bytes of data.[/COLOR]
64 bytes from 91.189.88.181 (91.189.88.181): icmp_seq=1 ttl=51 time=112 ms
64 bytes from 91.189.88.181 (91.189.88.181): icmp_seq=2 ttl=51 time=111 ms
64 bytes from 91.189.88.181 (91.189.88.181): icmp_seq=3 ttl=51 time=110 ms

--- [www.ubuntu.com](www.ubuntu.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 110.053/110.934/111.995/0.802 ms
[/FONT]

---

### Post by chili555 on 2021-06-19
Possibly helpful: [https://askubuntu.com/questions/227956/steam-fatal-error-steam-needs-to-be-online-to-update-but-was-set-to-offline-mo](https://askubuntu.com/questions/227956/steam-fatal-error-steam-needs-to-be-online-to-update-but-was-set-to-offline-mo)

First, I would try:

```
sudo apt install libnss-resolve:i386
```Then re-launch steam. If it fails again, we'll try other suggestions.

---

### Post by davoudi on 2021-06-19
> **chili555 said:**
> Possibly helpful: [https://askubuntu.com/questions/227956/steam-fatal-error-steam-needs-to-be-online-to-update-but-was-set-to-offline-mo](https://askubuntu.com/questions/227956/steam-fatal-error-steam-needs-to-be-online-to-update-but-was-set-to-offline-mo)

First, I would try:

```
sudo apt install libnss-resolve:i386
```Then re-launch steam. If it fails again, we'll try other suggestions.
 I already installed that following another thread in another forum.

---

### Post by chili555 on 2021-06-19
Please try this from the link:

> So, first get the IP with

ping media.steampowered.com
# returns 200.143.247.11 for me
then add that to /etc/hosts, like this:

200.143.247.11 media.steampowered.com
And it should work as expected.Please get the IP address from the ping, not the example above. It will be different for your location. My result, in SC, USA was 96.7.224.66. Yours will be different.

---

### Post by davoudi on 2021-06-20
> **chili555 said:**
> Please try this from the link:

Please get the IP address from the ping, not the example above. It will be different for your location. My result, in SC, USA was 96.7.224.66. Yours will be different.
 I tried that solution too. Steam updates successfully. Then Pins get updated. Then steam checks for update in order to start but it stuck in this step.

---

### Post by chili555 on 2021-06-20
> Then steam checks for update in order to start but it stuck in this step.If you try the ping step again, is the IP the same as previously? Does it help to add a new line to /etc/hosts?

---

### Post by davoudi on 2021-06-20
> **chili555 said:**
> If you try the ping step again, is the IP the same as previously? Does it help to add a new line to /etc/hosts?
The IP didn't change so it is the same.

---

### Post by chili555 on 2021-06-20
I regret that I haven't any further suggestions. Perhaps one of my colleagues will chime in. Sorry.

---

### Post by davoudi on 2021-06-20
> **chili555 said:**
> I regret that I haven't any further suggestions. Perhaps one of my colleagues will chime in. Sorry.
 No problem. Thanks for your time and attention.

---

### Post by davoudi on 2021-06-21
I finally manage to run steam after waiting for a while and trying it again.

---

