---
title: "Still no clue about Relakks?"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by toxin on 2007-10-28
Did somebody manage to have Relakks working on Gutsy?
I'm trying since Festy but no way.

---

### Post by dburnett77 on 2007-10-29
This site may prove of sum ***-issthfthunce:

[http://www.sharemywifi.com/relakks/](http://www.sharemywifi.com/relakks/)

---

### Post by PartisanEntity on 2007-10-31
I have been using Relakks since Feisty:
[http://www.cognitivecombine.com/?p=134](http://www.cognitivecombine.com/?p=134)

---

### Post by toxin on 2007-11-01
Hi guys, thank you for your answers.

**@dburnett77** I know that site, but it doesn't seem to be anyhow related to linux :confused:

**@PartisanEntity** I tried network-manager-pptp already and didn't work. Maybe the point is that I didn't install vpnc and network-manager-vpnc. They shouldn't be required in theory, but there's maybe a bug or something in nm. Actually I had an entry called Relakks in Network Manager, but it wasn't selectable.
My subscribtion to Relakks has now expired,  but I'm going to renew it these days and try with those packages.

---

### Post by PartisanEntity on 2007-11-01
If you are using a laptop, try connecting to Relakks when wired. I can't connect to Relakks through wireless, but its working through wired, still trying to figure out why.

---

### Post by toxin on 2007-11-01
No, I'm using a desktop computer. Another issue may be that I have an USB modem with Conexant chipset, not an ethernet one. BTW, perhaps installing vpn could be the solution. I'll let you know.

Thanks.

---

### Post by kd7swh on 2007-11-06
if you want pptp vpn to work with your wireless in gusty you have to change your wifi card to eth0

(see my post [http://ubuntuforums.org/showthread.php?p=3714728#post3714728](http://ubuntuforums.org/showthread.php?p=3714728#post3714728))

---

### Post by toxin on 2007-12-23
Ok I finally renewed my Relakks subscription and tried again.
I couldn't have network-manager work as I'm connecting to the internet through an USB modem via pppoa and, as I understand, nm lets you connect to a VPN only if you have eth0 active.
I managed to configure kvpn instead, but still have problems. I can't tell if the problems are route related or pptp related.
I connect to my provider via ppp0 and get these IPs:

```
Dec 23 12:54:39 blackop pppd[11149]: local  IP address 151.50.63.18
Dec 23 12:54:39 blackop pppd[11149]: remote IP address 151.6.148.72
Dec 23 12:54:39 blackop pppd[11149]: primary   DNS address 193.70.152.15
Dec 23 12:54:39 blackop pppd[11149]: secondary DNS address 193.70.152.25
```

With this routing table:

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
151.6.148.72    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```

Then I connect to Relakks and get these IPs:

```
Dec 23 12:56:12 blackop pppd[11283]: MPPE 128-bit stateless compression enabled
Dec 23 12:56:12 blackop pppd[11283]: local  IP address 83.233.183.110
Dec 23 12:56:12 blackop pppd[11283]: remote IP address 83.233.183.2
Dec 23 12:56:12 blackop pppd[11283]: primary   DNS address 82.209.169.71
Dec 23 12:56:12 blackop pppd[11283]: secondary DNS address 82.209.169.72

```

With this routing table:

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
83.233.183.2    0.0.0.0         255.255.255.255 UH    0      0        0 ppp1
151.6.148.72    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
```

Which, as I understad, is bogus. So I set the following routing table:

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
83.233.183.2    151.6.148.72    255.255.255.255 UGH   0      0        0 ppp0
151.6.148.72    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp1 
```

But now I get a bunch of error messages in the log:

```
Dec 23 12:57:21 blackop pppd[11283]: Protocol-Reject for unsupported protocol 'Ascom Timeplex' (0x43)
Dec 23 12:57:21 blackop pppd[11283]: Protocol-Reject for unsupported protocol 0xa07d
Dec 23 12:57:22 blackop pppd[11283]: Protocol-Reject for unsupported protocol 0x81
Dec 23 12:57:22 blackop pppd[11283]: Protocol-Reject for unsupported protocol 0x9ec1
Dec 23 12:57:22 blackop pppd[11283]: Protocol-Reject for unsupported protocol 0x79
Dec 23 12:57:23 blackop pppd[11283]: Protocol-Reject for unsupported protocol 0x87
Dec 23 12:57:24 blackop pppd[11283]: Protocol-Reject for unsupported protocol 0x1e12
```

etc. etc.

Pinging 83.233.183.2 works, so the link to the Relakks gateway through ppp0 works. But i can't reach any other IP.

Has anybody a clue about this deal? Am I missing something about that route or is pptp that doesn't work properly due to those Protocol-Reject issues?

Thanks.

---

### Post by kd7swh on 2007-12-26
it could be a firewall issue. is there a router or something else in the way?

---

### Post by toxin on 2007-12-26
> **kd7swh said:**
> it could be a firewall issue. is there a router or something else in the way?

Hi kd7swh, thank you for your reply. No, I haven't got any router on the way. Furthermore, iptables is blank. Relakks is driving me crazy :(

---

### Post by kd7swh on 2007-12-28
if the ping works and you don't have a firewall in the way. I don't know what it could be. Have you made any changes to  ```
/etc/hosts
```?

---

### Post by toxin on 2007-12-30
No change to /etc/hosts.
I only move /etc/ppp/resolv.conf (created by pptp) to /etc/resolv.conf in order to use Relakks DNS.

But what about the routing table I posted above? Is it right?

---

### Post by Convert on 2008-01-03
I know that part of the problem is that network-manager-pptp does not get installed when the VPN PPTP plugin is installed.  I manually added network-manager-pptp via the Synaptic Package Manager and now my vpn connection to Relakks is working with the wireless card.

Specifically, I have the following installed:

Via Synaptic Package Manager
pptp-linux
network-manager-pptp

Via Application Add/Remove:
VPN Connection Manager (PPP Generic)

If it makes a difference (and it probably does), I have an Intel ABG wireless card on wlan0 and the wired ethernet port is active on eth0 (although no cable is connected).  Also, the default settings for pptp in the Configure VPN dialog worked fine for me.

And I also have the Cisco network-manager-vpnc, vpnc, and VPN Connection Manager (vpnc) installed, although I seriously doubt this affects the ability to do a pptp connection.

---

