---
title: "Slow HTTP connections, other assorted network oddities"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by willfe on 2008-02-13
**Update:** This has been solved. It was the local router in use that was misconfigured (just a little) that caused this problem.

Do *not* be fooled if you have this problem, reboot the machine into Windows for testing, and determine that it "works just fine" on Windows. It may not always work even if your specific test cases do, and it changes nothing anyway.

I had been having this trouble for a few weeks, and yesterday got an opportunity to test whether this issue happened elsewhere (not just on this connection on this router). On the other connection (also wireless, btw), everything worked fine. No problems, no stalls, no delays, etc.

Returning to this environment (where things were broken), I took a closer look at the router's configuration. It is an Asus WL520GU, connected to an AT&T DSL modem. The Asus is pretty new (purchased in January); the DSL modem is not.

The DSL modem was configured to claim 192.168.1.254 as its private address, while performing IP passthrough (passing on routing/firewall duties to the client connected on its ethernet port).

The Asus was configured to claim 192.168.1.1. On a hunch, I switched it to 192.168.2.1 (note the different network there), so all clients would end up on 192.168.2.0/28 instead of 192.168.1.0/28. That fixed it. Apparently the router and modem get huffy with each other if they both try to sit on the same subnet acting as routers, even when the modem only has one client (the router). *Sigh*.

Anyway, check that setting on your router if you have this problem.

_*Original problem description follows*_
I'm trying to sort out some oddities I'm seeing in Hardy (Alpha 4, with updates as of a few minutes prior to this post) relating to network performance. I'll include hardware configuration info below the description of symptoms.

It's a fairly new install; I haven't had it around long enough to really bork any of the configuration :)

For the most part, network performance is quite good -- after some normal wrestling with ndiswrapper (sadly, b43 and b43legacy won't talk to my wireless card -- I have never gotten so much as a "found hardware I hate!" message in dmesg, syslog, or messages from b43 or b43legacy) I've gotten wireless networking up and running. The good news is Network Manager works fine with it, even with WPA2 encryption. I do have to run a script upon login to get things working, though. For some reason, the ssb driver grabs the wireless card away from ndiswrapper (and I *have* blacklisted ssb, but it loads anyway because ohci_hcd seems to want it):

```

root@prometheus:~# cat fix_wireless.sh 
#!/bin/sh
sudo rmmod ohci_hcd ssb ndiswrapper
sudo modprobe ndiswrapper
echo Waiting 15 seconds to let the built-in network manager grab the interface
echo before continuing...
sleep 15;
sudo modprobe ohci_hcd
sudo modprobe ssb

```

Now, the symptoms:

* "apt-get update" will almost always freeze for upwards of two minutes before it actually begins transferring package lists; "apt-get -fu dist-upgrade" does the same before it starts transferring packages. Using Synaptic gives the same results: updating the package lists or upgrading the system both begin with a nasty delay. "Waiting for headers" just takes forever :) During this delay, other applications continue to work properly. I can do DNS lookups and find remote hosts, I can ping them, and I can browse random pages with Firefox. Once the transfers *do* start, transfer speeds are normal for the connection in use at this location (768kb/256kb DSL, bleh). On my home connection (10Mb/768kb cable), the same delays occur, and then transfers are as fast as that connection will permit.
* Firefox will occasionally stall for about the same amount of time when I ask it to load a new page in a new tab. If I could pin down a specific page that causes this, you'd see a URI or two posted here along with my report. Alas, it seems to be random (or at least following a pattern I can't find). This causes several (fairly braindead, I'll admit) applications I use fail, since they do all sorts of fancy callbacks via JavaScript to move from page to page. DHL's website is a good example (they're a shipping company); I can't actually accomplish anything once I've logged in. The site works fine from my Ubuntu 7.10 desktop (amd64 there), same major/minor build of Firefox.
* SCP transfers to *other* systems used to fail consistently, stalling for minutes until killed. SCP transfers *into* this system work fine. This mysteriously fixed itself on the very last update I just did a bit ago (I just tested SCP again to make sure it was still broken, and it works fine now). Odd.

I might as well also vent that suspend-to-RAM just crashes the machine (it never gets to the suspended state; it just freezes) and it'll also crash if I close the laptop's lid (I fixed that by setting the system preference to "Do nothing" for the "lid closed" action). These aren't showstoppers -- Hardy shuts down and starts up fast enough that it's not an issue.

It's also worth noting this behavior occurs whether I'm using the wireless card or the wired ethernet interface. Both are DHCP, set to roaming mode. Disabling roaming mode doesn't change the behavior.

As an amusing aside, I wasn't able to post this message from Linux on the notebook; I had to reboot into Vista (ugh) to post this. I can browse the forums just fine, but posting (either via "preview" or "submit new thread") just sits and spins -- never gets anywhere. :(

My hardware configuration:

HP/Compaq Presario F534US; amd64 X2 dual-core, though I'm running the standard 32-bit edition of Hardy on it.

Assorted detailed information follows:

```
root@prometheus:~# ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1a:73:7e:f3:de  
          inet addr:192.168.1.53  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe7e:f3de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:86784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51388 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:119814101 (114.2 MB)  TX bytes:4587297 (4.3 MB)
          Interrupt:21 Memory:b8000000-b8004000 

```

```

root@prometheus:~# lspci | grep Eth
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
root@prometheus:~# lspci | grep Net
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

```

```

root@prometheus:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

```

```

root@prometheus:~# cat /etc/resolv.conf 
# generated by NetworkManager, do not edit!
nameserver 4.2.2.2
nameserver 192.168.1.1

```

```

root@prometheus:~# cat /etc/network/interfaces 
auto lo
iface lo inet loopback
iface eth0 inet dhcp

```

If any other details from the machine would be helpful, you need only but ask :)

Advice is appreciated. This is tantalizingly close to being completely usable.

Thanks!

---

