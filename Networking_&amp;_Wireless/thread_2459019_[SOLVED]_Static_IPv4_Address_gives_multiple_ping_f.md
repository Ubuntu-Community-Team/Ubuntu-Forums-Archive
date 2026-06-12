---
title: "[SOLVED] Static IPv4 Address gives multiple ping failures"
date: 2021-03-08
forum: Networking &amp; Wireless
---

### Post by germarsh on 2021-03-08
Hello forum attendees!

Although new to Ubuntu I have been delving into Unix for a while on Raspberry Pi's but am now stuck! I have many years experience in IT support although not a network specialist - usually on OpenVMS. However, all that experience counts for nothing at the moment!

Due to utter frustration with Windows 10, I decided to wipe the drive and install Ubuntu from scratch on my Samsung laptop. (File Explorer crashed around 50% of the time I used it. Samsung stated that the model - NP350E7C - is not compatible with Win 10. I asked why on earth did it volunteer for the upgrade then!

I have been quite impressed with how easy it was to install and that it utilised an additional monitor without any intervention. I quickly got to grips with the GUI and the overall response speed is impressive.

I am hoping to use it as a testbed for web technologies so installed the LAMP stack - again without any issue.

To ease access from the LAN, I followed instructions on setting up a static IP address - also, I wanted the quickest network response from it so connected it via Ethernet cable into the router. I soon noticed that Firefox was timing out on websites. Pings showed that some were actually working but there was about 85% failure rate. I also noticed that the speed of the link was varying from 1Gb to 1Mb within a few seconds.

Hours of investigation including swapping cables and the like made me realise that the problem was with the static IP address as the same issue occurs on the wireless interface too. I noted that, although I attempted to disable the IPv6 address in the settings the interface would still obtain an IPv6 address. The router recognises it as a "Link Local" address even though I did not set that up either.

I have had to set the interface to DHCP for the link to be stable.

I have searched these forums as best as I can but can see nothing which resembles what I am seeing. I have downloaded the wireless diagnostic script so will switch back to wireless tomorrow and see if setting the static address will give any useful info.

I can understand that there can be many problems with proprietary drivers and the like but I would just like to state that I am impressed with the technical and diplomatic skills of many contributors on these forums! Thank you from an old but still enthusiastic techie.

---

### Post by chili555 on 2021-03-08
With a DHCP connection, please run and post:

```
ip addr show
```What static address did you set? What DNS nameserver(s)?

A link-local IPv6 address; typically fe80::xxxx is normal and entirely expected.

---

### Post by germarsh on 2021-03-09
Thank you very much for the quick response. I have configured the router only to allocate addresses from 192.168.0.125 and I attempted to set the static address of .65. In the Settings I put 24 as the mask - which I noted was translated to the ip address format - and the address of the router as the gateway and the single nameserver: 192.168.0.1

Here is the output from the command:

```
gerald@Linux-Laptop:~$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether b8:88:e3:6a:5c:09 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.181/24 brd 192.168.0.255 scope global dynamic noprefixroute enp2s0
       valid_lft 568064sec preferred_lft 568064sec
    inet6 fe80::fabe:e358:f9dd:e235/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp3s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 50:b7:c3:4e:2f:c6 brd ff:ff:ff:ff:ff:ff

```

---

### Post by germarsh on 2021-03-09
The router has an option to always allocate the IP address to that link and I am thinking of using that. It should be fairly simple to set up a static address though - so I thought!

I note too that there seem to be different "network managers" involved in the command line configs. Some configuration files suggested on line do not exist on my system. I get a 01-network-manager-all.yaml in /etc/netplan where one suggestion was to modify a different file. (I know the yaml format as I run Home Assistant on Raspberry Pi which uses it extensively.)

---

### Post by chili555 on 2021-03-09
> **germarsh said:**
> The router has an option to always allocate the IP address to that link and I am thinking of using that. It should be fairly simple to set up a static address though - so I thought!

I note too that there seem to be different "network managers" involved in the command line configs. Some configuration files suggested on line do not exist on my system. I get a 01-network-manager-all.yaml in /etc/netplan where one suggestion was to modify a different file. (I know the yaml format as I run Home Assistant on Raspberry Pi which uses it extensively.)If Network Manager is running, then please do not adjust netplan. Is it?

```
sudo service NetworkManager status

```If so, then make your changes there: [IMG]https://i.postimg.cc/Vk8FQG9z/Screenshot-from-2021-03-09-09-23-29.png[/IMG]

Substitute your details, of course. Restart NM:

```
sudo service NetworkManager restart

```Check to see if you got the requested address:

```
ip addr show
ping -c3 www.ubuntu.com
```

---

### Post by germarsh on 2021-03-09
The only difference I made to the manual settings was that I used the address of the router to be the single DNS. I shall try as you say.

Here is the output of the service status:

```
&#9679; NetworkManager.service - Network Manager
     Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendo>
     Active: active (running) since Mon 2021-03-08 22:46:10 GMT; 20h ago
       Docs: man:NetworkManager(8)
   Main PID: 738 (NetworkManager)
      Tasks: 3 (limit: 9354)
     Memory: 16.0M
     CGroup: /system.slice/NetworkManager.service
             &#9492;&#9472;738 /usr/sbin/NetworkManager --no-daemon

Mar 09 12:47:42 Linux-Laptop NetworkManager[738]: <info>  [1615294062.1881] age>
Mar 09 13:14:25 Linux-Laptop NetworkManager[738]: <info>  [1615295665.0359] age>
Mar 09 13:30:40 Linux-Laptop NetworkManager[738]: <info>  [1615296640.3489] age>
Mar 09 13:36:37 Linux-Laptop NetworkManager[738]: <info>  [1615296997.3517] age>
Mar 09 15:22:39 Linux-Laptop NetworkManager[738]: <info>  [1615303359.0723] age>
Mar 09 15:33:33 Linux-Laptop NetworkManager[738]: <info>  [1615304013.9088] age>
Mar 09 16:04:55 Linux-Laptop NetworkManager[738]: <info>  [1615305895.1643] age>
Mar 09 18:27:19 Linux-Laptop NetworkManager[738]: <info>  [1615314439.2252] age>
Mar 09 19:19:31 Linux-Laptop NetworkManager[738]: <info>  [1615317571.8214] age>
Mar 09 19:33:02 Linux-Laptop NetworkManager[738]: <info>  [1615318382.0179] age>
lines 1-20/20 (END)


```

---

### Post by germarsh on 2021-03-09
The service restarted ok and the pings were successful but this looks like it has not picked up the manual address:

```
gerald@Linux-Laptop:/var/www$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether b8:88:e3:6a:5c:09 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.181/24 brd 192.168.0.255 scope global dynamic noprefixroute enp2s0
       valid_lft 529329sec preferred_lft 529329sec
    inet6 fe80::fabe:e358:f9dd:e235/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp3s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 50:b7:c3:4e:2f:c6 brd ff:ff:ff:ff:ff:ff


```

---

### Post by germarsh on 2021-03-09
I have just checked the Wired setting and find that all fields and tags are greyed out.

Not seen that before!

---

### Post by germarsh on 2021-03-09
Switched off the wired connection and switched it on again. Still greyed out. (Except the Cancel button.)

Now the address is correct though!...

(Network died when it picked up the manual address - I think the setup was greyed out as there was another running. Now set it back to DHCP so I can post this. 

Just discovered that ip addr show gives a different address to ifconfig...

```
gerald@Linux-Laptop:/var/www$ ifconfig
enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.181  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::fabe:e358:f9dd:e235  prefixlen 64  scopeid 0x20<link>
        ether b8:88:e3:6a:5c:09  txqueuelen 1000  (Ethernet)
        RX packets 411052  bytes 147040222 (147.0 MB)
        RX errors 0  dropped 26550  overruns 0  frame 0
        TX packets 76660  bytes 9056279 (9.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 11087  bytes 1207119 (1.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 11087  bytes 1207119 (1.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

gerald@Linux-Laptop:/var/www$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether b8:88:e3:6a:5c:09 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.181/24 brd 192.168.0.255 scope global dynamic noprefixroute enp2s0
       valid_lft 604713sec preferred_lft 604713sec
    inet 192.168.0.65/24 brd 192.168.0.255 scope global secondary noprefixroute enp2s0
       valid_lft forever preferred_lft forever
    inet6 fe80::fabe:e358:f9dd:e235/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp3s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 50:b7:c3:4e:2f:c6 brd ff:ff:ff:ff:ff:ff


```

---

### Post by germarsh on 2021-03-09
OK - Now I am really confused! Firefox is working as are pings to [www.ubuntu.com]("http://www.ubuntu.com") but pinging 192.168.0.1 fails!...

```
erald@Linux-Laptop:/var/www$ ping -c3 www.ubuntu.com
PING www.ubuntu.com (91.189.91.45) 56(84) bytes of data.
64 bytes from fautso.canonical.com (91.189.91.45): icmp_seq=1 ttl=53 time=86.6 ms
64 bytes from fautso.canonical.com (91.189.91.45): icmp_seq=2 ttl=53 time=93.8 ms
64 bytes from fautso.canonical.com (91.189.91.45): icmp_seq=3 ttl=53 time=86.1 ms

--- www.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2004ms
rtt min/avg/max/mdev = 86.108/88.840/93.846/3.544 ms
gerald@Linux-Laptop:/var/www$ ping -c3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2037ms

gerald@Linux-Laptop:/var/www$ 


```

---

### Post by germarsh on 2021-03-09
I note that the service status reports the change back to default...
```
nager: NetworkManager state is now CONNECTED_LOCAL
nager: NetworkManager state is now CONNECTED_SITE
licy: set 'Wired connection 1' (enp2s0) as default for IPv4 routing and DNS
vice (enp2s0): Activation: successful, device activated.
nager: startup complete
nager: NetworkManager state is now CONNECTED_GLOBAL
cp6 (enp2s0): request timed out
cp6 (enp2s0): state changed unknown -> timeout
cp6 (enp2s0): canceled DHCP transaction
cp6 (enp2s0): state changed timeout -> done
~

```

I've also just noticed that the ip addr show command shows it has the two addresses...
```
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether b8:88:e3:6a:5c:09 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.181/24 brd 192.168.0.255 scope global dynamic noprefixroute enp2s0
       valid_lft 603531sec preferred_lft 603531sec
    inet 192.168.0.65/24 brd 192.168.0.255 scope global secondary noprefixroute enp2s0
       valid_lft forever preferred_lft forever
    inet6 fe80::fabe:e358:f9dd:e235/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp3s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 50:b7:c3:4e:2f:c6 brd ff:ff:ff:ff:ff:ff

```

And here is another mystery. I cannot ping the router from it but I can ping another router (just being used as a hub) on the LAN. It can also see my PC and the pc successfully pings it as 192.128.0.65!

In my decades of IT support work at various levels, I have always considered networks to be a black art but this is a cracker!

I shall leave the laptop for a while to see if something settles.

---

### Post by chili555 on 2021-03-09
Let's be certain that there are no other conflicting configurations here. Please post:

```
cat /etc/netplan/*.yaml
cat /etc/network/interfaces
```

---

### Post by germarsh on 2021-03-09
Tried to give an update on what I have done but the internet link has died (this entered on PC).

I shall try the commands. (Thanks very much for your assistance on this. I would be stuck otherwise!)
I'll get it working again using DHCP then post the output.

---

### Post by germarsh on 2021-03-09
Back on DHCP now. Here's the output...
```
gerald@Linux-Laptop:/var/www$ cat /etc/netplan/*.yaml
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
gerald@Linux-Laptop:/var/www$ cat /etc/network/interfaces
cat: /etc/network/interfaces: No such file or directory

```

And here was the ping attempt under manual...

```
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.799 ms

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 1 received, 66.6667% packet loss, time 2043ms
rtt min/avg/max/mdev = 0.799/0.799/0.799/0.000 ms
```

---

### Post by germarsh on 2021-03-09
Yep - the system currently possesses two addresses! I can access Apache on them from my PC.
```
gerald@Linux-Laptop:~/Downloads/piwigo-11.3.0/piwigo$ ip address show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether b8:88:e3:6a:5c:09 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.181/24 brd 192.168.0.255 scope global dynamic noprefixroute enp2s0
       valid_lft 601043sec preferred_lft 601043sec
    inet 192.168.0.65/24 brd 192.168.0.255 scope global secondary noprefixroute enp2s0
       valid_lft forever preferred_lft forever
    inet6 fe80::fabe:e358:f9dd:e235/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp3s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 50:b7:c3:4e:2f:c6 brd ff:ff:ff:ff:ff:ff
gerald@Linux-Laptop:~/Downloads/piwigo-11.3.0/piwigo$ ifconfig
enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.181  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::fabe:e358:f9dd:e235  prefixlen 64  scopeid 0x20<link>
        ether b8:88:e3:6a:5c:09  txqueuelen 1000  (Ethernet)
        RX packets 476522  bytes 169330660 (169.3 MB)
        RX errors 0  dropped 29938  overruns 0  frame 0
        TX packets 93663  bytes 11342280 (11.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 16260  bytes 2624205 (2.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 16260  bytes 2624205 (2.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


```

Thank you for your help again, chili555, I shall have another go tomorrow.

---

### Post by germarsh on 2021-03-10
I suspended the system overnight and that has removed the static address...

```
gerald@Linux-Laptop:~/Downloads/piwigo-11.3.0/piwigo$ ip address show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether b8:88:e3:6a:5c:09 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.181/24 brd 192.168.0.255 scope global dynamic noprefixroute enp2s0
       valid_lft 604644sec preferred_lft 604644sec
    inet6 fe80::fabe:e358:f9dd:e235/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp3s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 50:b7:c3:4e:2f:c6 brd ff:ff:ff:ff:ff:ff


```

---

### Post by chili555 on 2021-03-10
> The router has an option to always allocate the IP address to that link and I am thinking of using that. It should be fairly simple to set up a static address though - so I thought!Please double-check the settings in the router. Be certain that there are no existing allocations; that the DHCP pool only is set to x.125 to x.253 and thare are no other impediments to static IP addresses in the x.65 neighborhood. I also suggest power-cycling the router.

---

### Post by germarsh on 2021-03-10
I have quite a few static IP addresses - cameras and Raspberry Pi's. The  router's DHCP address range is from .121 to .240 - is there any  particular reason you mentioned from .125? I have rebooted the router  but that made no difference. IPv6 is disabled on the router - if that is  of any concern.

I have given the link a bit of a hammering on  its .181 allotted address and there are no issues with it. It is strange  how this occurs with wired and wireless access too. I set up the cable  link so I could rule out WiFi hassle.

I have downloaded Wireshark in an attempt to determine what is happening. I shall give it a go.

---

### Post by germarsh on 2021-03-10
There is nothing even adjacent to .65 but strange how the device is shown twice. I have my doubts about the s/w in domestic routers!

[ATTACH=CONFIG]288088[/ATTACH]

---

### Post by chili555 on 2021-03-10
> The router's DHCP address range is from .121 to .240 - is there any particular reason you mentioned from .125? Because that's what you said in post #3:

> I have configured the router only to allocate addresses from 192.168.0.**125** 

---

### Post by germarsh on 2021-03-10
Oops - Sorry. I meant .121

I am now wondering if I can get the router to leave the laptop at 181 and reduce the DHCP entries to a max of 180. The router does have an option to allocate that address permanently. I suspect it matches it to the MAC address. I shall look into it. No other router we have had did that. And we have had a lot of them! We tend to change ISP every few years and along comes another router. Also, if you have a broadband issue here, they tend to send you yet another router!

I have a box full of the damn things down the shed but some are locked down so tightly you are restricted what you can do.

---

### Post by chili555 on 2021-03-10
> The router does have an option to allocate that address permanently. I suspect it matches it to the MAC address.That's exactly how it is supposed to work. Have you checked the allocation table to see that there is *no* listing involving the MAC address of your ethernet device?

I assume that there is no intervening network device between the Ubuntu computer and the router; that is no, for instance, dumb switch.

> some are locked down so tightly you are restricted what you can do.I have one of those now. It feeds but one device via ethernet, my own wireless router that I selected because I can manipulate everything I need and want to control.

---

### Post by germarsh on 2021-03-11
I am beginning to think that the router is playing up big time. My son and I were both on a Zoom meeting for our local camera club. He connects to an extender and I am connected to the router. His link died a death for about 10 mins. I bounced the extender to no avail. I was still on the router and Zoom was ok. I looked at the router connections and the extender had two IP addresses - on static and the other DHCP. Then the router dropped the broadband link. Second time today. We are going to contact the ISP tomorrow to report it but I cannot rule out influences of my rather complex setup!

(I tried the usual test with manual setup and ping. Same symptoms. Ping works for a while then times out for ages then may work. About 90% failures.)

I am really considering whether to use my other router - which had suspect issues - as the main one and swap. In the meantime I shall continue with DHCP as even Wireshark crash!

Thanks for your help. I shall keep you informed but I suspect that this is not a Linux issue. (Although my technical curiosity drives me to get to the bottom of why this laptop has the problem with the static address whereas Raspberry Pi's and my Win10 pc does not.

---

### Post by germarsh on 2021-03-13
Yep - this was all my silly fault, although not helped by the naff reporting capabilities of our router!

(I tried to include a screenshot of the router's device list but the submission resulted in some missing security token problem.)

The router showed three entries for the .65 address - all for the same MAC, that of the Ubuntu system.

However, Wireshark on the system revealed the damning evidence:

```
Frame 93: 60 bytes on wire (480 bits), 60 bytes captured (480 bits) on  interface enp2s0, id 0 
Ethernet II, Src: _gateway (04:a2:22:2d:61:12), Dst: Linux-Laptop.local  (b8:88:e3:6a:5c:09) 
Address Resolution Protocol (reply) 
[Duplicate IP address detected for 192.168.0.65 (b8:88:e3:6a:5c:09) -  also in use by 02:0f:b5:fe:4b:ab (frame 72)] 
    [Frame showing earlier use of IP address: 72] 
    [Seconds since earlier frame seen: 9]
```

In other words, I had a choice of about 120 addresses reserved for static addressing and I allocated the same address to the laptop as I had some five years earlier to a television! That explains the strange behaviour in the evening too. It was only a problem when the TV was on!

My grateful thanks and profound apologies goes out to all who helped and especially chili555.

As expected, the Ubuntu system is working perfectly. I look forward to learning more about it!

---

