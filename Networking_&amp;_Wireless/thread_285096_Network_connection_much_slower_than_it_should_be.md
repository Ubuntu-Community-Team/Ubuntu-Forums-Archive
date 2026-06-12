---
title: "Network connection much slower than it should be"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by dotsi on 2006-10-26
I'm using an ethernet connection that is straight behind the house complex router, no additional hardware of my own in between. The connection is terribly slow, much slower than on Windows XP on the same computer. I've disabled ipv6 from both the whole system and Firefox, but that didn't help. I'm currently running freshly upgraded edgy but the connection was slow back in dapper too.

I'm also running out of ideas, any help? I'm more than glad to attach some information about my system, just tell me what do you want to know.

---

### Post by viz_e on 2006-10-27
Same here: ethernet working as 10Mbit instead of 1Gb after upgrade to edgy.

---

### Post by dotsi on 2006-10-27
> **viz_e said:**
> Same here: ethernet working as 10Mbit instead of 1Gb after upgrade to edgy.

It seemed that my network adapter had somehow gone to 10Mbit mode too, but **sudo mii-tool eth1** says it's still 100Mbit full duplex as it should be. Auto-negotiation is disabled from the switch, thus forcing it to that mode.

---

### Post by davec64 on 2006-10-27
Yep, same problem.

The laptop is wireless and my Desktop is wired.(Both Dapper).
Firefox is slow to return web pages and Evolution takes an age to return embedded images in HTML emails.

If anybody has got any suggestions, they'd be much appreciated!

---

### Post by viz_e on 2006-10-28
Actually, after a deeper analysis, it turns out in my case that only tasks like ssh, scp and so on are slow.  For those, I get 1.2 Mbytes/s in upload and 1.6 Mbytes/s in download. By normal browsing everything is faster. I wonder whether there is some constraints somewhere for ssh... Any idea?!? :confused:

---

### Post by dotsi on 2006-10-28
OK, I also tried adding "nolapic noapic" on the kernel boot line, as instructed elsewhere, but that was no use. The problem still remains. Someone also told me that the DNS server I'm using could be faulty or just not working fine with Linux, how do I know that?

---

### Post by stream303 on 2006-10-29
Common problem with inexpensive routers that also do internal dns - easily fixed with a config file.

Take a look at your  /etc/resolv.conf  file.

I'll bet that the dns of your router is first in the list, before the dns addresses of your isp.  We wait for the funky router dns to timeout before it gets to the isp's dns servers.

If this is the case after examining your /etc/resolv.conf file, there are things you can do to alter this file correctly and keep it from being overwritten upon re-lease or reboot.

---

### Post by dotsi on 2006-10-29
> **stream303 said:**
> Common problem with inexpensive routers that also do internal dns - easily fixed with a config file.

Take a look at your  /etc/resolv.conf  file.

I'll bet that the dns of your router is first in the list, before the dns addresses of your isp.  We wait for the funky router dns to timeout before it gets to the isp's dns servers.

If this is the case after examining your /etc/resolv.conf file, there are things you can do to alter this file correctly and keep it from being overwritten upon re-lease or reboot.

Thanks for your reply. Here's my /etc/resolv.conf:

```
domain lnet.lut.fi
nameserver 157.24.8.11
search lnet.lut.fi lut.fi cc.lut.fi it.lut.fi pc.lut.fi
nameserver 157.24.100.6
```

It seems that my host's domain name is on the first line, followed by the "primary" nameserver. Then there are the searchable domain names and finally the "secondary" nameserver (actually I switched the nameservers the other way round because the network admin of this house told me there might be some problems with the primary nameserver). I don't think that the router does any DNS'ing of it's own, since there are separate DNS servers defined in the network's instructions.

Is there a way I can alter the file in order to make things better and to prevent further problems?

---

### Post by stream303 on 2006-10-30
One thing right off the bat:  domain and search lines are mutually exclusive (per man resolv.conf).  You can only have one or the other - otherwise the system will just use the last search or domain line it finds in that file.

Nameservers should follow below either domain or search - so you may have to pick either domain or search and stick to it exclusively.  I'm not familiar with multiple domains or search lists, so I'll have to defer this to someoene else.

Are you sure your nameservers are correct?  If you leave out the nameservers altogether, and use only a domain or search line as the first line in the file, will it pick up the proper nameservers automatically?  Something to try, but I leave this to the big guns now...

---

### Post by dotsi on 2006-10-30
> **stream303 said:**
> One thing right off the bat:  domain and search lines are mutually exclusive (per man resolv.conf).  You can only have one or the other - otherwise the system will just use the last search or domain line it finds in that file.

Nameservers should follow below either domain or search - so you may have to pick either domain or search and stick to it exclusively.  I'm not familiar with multiple domains or search lists, so I'll have to defer this to someoene else.

Are you sure your nameservers are correct?  If you leave out the nameservers altogether, and use only a domain or search line as the first line in the file, will it pick up the proper nameservers automatically?  Something to try, but I leave this to the big guns now...

Thanks again for your answer. It didn't seem to matter which I choose, domain or search. They both function the same.

I'm quite sure that the nameservers are correct, because they are listed on a paper with all the IP addressess for the apartments in this house, and I also checked with the network admin that they are still valid. After commenting out the nameserver lines in the /etc/resolv.conf file my browser wasn't able to resolve any addresses whatsoever, so it seems that no automatic DNS'ing here.

---

### Post by jazzroy on 2006-10-30
same troubles here, internet very slow under ubuntu... but addresses are in a different order:

> search polito.it
nameserver 130.192.42.65
nameserver 130.192.3.21
nameserver 130.192.3.24

---

### Post by viz_e on 2006-10-30
Any clue about a slow ssh connection?

---

### Post by dotsi on 2006-10-31
My network interface card is 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78) and it's using the 3c59x kernel module. Is there any other module I could try it with?

---

### Post by dotsi on 2006-10-31
OK, I'm having some weird output from some of the tools I'm told to try:

```
$ ifconfig eth1
...
RX packets:657227 errors:0 dropped:0 overruns:19 frame:0
...
```

What are these overruns and do they have anything to do with the slowness?

```
$ dmesg | grep eth1
[17179592.380000] eth1:  setting half-duplex
```

but

```
$ sudo mii-tool eth1
eth1: 100 Mbit, full duplex, link ok
```

Which I should believe? mii-tool I think, because it has the "latest" information, am I right?

How about flow control, could it be used to make things better?

---

### Post by cnkbrown on 2006-10-31
Just to keep the thread fresh - I also have a way slow eth0 connection.

I have Win XP and this very fresh ubuntu Edgy machine on same network - using same internet speed test sites, Win XP gets upwards 2.3 MBpbs, where ubuntu is lucky to get 64 KBps.  Clearly, something is fundamentally wrong.

Following advice from various posts, I have;

- verified dmesg | eth0 that eth0 is 100 MBps, full duplex
- verified mii-tool eth0 reports 100baseTx-FD
- disabled IPv6 in etc/modprobe.d/aliases
- twiddled various settings in firefox's about:config
- installed firestarter, and tried test w/ firewall disabled
   * actually got me to ~90 Kbps - whoopee!
- fiddled with DNS servers
   * does not help - at all.

I'm about to go find a dead cat and a chicken, and head to the local boneyard.

I wouldn't mind the slow speed, except for the unbearable amount of time it takes to install worthwhile packages (usually at about 6 (yes, six) KBps), the trash talk I'm taking from my 12 year old about how much linux sucks, and the kids fighting about who gets to use the 'fast one'.

Admittedly, this box is an older P4 machine, but it should be doing better than dial up modem speeds.  Especially as System Monitor shows things mostly idle.

I feel better now - well a little, anyway.

---

### Post by fredy prada on 2006-11-01
my conection is extremely slow, i moved from kubuntu to ubuntu, i disabled the IPv6, i installed opera, i did everything they recommend in the forums but the connection was slow, so in my everyday work i was forced to moved back to window$.

thanks

---

### Post by dotsi on 2006-11-04
So, where are all the big guns? :)

---

### Post by dotsi on 2006-11-06
Well, still something to look at:

```
$ sudo mii-diag eth1
Basic registers of MII PHY #24:  2100 780d 0041 6800 0581 0000 0004 2001.
Basic mode control register 0x2100: Auto-negotiation disabled, with
Speed fixed at 100 mbps, full-duplex.
You have link beat, and everything is working OK.
Link partner information is not exchanged when in fixed speed mode.
   End of basic transceiver information.
```

```
$ lsmod | grep 3c
3c59x                  47912  0
mii                     6912  1 3c59x
```

```
$ sudo vortex-diag -a
vortex-diag.c:v2.16 1/12/2004 Donald Becker (becker@scyld.com)
http://www.scyld.com/diag/index.html
Index #1: Found a 3c920 Series NIC adapter at 0xd000.
Station address 00:04:75:bf:48:aa.
  Receive mode is 0x07: Normal unicast and all multicast.
The Vortex chip may be active, so FIFO registers will not be read.
To see all register values use the '-f' flag.
Initial window 4, registers values by window:
  Window 0: 0000 0000 e71f 0000 c7c7 00bf ffff 0000.
  Window 1: FIFO FIFO 0700 0000 0000 007f 0000 2000.
  Window 2: 0400 bf75 aa48 0000 0000 0000 0052 4000.
  Window 3: 0000 0180 05ee 0000 000a 0800 0800 6000.
  Window 4: 0000 0000 0000 0ccc 0001 8880 0000 8000.
  Window 5: 1ffc 0000 0000 0600 0807 06ce 06c6 a000.
  Window 6: 0000 0000 0000 0000 0000 0000 0000 c000.
  Window 7: 0000 0000 8100 0000 0000 0000 0000 e000.
Vortex chip registers at 0xd000
  0xD010: **FIFO** 00000000 0000000d *STATUS*
  0xD020: 00000020 00000000 00080000 00000004
  0xD030: 00000000 2afdd503 37f16180 00080004
  0xD040: 0097eaa6 00000000 000000b7 00000000
  0xD050: 00000000 00000000 00000000 00000000
  0xD060: 00000000 00000000 00000000 00000000
  0xD070: 00009000 00000000 01600160 00000000
  DMA control register is 00000020.
   Tx list starts at 00000000.
   Tx FIFO thresholds: min. burst 256 bytes, priority with 128 bytes to empty.
   Rx FIFO thresholds: min. burst 256 bytes, priority with 128 bytes to full.
   Poll period Tx 00 ns.,  Rx 0 ns.
   Maximum burst recorded Tx 352,  Rx 352.
Indication enable is 06c6, interrupt enable is 06ce.
No interrupt sources are pending.
Transceiver/media interfaces available:  100baseTx 10baseT.
Transceiver type in use:  Autonegotiate.
MAC settings: **half-duplex**.
Maximum packet size is 1518.
Station address set to 00:04:75:bf:48:aa.
Configuration options 0052.
```

There's that half-duplex again! And still according to the network admin, this port should be forced to 100Mbit full-duplex from the switch. This is because there has been some problems with 3com NICs and HP switches, and disabling autonegotiation has sometimes solved it.

---

### Post by netztier on 2006-11-06
> **dotsi said:**
> 

```

...
**Transceiver type in use:  Autonegotiate.**
MAC settings: **half-duplex**.
Maximum packet size is 1518.
Station address set to 00:04:75:bf:48:aa.
Configuration options 0052.
...

```

There's that half-duplex again! And still according to the network admin, this port should be forced to 100Mbit full-duplex from the switch. This is because there has been some problems with 3com NICs and HP switches, and disabling autonegotiation has sometimes solved it.

If the switch port is set to full duplex, your NIC *must* be manually set to full duplex too. This is because the switch (and any other NIC-like device I have come across) stops sending what is called "Fast Link Pulses" in which its speed and duplex capabilities are encoded. 

If a device does *not* "hear" Fast Link Pulses, it *must* default to half duplex. The output of mii-tool also explains this: *"Link partner information is not exchanged when in fixed speed mode."* And there you go: **[COLOR="Red"]duplex mismatch[/COLOR]**


One thing you can't do: force full duplex mode "from the switch". Once you configure a fixed setting for speed or duplex, the the device stops advertising it's capabilities.

So it's either "auto" for both devices (and it's left to them to exchange their preferred modes and agree on one), or it's manually fixing *both* ends to the same setting. Every other combination (except one: one side "auto", the other fixed to "half duplex") will result in a duplex mismatch and miserable performance.



Maybe the module is buggy or it does not properly reconfigure the NIC to full duplex. What does dmesg say about the link when the NIC is being plugged in?


[I]Edit:
Here's a document by from Cisco that sums it up quite nicely: [Why Do Autonegotiation and Compatibility Issues Exist? ]("http://www.cisco.com/en/US/products/hw/switches/ps700/products_tech_note09186a00800a7af0.shtml#why_do_auto")[/I]

regards

Marc

---

### Post by dotsi on 2006-11-07
I solved the case by asking the network admin to enable autonegotiation again from the switch. Now everything seems to function as it should be. 

Thanks for your great advice!

---

### Post by dotsi on 2006-11-21
All right, the problem seems to be still somewhat persisting. I guess it has something to do with the NIC not being advertising its autonegotiation capability. This has to be turned on manually and networking must be restarted with ```
sudo mii-tool -r eth1 && sudo /etc/init.d/networking restart
``` Is there a way I can automatically enable the autonegotiation at bootup?

---

