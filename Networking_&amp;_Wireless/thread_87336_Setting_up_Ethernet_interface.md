---
title: "Setting up Ethernet interface"
date: 2005-11-07
forum: Networking &amp; Wireless
---

### Post by awood on 2005-11-07
Hello,
I am new to Ubuntu (as well as linux).  I recently installed Ubuntu on my good old P3 500Mhz PC.  During the installation, I received an error along the lines of Network initialization or DHCP Failed.

After the installation, I went to System->Administration->Networking and activated the ethernet connection.  Additionally, under the ethernet connection properties, I set my connection configuration to use DHCP.  My problem remains, I still cannot connect to the internet.  I would imagine that this has something to do with obtaining an IP from my router (which works fine on my Windows machines).

How does one go about getting an ip address(from the command prompt preferably)?  I tried "sudo dhclient eht0", but received the following output:

```

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
...
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

One thing I notices is that on my Windows machines, the subnet mask is 255.255.255.0.  Perhaps I am polling the wrong subnet mask address?  If so, how does one set this?

---

### Post by mlomker on 2005-11-07
That's the right command for requesting an address.  You might have a driver problem.

**lspci** will tell you what your card is.  **lsmod** will show you the loaded drivers.  **dmesg | less** will allow you to page through the error log.

---

### Post by bcavagnolo on 2005-11-07
I'm having a similar problem that you may be able to help me with.  I normally use my wireless card which comes up automatically as eth0 and works just fine.  Sometimes my built-in Intel ethernet adaptor comes up as eth1, and sometimes it doesn't.  When it comes up automatically, it appears when I "lspci" and I see the e100 driver when I "lsmod | grep e100."  When it doesn't come up (i.e., whenever I need it:), it doesn't show up in lspci.  However, if I "modprobe e100" I get the following lines in the log file:

Nov  7 19:10:48 localhost kernel: [4295372.610000] e100: Intel(R) PRO/100 Network Driver, 3.4.8-k2-NAPI
Nov  7 19:10:48 localhost kernel: [4295372.610000] e100: Copyright(c) 1999-2005 Intel Corporation

but still lspci doesn't pick it up.  In what seem to be log entries in which the e100 successfully detects the Intel hardware and maps it to eth1, I see the following:

Nov  7 06:52:40 localhost kernel: [4294677.280000] e100: Intel(R) PRO/100 Network Driver, 3.4.8-k2-NAPI
Nov  7 06:52:40 localhost kernel: [4294677.280000] e100: Copyright(c) 1999-2005 Intel Corporation
Nov  7 06:52:40 localhost kernel: [4294677.305000] e100: eth0: e100_probe: addr 0xc0200000, irq 11, MAC addr 00:02:8A:4F:FF:BD
Nov  7 06:53:39 localhost kernel: [4294848.875000] e100: eth1: e100_watchdog: link up, 100Mbps, full-duplex

Any ideas?  Is my hardware getting flaky?

Thanks,
Brian

---

### Post by awood on 2005-11-08
Thank you for your replies.

lspci tells me that my card is a Realtek Semiconductor Co. card
lsmod does not show eth0 (is that what i should be looking for?)
dmesg | less shows:

```

eth0: RealTek RTL8139 at 0x1000, mac address, IRQ 9
eth0: Identified 8139 chip type 'RTL-8139C'
...
NET: Registered protocol family 10
Disabling Privacy Extensions on device c02eb280(lo)
IPv6 over IPv4 tunneling driver
Disabling Privacy Extensions on device c6ba2c00(sit0)
eth0: link down
NET: Registered protocol family 17
eth0: no IPv6 router present
eth0: link down
eth0: no IPv6 router present
...

```

I'm still a bit lost on understanding the problem (and solution!).  Any guidance is greatly appreciated.

Thanks.

---

### Post by mlomker on 2005-11-08
> When it doesn't come up (i.e., whenever I need it:), it doesn't show up in lspci.  However, if I "modprobe e100" I get the following lines in the log file:


I've never seen a situation when lspci didn't see hardware.  You can solve the problem with the adapter name changing by listing your cards in /etc/iftab by their hardware address (**ifconfig** will list that address for you).

```

mlomker@mlomkernote:/$ cat /etc/iftab
# This file assigns persistent names to network interfaces.  See iftab(5).
eth0 mac 00:03:0D:33:CC:F0
wlan0 mac 00:12:F0:CC:5D:06

```

If modprobing the driver always brings it up then you could just put **e100** in you /etc/modules file and see if that works.

---

### Post by mlomker on 2005-11-08
> 
eth0: RealTek RTL8139 at 0x1000, mac address, IRQ 9


Realtek cards seem to have more than their fair share of problems.  You'll find quite a few threads referencing that card if you search.  Sometimes the wrong driver loads, for example in [this thread.]("http://www.ubuntuforums.org/showthread.php?p=377332#post377332")  

It sounds like the driver is loading properly in this case, though.

What do you get for:

```

lsmod | grep 8139
sudo mii-tool eth0
ifconfig eth0

```

The ifconfig command should indicate that packets are being sent and received.

---

### Post by awood on 2005-11-08
I have included the outputs for the following cards.  I should also note, that I have an older ISA network card (D-Link) on this machine as well (with no ethernet cable attached to it).

lsmod | grep 8139
```

8139too           23552      0
8139cp            18432      0
mii                   5248       2 8139too,8139cp

```

sudo mii-tool eth0
```

eth0: no link

```

ifconfig eth0
```

Link encap:Ethernet HWaddr 00:10:B5:0D:9C:92
inet6 addr: f380:210:b5ff:f30d:9c92/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
Interrupt: 9 Base address:0x1000

```

Again, thank you for your patience and assistance.

---

### Post by paddyg on 2005-11-08
may i suggest something just as a test?---hope you haven't done that yet...

if you don't have any particular reasons why you should use dhcp, why don't try a static ip for your box?---that's where you could set your subnet mask address

and then you can check out
```
ifconfig eth0
```

---

### Post by mlomker on 2005-11-08
[QUOTE=awood]I have included the outputs for the following cards.  I should also note, that I have an older ISA network card (D-Link) on this machine as well (with no ethernet cable attached to it).
[/QUOTE]

I'd pull the Dlink card. I suspect you're having the same problem referred to in the link--two drivers loading for just one card.

I'd try removing them and then try them one at a time to see which one works:

```

sudo rmmod 8139too
sudo rmmod 8139c

```

Then load one:

```

sudo modprobe 8139too
sudo ifconfig eth0 up

```

Then see if it works, perhaps by pinging your router or something on the Internet.  Then repeat the process using the **8139c** driver.

---

### Post by awood on 2005-11-08
Well, it turns out that having two cards in one machine was cause the problem.  I had the ethernet cable connected to my ISA DLink Card (no clue why I would do such a thing), but the eth0 was trying to use the RealTek Card.  I just removed my ISA card, and plugged into the RealTek, and everything is working just fine.

Again, thanks for your time and help.

---

