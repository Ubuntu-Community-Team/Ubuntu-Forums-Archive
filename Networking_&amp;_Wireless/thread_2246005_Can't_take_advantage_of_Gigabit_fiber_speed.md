---
title: "Can't take advantage of Gigabit fiber speed"
date: 2014-09-27
forum: Networking &amp; Wireless
---

### Post by marcw on 2014-09-27
I'm participating in a trial of a 1Gbps fiber installation by CenturyLink.  Yes, it's really 1Gbps (1000Mbps) to my home.  Unfortunately, I'm not getting anywhere close to the rated download speed on my Ubuntu machines so I thought I'd ask for advice here.  CenturyLink has not been much help so far.  Here's the kicker: when running laptop B (below) in Windows Networking Safe Mode I can achieve close to the full gb throughput.  As far as CenturyLink is concerned, that's all they care about - it's proof that they are in fact delivering the full gb speeds.

For testing purposes, I perform all tests directly out the back of the provided Technicolor router, bypassing my home network completely.  Test machines are a couple of fairly recent HP laptops:
	A) 6930p - 14.04 64bit desktop installed
	B) 8470p - Win7 installed, using Ubuntu 14.04.1 64bit desktop live DVD
	C) same as B - Win7 
	D) same as B - Win7 Network Safe Mode

Here's what I've done so far:

Preliminary test:  iperf - full duplex through the CenturyLink provided switch (router)

Results:
12345@678-HP-Elitebook-6930p:~$ iperf -c 192.168.0.187 -t 20 -d
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 192.168.0.2, TCP port 5001
TCP window size: 366KByte (default)
------------------------------------------------------------
[  5] local 192.168.0.187 port 33336 connected with 192.168.0.2 port 5001
[  4] local 192.168.0.187 port 5001 connected with 192.168.0.2 port 41903
[ ID] Interval       Transfer     Bandwidth
[  5]  0.0-20.0 sec  2.17 GBytes   934 Mbits/sec
[  4]  0.0-20.0 sec  2.17 GBytes   930 Mbits/sec

I believe this tells me that my laptops and switch are capable of handling full duplex gb traffic.

I've attached screenshots of the results of the speed tests when I test the laptops against the CenturyLink speed test web site.  Summarized here:
[table="width: 500, class: grid, align: left"]
[tr]
	[td][/td]
	[td]download speed[/td]
	[td]upload speed[/td]
	[td]attachment name[/td]
[/tr]
[tr] 
	[td]machine A[/td]
	[td]142[/td]
	[td]934[/td]
	[td]094.png[/td]
[/tr]
[tr] 
	[td]machine B[/td]
	[td]259[/td]
	[td]933[/td]
	[td]095.png[/td]
[/tr]
[tr] 
	[td]machine C[/td]
	[td]428[/td]
	[td]695[/td]
	[td]096.png[/td]
[/tr]
[tr] 
	[td]machine D[/td]
	[td]909[/td]
	[td]943[/td]
	[td]097.png[/td]
[/tr]
[/table]

You can see that the Ubuntu upload speeds are terrific.  So it would seem that there's something within Ubuntu that's throttling my potential download speeds but I don't know what it is and would appreciate any advice.

---

### Post by tgalati4 on 2014-09-27
I would run ten tests of each case and look at the variability.  It's possible that you are hitting traffic at CenturyLink's switch--like video streaming which would have Quality of Service (QoS) policies to ensure that their content gets through.  

Also make sure that your Ubuntu machine is not running updates or other chores in the background.  Monitor with *top* or *htop*.

Make sure your cabling and connections are Cat6.  Although Cat5e can handle gigabit traffic (350 MHz bandwidth), Cat6 is really needed to ensure full duplex performance.

It's possible that the linux drivers for your network card need tweaking or are too generic to support higher bandwidth compared to Windows proprietary drivers.  On a laptop, you would be using wireless, so you will be lucky to get better than Wireless G speeds (48 to 54 Mbits/sec).

I would find a server or workstation with a decent gigabit card and run the tests again in linux.

Compare the wireless performance in your 4 Use Cases and see what the differences are.

---

### Post by marcw on 2014-09-27
Thanks for taking the time to read about my issue.

> **tgalati4 said:**
> I would run ten tests of each case and look at the variability.  It's possible that you are hitting traffic at CenturyLink's switch--like video streaming which would have Quality of Service (QoS) policies to ensure that their content gets through.  

Believe me, I've run through these and other tests dozens of times at most hours of the day.  The only fluctuations I've seen have been minor.

> Also make sure that your Ubuntu machine is not running updates or other chores in the background.  Monitor with *top* or *htop*.

Yep, standard procedure.

> Make sure your cabling and connections are Cat6.  Although Cat5e can handle gigabit traffic (350 MHz bandwidth), Cat6 is really needed to ensure full duplex performance.

Right.  Everything in the house is cat6 including the patch cables used for testing.

> It's possible that the linux drivers for your network card need tweaking or are too generic to support higher bandwidth compared to Windows proprietary drivers.  On a laptop, you would be using wireless, so you will be lucky to get better than Wireless G speeds (48 to 54 Mbits/sec).

Yes, this makes sense and already thought of that.  That's why I showed the full duplex iperf test in my original post.  It seems to show that the CenturyLink switch and my laptops all can handle asymetrical full duplex Gb traffic.  Not sure I understand your comment about wireless.  I rarely run anything wirelessly.  Matter of fact, I disabled wireless networking on the laptops and router just to insure there wouldn't be interference during my testing(although I doubt it made any difference).

---

### Post by tgalati4 on 2014-09-27
I run all my laptops with wireless.  If I had fiber to the house, I would certainly pull cable to each corner of each room.  If your normal mode was wireless for laptops, then testing for gigabit would be overkill.  I'm lucky to get 7 Mbits/sec with business-grade DSL.  ATT UVerse has pretty agressive QoS rules as they try to compete with the cable TV companies.

What network cards are you running?

```
lspci | grep Ethernet
```

What switches are available for those Ethernet card modules?

For a Broadcom Tigon3 ethernet chipset:

```
modinfo tg3
```

Yours will be different.

---

### Post by marcw on 2014-09-28
> **tgalati4 said:**
> What network cards are you running?

*00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)*

> What switches are available for those Ethernet card modules?


[I]12345@678-HP-EliteBook-6930p:~$ sudo modinfo e1000e
[sudo] password for marcw: 
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko
version:        2.3.2-k
license:        GPL
description:    Intel(R) PRO/1000 Network Driver
author:         Intel Corporation, <linux.nics@intel.com>
srcversion:     FAFC167239309C03F11F440
alias:          pci:v00008086d000015A3sv*sd*bc*sc*i*
*********  A bunch of other aliases ****************
alias:          pci:v00008086d0000105Esv*sd*bc*sc*i*
depends:        ptp
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512
parm:           debug:Debug level (0=none,...,16=all) (int)
parm:           copybreak:Maximum size of packet that is copied to a new buffer on receive (uint)
parm:           TxIntDelay:Transmit Interrupt Delay (array of int)
parm:           TxAbsIntDelay:Transmit Absolute Interrupt Delay (array of int)
parm:           RxIntDelay:Receive Interrupt Delay (array of int)
parm:           RxAbsIntDelay:Receive Absolute Interrupt Delay (array of int)
parm:           InterruptThrottleRate:Interrupt Throttling Rate (array of int)
parm:           IntMode:Interrupt Mode (array of int)
parm:           SmartPowerDownEnable:Enable PHY smart power down (array of int)
parm:           KumeranLockLoss:Enable Kumeran lock loss workaround (array of int)
parm:           WriteProtectNVM:Write-protect NVM [WARNING: disabling this can lead to corrupted NVM] (array of int)
parm:           CrcStripping:Enable CRC Stripping, disable if your BMC needs the CRC (array of int)[/I]

Even though you asked just for modinfo, here's some ethtool settings.  Both of these outputs are for the 6930p.  The other laptop is similar:

[I]12345@678-HP-EliteBook-6930p:~$ ethtool -i eth0
driver: e1000e
version: 2.3.2-k
firmware-version: 1.8-3
bus-info: 0000:00:19.0
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes
supports-priv-flags: no

12345@678-HP-EliteBook-6930p:~$ ethtool -k eth0
Features for eth0:
rx-checksumming: on
tx-checksumming: on
	tx-checksum-ipv4: off [fixed]
	tx-checksum-ip-generic: on
	tx-checksum-ipv6: off [fixed]
	tx-checksum-fcoe-crc: off [fixed]
	tx-checksum-sctp: off [fixed]
scatter-gather: on
	tx-scatter-gather: on
	tx-scatter-gather-fraglist: off [fixed]
tcp-segmentation-offload: on
	tx-tcp-segmentation: on
	tx-tcp-ecn-segmentation: off [fixed]
	tx-tcp6-segmentation: on
udp-fragmentation-offload: off [fixed]
generic-segmentation-offload: on
generic-receive-offload: on
large-receive-offload: off [fixed]
rx-vlan-offload: on
tx-vlan-offload: on
ntuple-filters: off [fixed]
receive-hashing: on
highdma: on [fixed]
rx-vlan-filter: off [fixed]
vlan-challenged: off [fixed]
tx-lockless: off [fixed]
netns-local: off [fixed]
tx-gso-robust: off [fixed]
tx-fcoe-segmentation: off [fixed]
tx-gre-segmentation: off [fixed]
tx-ipip-segmentation: off [fixed]
tx-sit-segmentation: off [fixed]
tx-udp_tnl-segmentation: off [fixed]
tx-mpls-segmentation: off [fixed]
fcoe-mtu: off [fixed]
tx-nocache-copy: on
loopback: off [fixed]
rx-fcs: off
rx-all: off
tx-vlan-stag-hw-insert: off [fixed]
rx-vlan-stag-hw-parse: off [fixed]
rx-vlan-stag-filter: off [fixed]
l2-fwd-offload: off [fixed][/I]

But I'm not sure what would be gained by changing any of these settings since iperf already proved that both the hardware and software are capable of providing asymetrical Gb throughput.  Unless I don't understand iperf correctly.

---

### Post by tgalati4 on 2014-09-28
As you can see, there are a lot of settings that you can fiddle with.  In order to solve a problem like this, one must get into the details and the fundamentals of how the network functions.  Something like this:  [http://www.tcpipguide.com/free/t_NetworkLayerLayer3.htm](http://www.tcpipguide.com/free/t_NetworkLayerLayer3.htm)

Just because you can move data packets quickly between two endpoints does not mean you can sustain an equally-high throughput for files between two computers--the final measure of throughput.

This makes for interesting reading:  [http://downloadmirror.intel.com/9180/eng/README.txt](http://downloadmirror.intel.com/9180/eng/README.txt)

I only counted a dozen parameters that could affect throughput.  You can change them using the modprobe switches or in a configuration file in /etc/modprobe.d.

It's possible that the Windows driver uses different default values than the Linux driver.  You could send an email to Intel and ask them.  They probably wrote the driver for Windows.  They might be moderately interested in network card performance since they are a chip company.  Nobody wants their chip to look bad.

Send them a link to this thread as a data reference.

*iperf* as several settings as well.  You can try changing the write buffer to something other than 8 kilobytes.

---

