---
title: "Multiple simultaneous vpn connections?"
date: 2017-01-01
forum: Networking &amp; Wireless
---

### Post by tinynja98 on 2017-01-01
Hello, i have been trying for the past hour or so to do what i wanted to do by searching on the webz, but with no success. Here's what i'm wanting to achieve:

- I have multiple wireless devices which i want to connect to my computer by hosting a WiFi Hotspot on it (i'm good with setting up this part);
- Setup multiple vpn connections to different vpn servers on the same computer which is hosting the WiFi Hotspot;
- Specify which vpn connection will be used by a specific wireless device (using its local ip address, since i could reserve it to its mac address).

So, in short, let's say i'm using iPod Touch #1, it would be connected to the WiFi Hotspot of my computer, and if i check its external IP, it would be the one of VPN #1. If i'm using iPod Touch #2, it too would be connected to the WiFi Hotspot of my computer, and its external IP would be that of VPN #2.

The part i'm having difficulty with is setting multiple vpn connections. Once that is done, i think i can manage the routing using ufw. Thanks for your help :)

---

### Post by SeijiSensei on 2017-01-01
If you're using OpenVPN, assign each connection to a different port number in separate configuration files under /etc/openvpn.

---

### Post by tinynja98 on 2017-01-01
All that i can see in /etc/openvpn is the file "update-resolv-conf". What do i have to write in the separate configuration files to assign a connection a port number?

UPDATE: I have added the two vpn servers to which i want to connect simultaneously to network-manager, and i also added a second tun interface, setting each vpn to use a different tun interface. However, the first vpn connection works perfectly (using the drop down menu from the top right of the screen) but when i try to connect to the second vpn, it connects for a minute or so and then it disconnects. The first vpn connected stays on all the time, only the second one disconnects after a minute. Why is this happening?

---

### Post by SeijiSensei on 2017-01-02
I've never used Network Manager for VPNs, but off the top of my head I'd guess you have a routing problem. Please post the results of the command "route -n" after the first tunnel is created and again immediately after the second one comes up before it disconnects.

---

### Post by tinynja98 on 2017-01-02
Yay thanks for coming back to me! I thought my thread would end up in the trash :p Well what would you use instead of Network Manager for VPNs? I just want it to work, i don't care how... But here are the results of "route -n":

Before any vpn is connected:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp2s0f2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0f2
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0f2
```

After the first vpn is connected:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.12.1.53      0.0.0.0         UG    50     0        0 tun0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp2s0f2
10.12.0.1       10.12.1.53      255.255.255.255 UGH   50     0        0 tun0
10.12.1.53      0.0.0.0         255.255.255.255 UH    50     0        0 tun0
142.4.206.228   192.168.1.1     255.255.255.255 UGH   100    0        0 enp2s0f2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0f2
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0f2
```

After the first and the second vpn are connected:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.12.1.53      0.0.0.0         UG    50     0        0 tun0
0.0.0.0         10.12.0.93      0.0.0.0         UG    51     0        0 tun2
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp2s0f2
10.12.0.1       10.12.1.53      255.255.255.255 UGH   50     0        0 tun0
10.12.0.93      0.0.0.0         255.255.255.255 UH    50     0        0 tun2
10.12.1.53      0.0.0.0         255.255.255.255 UH    50     0        0 tun0
142.4.206.228   192.168.1.1     255.255.255.255 UGH   100    0        0 enp2s0f2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0f2
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0f2
198.7.62.204    192.168.1.1     255.255.255.255 UGH   100    0        0 enp2s0f2
```

---

### Post by SeijiSensei on 2017-01-03
There needs to be just one default route, the one for 0.0.0.0/0.  If you're trying to push all your traffic through a tunnel, then pick one and set that as the default route.  However you will need to specify a route to the VPN server via your router, which looks to be 192.168.1.1.  Then the tunnel can be maintained via the public Internet, but everything else will go through the tunnel.

What purpose does the second tunnel serve? Why do you need it at all?

---

### Post by tinynja98 on 2017-01-03
Well basically, the whole point of this is to have a vpn running on my iPod Touch's, each having a different IP. I know i can run the vpn directly from iOS, but i have already tried that and i find it isn't reliable enough since the vpn would get disconnected after X amount of time, letting my real IP able to be seen when using the device. For that, desktop OS are much more reliable because you can do much more configuration than on iOS. (the second [and more] tunnels is because i want to use 1 computer to host the vpn's of multiple devices, rather than using a separate computer for each device)

I don't understand what you told me in the last post. What is the default route in my setup when i have both VPN's enabled?

Further explanation: what i want to do is that i would have multiple VPN's enabled on my computer, and everything (except the data coming from specific devices connected to the hotspot hosted by the computer) would go through ONE vpn, and ONLY the data coming and going from/to the specific local ip address of my iPod Touch#1 which is connected to the hotspot of my computer would use the second vpn.

---

### Post by tinynja98 on 2017-01-04
There ya go... that should be easier to understand ;)

[IMG]http://content.screencast.com/users/tinynja98/folders/Snagit/media/b7ab88ad-522d-409a-85c2-dee600e382bb/01.04.2017-00.21.png[/IMG]

---

### Post by SeijiSensei on 2017-01-05
You can't have a VPN from the router to Google or any other external host on the Internet except for a computer you control or a VPN provider. If you're visiting HTTPS sites, your traffic is already encrypted so a VPN is redundant.

---

### Post by tinynja98 on 2017-02-15
Ok my bad... I had wrong understanding of VPN's... I think that would be a more accurate representation of what I'm trying to do:
[IMG]http://i.imgur.com/CJGyQSm.png[/IMG]

---

### Post by tinynja98 on 2017-02-18
Hey SeijiSensei! I have have tried connecting to two VPN's using the openvpn command in the terminal and it seems that openvpn creates the routes by itself. How can I control  the routes which will be added when I launch a VPN so it doesn't add default routes and it only adds the strict minimum routes required (I have no idea which ones are required so please enlighten me on this part)?

EDIT: I saw that the option "redirect-gateway" was included in the .ovpn files provided by vpnbook, the vpn which i am using to test everything, but even removing that option (and rebooting just to make sure), when i run the command "sudo openvpn vpnbook.conf", i see that openvpn adds default routes with 128.0.0.0. Why is it doing this?

---

### Post by Mobile Data Solutions on 2018-01-04
This is an old thread, but FYI for anyone reading this w/this problem.... What you need to focus on is:

1. You cannot have >1 default gateway as previously mentioned
2. You need a way to seperate traffic that will go thru your VPN and traffic that won't
3. If you want ALL traffic through a VPN, that's fine and is the default behavior of OpenVPN
4. Again, you can have only ONE default route; that can be via a VPN or via normal Internet connection

Now, when someone says they want to use more than one VPN, the question is do they really want >1 VPN or do they want >1 connection to a single VPN?

>1 connection to a single VPN means multiple devices connecting to that VPN. If that is what you want, there are 2 ways to accomplish that. 

1) The VPN client is at your gateway router. Have your devices connect normally to  your LAN, and have  your router connects to VPN and routes all external traffic through it; or
2) Each device has client VPN software installed and connects to the same VPN on its own. This method requires your VPN provider to allow the # of connections you want (# devices).

The other possibility... you want to connect to multiple VPNs... means you need a way to segment your traffic. This is a form of Split VPN. Again, it will depend if you want your gateway router to make the decision on where the traffic is routed (which VPN) or if each device will decide which VPN it will use. How will your traffic be making a routing decision? Will it be based on device, port, destination, user, etc.? You must decide that before you can create a solution.

If you want a Split VPN, you will have to add a new routing table (probably more than one in this scenario), new routing rule policies, and iptables filters. How to do that is well beyond the scope of this post. My goal here is to clarify the difference between these goals. One must understand what they are trying to accomplish before proceeding. If you want a split VPN, google that term + Ubuntu or whatever your O.S. is. It is complicated to get it right. You need to fully understand your intentions/goals first though.

---

