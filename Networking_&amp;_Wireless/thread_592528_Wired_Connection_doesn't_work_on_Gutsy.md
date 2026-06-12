---
title: "Wired Connection doesn't work on Gutsy"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by vnetha on 2007-10-26
Hi,

I'm kind of a linux newbie.
I recently installed Gutsy on my old DELL OptiPlex GX280.
The installation went fine except for when I was all done, 
my wired internet connection doesn't work.

I have a NetXtreme BCM5751 Gigabit Ethernet PCI Express card.
The cable is plugged into my TrendNet wireless router. (TEW-432BRP)
I've also tried plugging the cable into the cable modem directly. It's an RCA DCM425.
Neither approach works. 

I initially had roaming enabled.
So I tried to manually configure things.
but that doesn't help either.

The connections (wireless and wired) work fine with my windows machines.
I'm attaching terminal responses to some common linux commands 
so you guys might see what I'm dealing with here.

I really want to give up Windows and switch over to linux completely.
Please help!


thanks,
Vivek.

---

### Post by anubhavrocks on 2007-10-26
Post outputs of 
cat /etc/network/interfaces
dmesg
ifconfig -a
route -n 
cat /etc/resolv.conf

---

### Post by vnetha on 2007-10-27
Hi Anubhav,

I have attached outputs to the commands you asked for...
The dmesg output was too big, so I had to split it up into 2 files.

I really appreciate your help.


thanks,
Vivek.

---

### Post by anubhavrocks on 2007-10-27
try this
```
sudo ifconfig  eth0 down
sudo modprobe -r tg3
sudo modprobe     tg3
sudo ifconfig eth0 up
sudo dhclient eth0
```

---

### Post by vnetha on 2007-10-28
Sorry, didn't seem to work...

```

vivek@vivek-desktop:~$ sudo ifconfig eth0 down
[sudo] password for vivek:
vivek@vivek-desktop:~$ sudo modprobe -r tg3
vivek@vivek-desktop:~$ sudo modprobe tg3
vivek@vivek-desktop:~$ sudo ifconfig eth0 up
vivek@vivek-desktop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
Listening on LPF/eth0/00:11:43:2f:fd:aa
Sending on LPF/eth0/00:11:43:2f:fd:aa
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

any other suggestions?
Vivek.

---

### Post by anubhavrocks on 2007-10-28
after the last step is complete can you post the output of 
```
ifconfig eth0
dmesg|tail
```

---

### Post by vnetha on 2007-10-28
Hi Anubhav,

I'm happy to report that the driver install did actually work.
I didn't realize that I was supposed to restart my computer after that.
Anyhow, everything looks good now. 

I can access internet just fine.
I'm writing this post on Gutsy.

Thanks for all your help.
I really appreciate it.

I just have to hit the multimedia configuration next.
and then, i'm really hoping I can get some virtualization going.


bye,
Vivek.

---

### Post by vnetha on 2007-10-28
Hi,

I think that last post was premature.
I've lost connectivity again.
All I did was install the flash plugin and restart.

The browser does behave a little differently.
before, it used to say immediately that there was no connectivity.
now, it takes quite a while trying to connect and then says the page can't be found.

i tried to reinstall the driver too.
here are those outputs again...

```

vivek@vivek-desktop:~$ sudo ifconfig eth0 down
[sudo] password for vivek:
vivek@vivek-desktop:~$ sudo modprobe -r tg3
vivek@vivek-desktop:~$ sudo modprobe tg3
vivek@vivek-desktop:~$ sudo ifconfig eth0 up
vivek@vivek-desktop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit F http://www.isc.org/sw/dhcp/
Listening on LPF/eth0/00:11:43:2f:fd:aa
Sending on LPF/eth0/00:11:43:2f:fd:aa
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
vivek@vivek-desktop:~$ ifconfig eth0
eth0 Link encap:Ethernet HWaddr 00:11:43:2F:FD:AA
inet6 addr: fe80::211:43ff:fe2f:fdaa/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:3 dropped:0 overruns:0 frame:52
TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:10316 (10.0 KB)
Interrupt:16
vivek@vivek-desktop:~$ dmesg|tail
[ 216.471887] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 216.471903] PCI: Setting latency timer of device 0000:02:00.0 to 64
[ 216.493116] eth0: Tigon3 [partno(BCM95751) rev 4001 PHY(5750)] (PCI Express) 10/100/1000Base-
T Ethernet 00:11:43:2f:fd:aa
[ 216.493130] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[ 216.493134] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[ 216.565126] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 233.656364] tg3: eth0: Link is up at 10 Mbps, full duplex.
[ 233.656369] tg3: eth0: Flow control is off for TX and off for RX.
[ 233.658694] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 243.786716] eth0: no IPv6 routers present
```

thanks, 
Vivek.

---

### Post by anubhavrocks on 2007-10-29
```
sudo ethtool -K eth0 rx off
```

---

### Post by vnetha on 2007-10-29
That didn't seem to change anything. I still can't connect.
Everything was fine for one brief blissful period yesterday.
I don't know what I did to mess things up!

any other commands I can try?
Vivek.

---

### Post by anubhavrocks on 2007-10-29
Whats the output of 
sudo ethtool -k eth0

---

### Post by vnetha on 2007-10-29
here we go...

```

vivek@vivek-desktop:~$ sudo ethtool -k eth0
[sudo] password for vivek:
Offload parameters for eth0:
Cannot get device udp large send offload settings: Operation not supported
rx-checksumming: on
tx-checksumming: on
scatter-gather: on
tcp segmentation offload: on
udp fragmentation offload: off
generic segmentation offload: off
```


thanks,
Vivek.

---

### Post by anubhavrocks on 2007-10-29
Oh so you did not use the command i told you to use previously,
```
sudo ethtool -K eth0 rx off
```
After doing this if you give this command 
```
sudo ethtool -k eth0
```

The response should show 
> 
rx-checksumming: off

If that is so do a 
```
sudo dhclient eth0 
```

---

### Post by immachargin on 2007-10-29
greetings all,
i have the very same problem with topic starter. my wired connection is OK with my windowsXP. what i mean here by OK is that i can surf internet, check email, IMing and so on. but when i boot with my gutsy, the wired connection failed to connect. the error returned by the browser is cannot find the server. i've check the info, all is exactly the same with my windowsXP. the IP, dns, dhcp, gateway all the same what i have in my winXP.

---

### Post by vnetha on 2007-10-29
Hi Abhinav,

I did run the command you gave me earlier,
but I had restarted my computer in-between.
Anywayz, here are the outputs...

```
vivek@vivek-desktop:~$ sudo ethtool -K eth0 rx off
[sudo] password for vivek:
vivek@vivek-desktop:~$ sudo ethtool -k eth0
Offload parameters for eth0:
Cannot get device udp large send offload settings: Operation not supported
rx-checksumming: off
tx-checksumming: on
scatter-gather: on
tcp segmentation offload: on
udp fragmentation offload: off
generic segmentation offload: off
vivek@vivek-desktop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit F http://www.isc.org/sw/dhcp/
Listening on LPF/eth0/00:11:43:2f:fd:aa
Sending on LPF/eth0/00:11:43:2f:fd:aa
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

still no luck!
Vivek.

---

### Post by anubhavrocks on 2007-10-30
What's the output of
```
sudo ethtool -t eth0
```

---

### Post by vnetha on 2007-10-30
```
vivek@v vivek-desktop:~$ sudo ethtool -t eth0
The test result is PASS
The test extra info:
nvram test (online) 0
link test (online) 0
register test (offline) 0
memory test (offline) 0
loopback test (offline) 0
interrupt test (offline) 0
```

---

### Post by vnetha on 2007-11-01
HELP! Anyone?

---

### Post by JasonMcKee on 2007-12-21
For what it's worth, I can confirm the same behavior on the same hardware (Optiplex GX280) running Fedora Core 8.  I can get out to the network with no problems if I assign a static IP address, but dhclient is unable to get an address.  And on the same network, I can get an IP with dhclient on a later Optiplex GX620 with the same driver/chipset (tg3/broadcom 5751).

---

