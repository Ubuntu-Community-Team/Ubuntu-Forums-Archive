---
title: "Network Throughput"
date: 2017-01-09
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2017-01-09
Folks,

I am trying to resolve some network issues on my home network. My network consists of wifi including a repeater wifi device and some homeplugs.

Main computer is an Ubuntu laptop running 16:04 and I have three Raspberry Pi devices running Debian connected to homeplugs.

What is the best way to check throughput, is it Ping, iperf, dd if=/dev/zero bs=32 count=1048576 (or similar) or speedtest.net?

If using ping does the packet size affect results much?

Any suggestions appreciated.

Geffers

---

### Post by TheFu on 2017-01-09
Look at all parts of the setup.  What are the theoretical maximum throughput each can provide? Make a list.  Test each part alone. Try ideal and real testing.  For wifi, that means less than 5 ft away from the main wifi-AP.  Avoid wifi. Repeaters probably make it much worse.

I wouldn't bother testing the WAN speeds, until all the LAN concerns are handled/accepted.

Ping doesn't test throughput.
iperf is for best case testing. Real world will never get anywhere close.
dd is for copying bits to other bits or disk testing to my knowledge. For network testing, the protocol used and disk storage speed would matter more.

IMHO.

If you want to know about real-world transfer speeds, then transfer the real files in the way you'd transfer them in real life.  Maybe use 'time'.  I use rsync for stuff like this.  Add --stats --progress to see how fast things are going.  rsync works with local copies, over NFS, over sshfs and over ssh tunnels. Very convenient.

From my R-pi v2 wired to a gige network, I'm seeing 94.2 Mbits/sec, which is about as good as anything else with a 100Mbps connection. Raspberry pi architecture. [https://raspberrypi.stackexchange.com/questions/43330/raspberry-pi-usb-bus-speed](https://raspberrypi.stackexchange.com/questions/43330/raspberry-pi-usb-bus-speed)  basically, all USB, storage and networking share a single USB2 bus. Specs say 480Mbps, but real world that drops to about 300Mbps. I've never seen USB2 storage go faster than 30Mbps, usually it is much slower than that.  And wifi always sucks.  Always.  There are just too many variable involved to do any remote troubleshooting.  Over the years, I've written about all the issues with wifi here. I'm tired, don't want  to do it any more. 

Don't use wifi if you can avoid it.

---

