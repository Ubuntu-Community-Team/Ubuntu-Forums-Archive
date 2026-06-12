---
title: "IP of gateway"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by andrei.kouznetsov on 2008-05-29
Hi, I have the following situation:
I connect to the internet through a gateway. This gateway connects to the internet using DHCP. Thus, every time it connects to the internet, it gets new IP address. I need its IP address to manipulate with the gateway through my web browser. How can I get its IP address?

---

### Post by kevdog on 2008-05-29
Doesn't the gateway have two IP addresses (an internal and external IP address).  If connecting through the gateway, if you go the [www.showmyip.com](www.showmyip.com), shouldn't this show you your external IP address of the gateway --> (this value could be optained in a shell script, using wget, and the result filtered to deliver the IP address using awk/sed).

---

### Post by andrei.kouznetsov on 2008-05-29
Yes, the gateway has two IP addresses. I am interested in the internal address, because I'm inside. By try and error I have found out that now my gateway is 192.168.1.101. It is an internal address. So, what did you say about awk/sed/wget?
I get
```

wget http://www.google.com
--15:40:11--  http://www.google.com/
           => `index.html'
Resolving www.google.com... 208.67.219.230, 208.67.219.231
Connecting to www.google.com|208.67.219.230|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 6,351         --.--K/s             

15:40:11 (95.06 KB/s) - `index.html' saved [6351]

```

I don't see the internal address of my gateway.

---

### Post by chili555 on 2008-05-29
```
chili@LAPTOP60:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         **192.168.1.1**     0.0.0.0         UG    100    0        0 eth1
```My gateway is then 192.168.1.1. If you need the router's external IP, see: [http://whatismyip.com/](http://whatismyip.com/)

---

### Post by andrei.kouznetsov on 2008-05-29
Hm, I have almost the same output:
```

~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```

but there is no 192.168.1.101. However, if I type in firefox [http://192.168.1.101](http://192.168.1.101), I get the webpage of my gateway.

I will try to explain the situation on the diagram:

**Me** <-ethernet-> **WGA** <-Wi-Fi-> **Router** <-ethernet-> **Internet**

192.168.1.1 is IP address of the router. I need the address of WGA (Wireless Gaming Adapter).

---

### Post by chili555 on 2008-05-29
> I get the webpage of my gateway.I'm a bit confused. Maybe it's because I'm old, but I don't understand. When you open *[http://192.168.1.101](http://192.168.1.101)* do you get the web interface for your router or your WGA?

What happens if you try *[http://192.168.1.1](http://192.168.1.1)*? Do you get the web interface page for your WGA?

Logically, it seems that your computers interface is shown in *ifconfig*; your WGA is 192.168.1.1 and your router is 192.168.1.101. Do you have any information that disagrees with this?

---

### Post by elamericano on 2008-05-29
If you broadcast ping the subnet (e.g. ping -b -c3 192.168.1.255) then it will show up in your arp cache if it eventually responds (arp -a | grep 00:15:F2:FF:26:99)

So, this works for me:
ping -b -c3 192.168.1.255 && sleep 5 && arp -a | grep 00:15:F2:FF:26:99

Obviously, you need to know the mac address of your WGA.

---

### Post by elamericano on 2008-05-29
chili555, I read it the same way. I would call the WGA a router, because the other device (a server?) has the gateway address.

---

### Post by chili555 on 2008-05-29
I think his wireless gaming adapter (WGA) is nothing more than a wireless ethernet bridge. I have one at my home server in the garage. They are a painless way to have wireless on any computer with an ethernet jack.

Sounds like he has the DHCP server set on _both_ the WGA and the router. His computer therefore got an IP address from the WGA and sees it as the gateway.

But I could be wrong. My server has a static address so you can reach it easily, and DHCP is off on the wireless bridge. The gateway on the server is set as 192.168.1.1, the router.

I'm not sure I understand enough about what andrei is trying to accomplish to know if he's headed in the right direction.

---

### Post by elamericano on 2008-05-29
Since 192.168.1.101 worked for him, I'm guessing that what he identified as his "router" has the DHCP server, and it gave an IP address to his computer and his WGA wireless access point. Thus, he doesn't know what IP address his WGA got.

Normally, I'd agree with you, because a lot of wireless access points are setup to NAT by default, but I'm going from his description.

Andrei, if post #7 doesn't work for you and [http://192.168.1.1](http://192.168.1.1) doesn't give you the webpage, let us know where the DHCP server is running.

---

### Post by andrei.kouznetsov on 2008-05-29
So, I will try again. My laptop connects to the internet through 2 devices. The first device is WGA, the second is a router. Essentially, WGA is an external wi-fi adapter. I connect my laptop to WGA by ethernet cable. So, I can manipulate with WGA using a web browser if I know IP of my WGA. By default the IP of WGA is 192.168.1.250. WGA is connected to my router through wi-fi. Router has DHCP. So, when I tell my WGA to connect to the router using DHCP, the router assigns a different IP address to WGA. The default IP address 192.168.1.250 does not work anymore, now it is 192.168.1.101. If I restart WGA or the router, there will be a different IP assigned, essentially the IP is random. So, I can not manipulate my WGA unless I know its new IP. The IP 192.168.1.1 is the IP of my router.

Here is the summary:
WGA has IP address 192.168.1.101
Router has IP address 192.168.1.1

The router assignes random IP to WGA when WGA connects to the router. I need IP of WGA to manipulate with WGA.

I hope, now it is clear.

---

### Post by andrei.kouznetsov on 2008-05-29
[http://192.168.1.1](http://192.168.1.1) gives the webpage of the router
[http://192.168.1.101](http://192.168.1.101) gives the webpage of the WGA

I'm not sure, but I think that DHCP is running on the router (it is a linksys device, I think it has DHCP). Also, I think DHCP is running on WGA too.

---

### Post by elamericano on 2008-05-29
Yes, clear. So:

ping -b -c3 192.168.1.255 && sleep 5 && arp -a | grep <WGA Mac Address>

should work. Do you know the Mac address of the WGA device?

---

### Post by andrei.kouznetsov on 2008-05-30
> **elamericano said:**
> Yes, clear. So:

ping -b -c3 192.168.1.255 && sleep 5 && arp -a | grep <WGA Mac Address>

should work. Do you know the Mac address of the WGA device?

Thank you for the reply. Yes, I think I can get the MAC address when I log in to my WGA. Here is the result
```

~$ ping -b -c3 192.168.1.255 && sleep 5 && arp -a
WARNING: pinging broadcast address
PING 192.168.1.255 (192.168.1.255) 56(84) bytes of data.

--- 192.168.1.255 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2010ms

```
I didn't do grep. It is strange, because there is no response from the broadcast. However, I get a response from that
```

$ ping -c 3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=2.23 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=2.00 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=2.49 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 2.009/2.246/2.495/0.202 ms

```

---

### Post by chili555 on 2008-05-30
Ah, ha! Now I think I get it! You want to be able to make changes in the WGA for ports to open for specific games, or the such, and to do so, you need to be able to log into the WGA's web-based administration page. But you can't find it, because it keeps changing. Do I have it? Forgive me; I am old and slow.

The solution is, quite simply, to set up the WGA with a static IP address and turn off DHCP in the WGA. Let the router behind it give DHCP addresses to the computers and game consoles behind the WGA.

Since you know 192.168.1.101 will work, why not use that? If you are old and slow like me, you might take a Sharpie and jot on the bottom of the WGA: **IP=192.168.1.101**.

---

### Post by jimv on 2008-05-30
If you look in the configuration for your router, there should be a spot where you can set it to always assign the WGA the same address.  That way you don't have to worry about it changing.  OR you can set the DHCP lease time on the router to some insane amount of time.

---

### Post by andrei.kouznetsov on 2008-05-30
> **chili555 said:**
> Ah, ha! Now I think I get it! You want to be able to make changes in the WGA for ports to open for specific games, or the such, and to do so, you need to be able to log into the WGA's web-based administration page. But you can't find it, because it keeps changing. Do I have it? Forgive me; I am old and slow.
Yes, you are absolutely right. The only correction is that I use it to connect to different wireless networks. I don't have an internal wi-fi adapter, so I use WGA. Not the best solution but it's what I have now.

The problem in your solution is that some wireless networks require that I use DHCP. For example my university wireless network requires it. Also, 192.168.1.101 is not always the IP of WGA. For example, it has changed again now. I can't find it again :(.

The manual of WGA syas
>   Obtain IP Address automatically (DHCP). If your network assigns IP addresses via DHCP, select this setting. .
I guess I can't just switch it off in my situation.

---

### Post by fwre01 on 2008-05-30
> **andrei.kouznetsov said:**
> Yes, you are absolutely right. The only correction is that I use it to connect to different wireless networks. I don't have an internal wi-fi adapter, so I use WGA. Not the best solution but it's what I have now.

The problem in your solution is that some wireless networks require that I use DHCP. For example my university wireless network requires it. Also, 192.168.1.101 is not always the IP of WGA. For example, it has changed again now. I can't find it again :(.

The manual of WGA syas
.
I guess I can't just switch it off in my situation.

andrei.kouznetsov, if i understand this correctly, why dont you set the WGA up with a static address say 192.168.1.2 from the GUI? you arent using this as your default gateway or DHCP server.

The WGA itself (i believe) is a layer 2 device, meaning you dont need to punch holes through it for games ect... it will switch frames based on the MAC address, not layer 3 or above

...hope that didn't confuse things further

---

### Post by andrei.kouznetsov on 2008-05-30
> **fwre01 said:**
> andrei.kouznetsov, if i understand this correctly, why dont you set the WGA up with a static address say 192.168.1.2 from the GUI? you arent using this as your default gateway or DHCP server.

The WGA itself (i believe) is a layer 2 device, meaning you dont need to punch holes through it for games ect... it will switch frames based on the MAC address, not layer 3 or above

...hope that didn't confuse things further

I don't set it up for static IP because some networks require DHCP. I use WGA to connect to those networks. The WGA by itself is a client that connects through wi-fi and it gives me access to the networks through ethernet.

---

