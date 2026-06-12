---
title: "Network not routing trafic"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by hellinux on 2008-05-05
Hi,

I have a Dell PowerEdge 2950 and installed Ubuntu 8.04 server on it.  It starts up fine, no [FAILED] messages and all looks good.  Then when I try the network I have a issue.

ifconfig shows eth0 with a fixed IP, Netmask looks good.

```
inet addr:10.38.52.104  Bcast:10.38.63.255  Mask:255.255.192.0
```

I checked the /etc/network/interfaces and I have the following
```

auto eth0
iface eth0 inet static
        address 10.38.52.104
        netmask 255.255.192.0
        network 10.38.0.0
        broadcast 10.38.63.255
        gateway 10.38.0.1

```

I can ping 10.38.52.104 and get a reply, but when I try to ping anything else I get "Destination Host Unreachable"

any ideas where to look for this problem?

---

### Post by Iowan on 2008-05-05
What else (address-wise) is on the network?

Dunno if Hardy has Roaming Mode (I'm still on Gutsy), but try turning it off.

---

### Post by andrewc6l on 2008-05-05
Whenever I see this, my first instinct is to make sure the gateway is correct. Yours is set to:

10.38.0.1

Given your IP address, are you certain it's not something like 10.38.52.1? Can you see other machines in the 10.38.52.* range?

---

### Post by hellinux on 2008-05-05
I will Google Roaming Mode next :-)

The subnet allows the 10.38.0.1 as a GW, see the IP calculation

```

Address:   10.38.52.104          00001010.00100110.00 110100.01101000
Netmask:   255.255.192.0 = 18    11111111.11111111.11 000000.00000000
Wildcard:  0.0.63.255            00000000.00000000.00 111111.11111111
=>
Network:   10.38.0.0/18          00001010.00100110.00 000000.00000000 (Class A)
Broadcast: 10.38.63.255          00001010.00100110.00 111111.11111111
HostMin:   10.38.0.1             00001010.00100110.00 000000.00000001
HostMax:   10.38.63.254          00001010.00100110.00 111111.11111110
Hosts/Net: 16382                 (Private Internet)

```

---

### Post by hellinux on 2008-05-05
oh and I cant see anything else in the range.

I ping 127.0.0.1 it works
I ping its own IP it works
I ping a IP that 10.38.52.105 and that does not work.  I have even connected it to my notebook with a Hub, added the 3rd PC on the network (103).  From my notebook, 105 I can ping 103 but not 104, my mystery Dell Power Edge.

---

### Post by andrewc6l on 2008-05-05
Strange... (and I shoulda caught that netmask :-) )

Is there a chance you've got more than one Ethernet controller on your machine, and the one you're plugging into the network is not the one you're configuring the IP address for?

---

### Post by netztier on 2008-05-06
> **hellinux said:**
> 
any ideas where to look for this problem?

My workstation "cube" suffers from siliar symptoms; all seems to be there, static IP address, mask, gateways, interface is up etc; can ping loopback, can ping own address.

But when checking with a 10Mbit hub (or a LAN switch with mirrored port) and a second computer running Wireshark, I discovered that "cube" did not actually send anything at all out of it's ethernet interface.

After a lot of searching, I found that there was a problem with the ethernet chip and driver combination. It's a Marvell Chipset with a version that only runs with the **skge** module, neither sky2 nor nvnet or forcedeth would work, and in addition to that, skge will only work if I add "**noapic**" as kernel option when booting.

So it might be worth checking if that NIC actually sends anything  out, you should at least see some ARP requests when you try to ping your default gateway.

regards

Marc

---

### Post by hellinux on 2008-05-06
more digging, looks like no traffic is coming out of that network card.  I dug through the logs.  things look ok, it s using BNX2 as a module.

I went on Braodcom site but there they only have source (I have not compiled anything for a very long time) so I thought perhaps a updated driver... any ideas on how to fix this are welcome.

---

### Post by hellinux on 2008-05-06
SOLVED... here is the problem.  The Dell PowerEdge server has 2 network ports.  As one final test I turned off one of the ports and then the network stopped working all together. Re-did the network configuration and it worked.  Looks like using only one port may cause a problem.

---

