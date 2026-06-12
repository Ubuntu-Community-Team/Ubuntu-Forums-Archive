---
title: "connect: Network is unreachable"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by Atanvarno on 2008-05-31
I recently install ubuntu server 8.04, and all was working fine until I turned off the machine and moved it into another room (its new perminant home). After I did this network stopped working.

It had been working fine before, as I had used apt-get to grab some packages and pinged google, but now it doesn't and I am sure I haven't changed anything.

Pinging my router:
```
$ ping 192.168.1.1
connect: Network is unreachable
```

My /etc/network/interfaces file:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```
sudo /etc/init.d/networking restart gives me ```
 * Reconfiguring network interfaces...
There is already a pid file /var/run/dhclient.eth0.pid with pid 5209
killed old client process, removed PID file
Internet Systens Consortium DCHP Client V3.0.6
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp

Listening on LPF/eth0/00:1d:92:2e:ff:19
Sending on LPF/eth0/00:1d:92:2e:ff:19
Sending on Socket/fallback
There is already a PID file /var/run/dhclient.eth0.pid with pid 13519072

Internet Systens Consortium DCHP Client V3.0.6
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp

Listening on LPF/eth0/00:1d:92:2e:ff:19
Sending on LPF/eth0/00:1d:92:2e:ff:19
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I am at a total loss, and I don't understand why it was working before and now doesn't?

---

### Post by prshah on 2008-05-31
> **Atanvarno said:**
> 
Listening on LPF/eth0/00:1d:92:2e:ff:19
Sending on LPF/eth0/00:1d:92:2e:ff:19

Listening on LPF/eth0/00:1d:92:2e:ff:19
Sending on LPF/eth0/00:1d:92:2e:ff:19


These are ipv6 addresses! Maybe you should blacklist ipv6 ; add the following line to the end of your "/etc/modprobe.d/blacklist" file:```

blacklist ipv6
``` then restart and see if it works? If it still doesn't can you post outputs of```

ifconfig
sudo mii-tool eth0
```

---

### Post by Atanvarno on 2008-05-31
Thanks for the reply!

Blacklisting ivp6 didn't work.

ifconfig:
```
eth0 Link encap:Ethernet HWaddr 00:1d:92:2e:ff:19
     inet6 addr: fe80::21d:92ff:fe2e:ff19/64 Scope:Link
     UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000
     RX bytes:0 (0.0 B)  TX bytes:2178 (2.1 KB)
     Interrupt:220 Base addess:0xa000

lo   Link encap:Local Loopback
     inet addr:127.0.0.1 Mask 255.0.0.0
     inet6 addr: ::1/128 Scope:Host
     UP LOOP RUNNING MTU:16436 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:0
     RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)
```
sudo mii-tool eth0:
```
eth0: negotiated 100baseTx-FD flow-control, link ok
```

---

### Post by prshah on 2008-05-31
> **Atanvarno said:**
> Thanks for the reply!

Blacklisting ivp6 didn't work.

ifconfig:
```
eth0 Link encap:Ethernet HWaddr 00:1d:92:2e:ff:19
[color=red]     inet6 addr: fe80::21d:92ff:fe2e:ff19/64[/color] Scope:Link

```


I think you've made some mistake in the blacklist process; it's still serving ipv6 addresses. Did you restart (the system)? Can you post your /etc/modprobe.d/blacklist file?

---

### Post by Atanvarno on 2008-05-31
> **prshah said:**
> I think you've made some mistake in the blacklist process; it's still serving ipv6 addresses. Did you restart (the system)? Can you post your /etc/modprobe.d/blacklist file?
You're right, for some reason I added the line to /etc/modules, by mistake. I returned /etc/modules to how it was before and edited /etc/modprobe.d/blacklist. It now looks like this:
```
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1349
blacklist snd_intel8x0m
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist ipv6
```

ifconfig is now:
```
eth0 Link encap:Ethernet HWaddr 00:1d:92:2e:ff:19
     UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000
     RX bytes:0 (0.0 B)  TX bytes:2178 (2.1 KB)
     Interrupt:220 Base addess:0xa000

lo   Link encap:Local Loopback
     inet addr:127.0.0.1 Mask 255.0.0.0
     UP LOOP RUNNING MTU:16436 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:0
     RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)
```
sudo mii-tool eth0 is now:```
negotiated 100baseTx-FD flow-control, link ok
```

Edit: I've now looked at the list of attached devices in the router, and the server isn't there. I've tried changing the network cable attaching the two, but nothing. Is this maybe a problem with the router?

---

### Post by Iowan on 2008-05-31
I don't suppose there's an uplink port on the router that you're plugged into... Did you try other ports (besides cables)?

---

### Post by prshah on 2008-06-01
> **Atanvarno said:**
> You're right, for some reason I added the line to /etc/modules, by mistake.
ifconfig is now:
```
eth0 Link encap:Ethernet HWaddr 00:1d:92:2e:ff:19
     UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000
     RX bytes:0 (0.0 B)  TX bytes:2178 (2.1 KB)
     Interrupt:220 Base addess:0xa000

```


The mistake is mine! I originally wrote /etc/modules, then (within a couple of minutes) edited it to read "/etc/modpro..."! I didn't think that you'd have reacted so fast to my initial post!

Now Step 2: Your eth0 looks good. With the router active, give the terminal command ```

sudo dhclient eth0
``` and post back output.

---

### Post by Atanvarno on 2008-06-01
> I don't suppose there's an uplink port on the router that you're plugged into... Did you try other ports (besides cables)? There's a WAN port, which the cable modem is pluged into (taped into, actually as the cable lacks a clip) and four network ports - I've tried the server in each network port.

I can't try wireless as I don't have a spare wireless card.

sudo dhclient eth0:```
There is already a id file /var/run/dhclieent.pid with pid 8193
killedold client process, removed PID file.
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1d:92:2e:ff:19
Sending on   LPF/eth0/00:1d:92:2e:ff:19
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```
I also tried plugging it into a different router (a spare ADSL one that is not connected to the net), and it got an IP address from it fine, which makes me think its the cable router, only the cable router hands out IPs to every other device in the house.

I much appricate all your help.

---

### Post by prshah on 2008-06-01
> **Atanvarno said:**
> which makes me think its the cable router, only the cable router hands out IPs to every other device in the house.


Can you check network config on the other devices and post back suitable output from those? (If windows machines, use "ipconfig /all" instead of ifconfig)

---

### Post by bruban on 2008-06-03
I'm having the same problem.

New install of Ubuntu 8.04 on a Dell XPS M1530 laptop. Networking was OK several days ago, but not OK today.

My topology is laptop > Debian Gateway (DNS, DHCP, IPv4) > switch > firewall > router

On the same network segment, another desktop pc also running 8.04 is working OK.

On the same network cable, another laptop worked fine, same config.


The problem appears to be intermittent on this XPS M1530 laptop.


mii-tool reports that the eth0 link is OK.

dhclient cannot find any DHCPOFFERS from the Debian server (though other PCs can).

I've also blacklisted IPv6 on the laptop, without fixing the problem.


In my initial troubleshooting, I've found that the laptop can see a wireless network external to my network. Perhaps this is taking precedence and stopping wired network connectivity?

---

### Post by Atanvarno on 2008-06-07
> **prshah said:**
> Can you check network config on the other devices and post back suitable output from those? (If windows machines, use "ipconfig /all" instead of ifconfig)
ipconfig /all from the windows laptop:
```
Windows IP Configuration

        Host Name . . . . . . . . . . . . : Laptop
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Intel(R) PRO/Wireless 2200BG Network
 Connection
        Physical Address. . . . . . . . . : 00-13-CE-CA-2B-E9
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.3
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
        Lease Obtained. . . . . . . . . . : 07 June 2008 16:39:41
        Lease Expires . . . . . . . . . . : 08 June 2008 16:39:29

Ethernet adapter Local Area Connection 2:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Broadcom NetLink (TM) Gigabit Ethern
et
        Physical Address. . . . . . . . . : 00-14-2A-3E-F8-55
```

I tried giving myself a static IP using this /etc/network/interfaces:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.20
netmask 255.255.255.0
gateway 192.168.1.1
```and then it came up in the router's attached devices list (not showing a device name, though) showing the correct MAC address. However, when I ping the router I get:```
server@beowulf:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data
From 192.168.1.20 imcp_seq=1 Destination Host Unreachable
From 192.168.1.20 imcp_seq=2 Destination Host Unreachable
From 192.168.1.20 imcp_seq=5 Destination Host Unreachable
From 192.168.1.20 imcp_seq=6 Destination Host Unreachable
From 192.168.1.20 imcp_seq=9 Destination Host Unreachable
From 192.168.1.20 imcp_seq=10 Destination Host Unreachable
From 192.168.1.20 imcp_seq=12 Destination Host Unreachable
From 192.168.1.20 imcp_seq=13 Destination Host Unreachable
From 192.168.1.20 imcp_seq=14 Destination Host Unreachable
From 192.168.1.20 imcp_seq=15 Destination Host Unreachable
From 192.168.1.20 imcp_seq=16 Destination Host Unreachable
From 192.168.1.20 imcp_seq=17 Destination Host Unreachable
From 192.168.1.20 imcp_seq=20 Destination Host Unreachable
From 192.168.1.20 imcp_seq=21 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
23 packets transmitted, 0 received, +14 errors, 100% packet loss, time 22006ms, pipe 3
```

---

### Post by Atanvarno on 2008-06-07
Double post

---

### Post by Wolfhere on 2008-10-10
Prshah. You are awesome :guitar: I am still pretty new to Linux...Ubuntu is my preferred. Because of people like you. I had installed to my Dell laptop, with no issue. But then I went to a show, and entered a drawing. I won a NOBi. Not enough ram to run the WindowsXP that came with it..but no productivity software. Yes, I know, its a toy. So I figured to install Ubuntu. The wireless never did work. The long and short is..I did not know where to start. Your steps helped me eliminate everything but the encryption key. For now, mac filtering is enough. Now I have to find the issue with encryption. There are always too many characters in the manual configuration when I go back in and look at it. Is there some file I can edit to manually enter the key so that the config does not lose it?

Thanks again dude. You know your s...tuff

---

### Post by bobyy on 2008-10-10
mystake

---

