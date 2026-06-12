---
title: "Can't get networking to work at all"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by numberboy on 2006-11-08
I decided to try out Ubuntu a few days back, since I've always been interested in using Linux and Ubuntu seems like a friendly way of doing it. However, I've had some trouble trying to get my home network connected.

I've got my network set up as a wireless network, connected to a broadband connection via a Netgear DG834G router. My computer connects to it via a wireless bridge (I used this because I've got XP Pro x64 and couldn't find any WLAN adapters with working drivers). It works brilliantly under Windows; the the WLAN is seen as a 100Mbps ethernet connection. The PC has two ethernet ports; an nForce4 SLI X16 port and a Marvell 88E8053 port, each built into the motherboard. The bridge is a Linksys WET54G ver. 3. The version of Ubuntu I used is 6.1 (the latest). It installed fine in a dual boot with Windows.

System>Administration>Networking reports two wired connections (eth1 and eth2). I'm not sure which of those the bridge is plugged into (it's plugged into first physical socket along the board). Both of them show ticks, and are set to DHCP. It also shows a modem connection that isn't enabled. I'm not getting a connection through either of them, though, and Firefox doesn't give me any webpages ('Server not found'). I did some searching on the problem, and although a lot of it is over my head, I did try restarting the networking by going into Terminal and entering 'sudo /etc/init.d/networking restart'. It seems to try getting DHCP data, but as far as I can tell it fails.

It shows 'DHCPDISCOVER on eth[1/2] to 255.255.255.255 port 67 interval #' (# being anywhere from 5 to 14) several times, and then 'No DHCPOFFERS recieved.
No working leases in persistent database - sleeping'.

I don't really know much about networking, but it seems like it's not seeing my router. For the record, the connection light on the ethernet port is continually lit and the transfer light blinks occasionally. I've got no idea how to fix this, and I'd really appreciate some help. Please keep in mind that I'm new to this OS, so I won't really understand specific technical stuff.

Any help would be appreciated,
thanks

edit - the router is at 192.168.1.1, and the computer is usually 192.168.1.4 under Windows. The router is set up for DHCP.

---

### Post by dmizer on 2006-11-08
well, since it's a wireless bridge, there shouldn't be anything special you need to do to configure things.  just plug it in and go.

post the output of ifconfig.

i suspect you're just going to have to disable the adapter that is not connected to the bridge.

---

### Post by numberboy on 2006-11-08
Okay, after fiddling around for a while, it seems to have given me an IP address. However, I have no idea how it happened, it's IPv6, and I still can't actually connect to the internet.

I've got two outputs from ifconfig. The first is when both ethernet connections are enabled:

```
eth0      Link encap:Ethernet  HWaddr 00:18:F3:29:2C:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:50 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:17:31:67:7D:7C  
          inet6 addr: fe80::217:31ff:fe67:7d7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:128 (128.0 b)  TX bytes:1876 (1.8 KiB)
          Interrupt:66 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

The second is when only the connection to the wireless bridge is enabled:
```
eth1      Link encap:Ethernet  HWaddr 00:17:31:67:7D:7C  
          inet6 addr: fe80::217:31ff:fe67:7d7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:128 (128.0 b)  TX bytes:4990 (4.8 KiB)
          Interrupt:66 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

I've also attached a screenshot of Network Settings since I thought I might be missing something there. It seems that the computer has been assigned an IP address, but every other machine on the network uses IPv4 addresses. The router address doesn't work, nor do the couple of internal Apache servers I've got running. Further, there's an icon for the 'lo' network in the top status bar, but no icon for my home network.

Again, any help would be appreciated,
thanks

---

### Post by lwoodtri on 2006-11-08
Greetings,

Looking at your ifconfig shows that a local loop address is assigned . . . (127.0.0.1) but there is no addr assigned to the eth1.  It appears that a DHCP request is going out since you have it set for Dhcp, but no offers are being returned to the requesting box.  If you are recieving an ip for you windows machine, I am to assume the dhcp server is working correctly.  so that leaves 2 things... either there are not enought ip addresses in the dhcp pool to be offered, or something on the ubuntu server is blocking the DHCP offer . .. is iptables / firewall running on the Ubuntu server?  I would begin looking down those 2 avenues.

cb

---

### Post by tedrogers on 2006-11-08
In my adventures with wireless on Ubuntu I've been told several times that you can't run Wired and Wireless connections at the same time.

If I was you, I'd go into my /etc/network/interfaces file and comment out your eth0 options completely. If you ever want to go back you can just uncomment then and restart.

I'm a beginner too so I hope this is accurate - I think I'm right here though. No harm in trying is there, especially if you make backup's.

I also find restarting networking very useful by running:

```
sudo /etc/init.d/networking restart
```

Hope this helps.

---

### Post by dmizer on 2006-11-08
i really have no idea why your bridge is assigning you an ipv6 ip address. i suppose i could speculate why, but that's not really an issue here.  obviously we need to get ipv6 turned off for you, or it's not going to work right.

so let me take a stab at telling you how to do this:

make a file called blacklist-ipv6 in /etc/modprobe.d/
```
gksudo gedit /etc/modprobe.d/blacklist-ipv6
```
enter the following line:
> blacklist ipv6
and make sure there is a blank line (enter) after this.  then save the file and exit.  reboot.  see if you can get connected then.

---

