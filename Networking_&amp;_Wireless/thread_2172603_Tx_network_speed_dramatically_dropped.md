---
title: "Tx network speed dramatically dropped"
date: 2013-09-05
forum: Networking &amp; Wireless
---

### Post by mokum2 on 2013-09-05
I have a mailserver on which transmission-daemon (torrents) is also running.
Since yesterday the tx speed totally dropped to a turtle stroll, rx speed is still ok.
I reinstalled the server just a couple of days ago (after having had the same problems). 

I just performed some tests with vsftpd, transferring about 712MB:
From my pc to my server: 47.5MB/s
From my server to my pc: 47.5kB/s
So tx speed is a factor 1000 slower than rx speed. It's a simple Compaq desktop with an old ide drive, so 47,5MB/s seems reasonable.

Problems started when I transferred the received files from my server to my pc when transmission-daemon was still running.
Months ago I did this without any problems. The dramatic decrease in speed happened a while ago, I don't exactly recall when.

Rebooting doesn't have any effect. When I reboot, tx speed is still lousy. So somehow something changed some setting and it's persistent.
 I don't have a clue as to what is causing this. Perhaps I contracted a digital std :(

The nic is working properly as far as I can see. Ethtool reports: Speed: 1000Mb/s, Duplex: Full. I checked some settings with sysctl, but I
can't see noticable differences between my server and my pc. It's not just a protocol, everything leaving the nic is bogged down.
Anybody have a clue?

---

### Post by houstonbofh on 2013-09-05
How full is your hard drive? EXT(x)fs is auto-defragmenting, but only if you keep it less than 85% full.  With torrent boxes, it is easy to fill the drive with millions of tiny fragments.  This makes reads a total nightmare.

---

### Post by mokum2 on 2013-09-05
> **houstonbofh said:**
> How full is your hard drive? EXT(x)fs is auto-defragmenting, but only if you keep it less than 85% full.  With torrent boxes, it is easy to fill the drive with millions of tiny fragments.  This makes reads a total nightmare.

It's not filled to the rim, 'just' 44%. I don't think the drive is the culprit, if I send something to the server the speed is fine. If I send the same file back to my pc, I can
grab a schnapps and a cigar and start talking about old times. Moreover, my torrent files only occupy 1.4GB. Far less than what I had when these problems didn't occur.
The torrent files are also on a separate partition, I tested transfers to and from different partitions with the same results.
The only thing I can think of at this point, is some kind of network problem.

---

### Post by varunendra on 2013-09-06
Does ifconfig report any tx packet drop errors on the server?

And just out of curiosity, which network chip it is using? -
```
sudo lshw -C network
```

---

### Post by mokum2 on 2013-09-06
> **varunendra said:**
> Does ifconfig report any tx packet drop errors on the server?

And just out of curiosity, which network chip it is using? -
```
sudo lshw -C network
```

No it doesn't, not one error. That was one of the first things I checked.
lshw -C network produces:

*-network:1
       description: Ethernet interface
       product: RTL8169 PCI Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:05:09.0
       logical name: eth1
       version: 10
       serial: a0:f3:c1:04:af:77
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.10 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=1Gbit/s
       resources: irq:18 ioport:1000(size=256) memory:fc501000-fc5010ff memory:50000000-5001ffff

Yesterday I turned off the server after having fiddled with it for hours. When I turned it on this morning, everything worked like a charm. But after some hours, tx speeds dropped again.
This evening I did some tests again, with the same results, turtle speed when transmitting. So I rebooted and tried again, to no avail. Then I remembered that problems began when I
installed everything on another computer, an identical Compaq. Problems didn't start right away but after some weeks I recalled. And ever since when I reboot and immediately try again,
there's no change in speed. But when I leave it off for a few hours and then boot again, speeds are fine. For a while that is.

So I began to think of thermal problems. I just swapped drive, memory and nic and put them back in the pc I used before. And voila, everything is hunky dory. So if it is a thermal problem, I still should have
normal tx speeds in the morning. Still, weird. No errors, only tx speed drops, other peripherals on the pci bus don't seem to have any problems. Allthough, I had the same probs with the integrated nic.
Anyway, thanks for the response. With a bit of luck, tomorrow wil be the end of my probs.

---

### Post by houstonbofh on 2013-09-06
Time to start breaking apart the components.  Have you played with iperf yet?  An amazingly useful tool.

[http://openmaniak.com/iperf.php](http://openmaniak.com/iperf.php)
[http://www.techrepublic.com/blog/opensource/iperf-a-simple-but-powerful-tool-for-troubleshooting-networks/3395](http://www.techrepublic.com/blog/opensource/iperf-a-simple-but-powerful-tool-for-troubleshooting-networks/3395)

This will confirm or eliminate the network stack fast.

Also, have you tried swapping cables?  Network cables can go bad.

---

### Post by mokum2 on 2013-09-07
> **houstonbofh said:**
> Time to start breaking apart the components.  Have you played with iperf yet?  An amazingly useful tool.

[http://openmaniak.com/iperf.php](http://openmaniak.com/iperf.php)
[http://www.techrepublic.com/blog/opensource/iperf-a-simple-but-powerful-tool-for-troubleshooting-networks/3395](http://www.techrepublic.com/blog/opensource/iperf-a-simple-but-powerful-tool-for-troubleshooting-networks/3395)

This will confirm or eliminate the network stack fast.

Also, have you tried swapping cables?  Network cables can go bad.

No, but I just installed it and will check it out. I did swap cables, I even used cat 7 cables. No difference at all.

This morning I tested again and this time speeds remained high. Downloading from the server at 72 MB/s, uploading to it at 55,5 MB/s. Probably the differences are caused by different read/write speeds of the hd. Not bad for an old Compaq.
So apparently it wás some kind of hardware problem. I'll look into iperf and do some rigorous testing this weekend.

Thanks again for your input.

---

