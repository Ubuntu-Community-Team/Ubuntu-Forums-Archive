---
title: "Packet File Capture and decode with AIM"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by matthew1429 on 2008-10-17
My daughter is using AIM w/o logging and we are concerned with some relationships that have come into her life.  Is there a way to capture packets on my LAN and see what kind of conversations are occurring?

I have an Ubuntu box running on the same LAN.  I've got Wireshark and Ettercap but haven't googled info on how to configure.  I also don't know how to capture packets.

Am I barking up the right tree?  Can anyone recommend any guides/resources to better train myself?  Wireshark is definitely not an out of the box solution as I have to see why it can't see my 'interfaces' which is eth0/eth1 I assume.

Any input would be appreciated.

---

### Post by iponeverything on 2008-10-17
Its very easy if don't care about easy to read output ;)

Here is a better solution:

ref: [http://arstechnica.com/articles/columns/linux/linux-20051002.ars](http://arstechnica.com/articles/columns/linux/linux-20051002.ars)

If it's a switched network or your wireless card does not support monitor, you could keep it running in the background on her machine and have it write to log. Though having a gateway machine running linux that can be bottle neck for the traffic might be better.

(I am not sure about the visibility of traffic on wireless networks..)

Just had another thought. -- Put the gateway/router on different ethernet segment, put a secondary address on your interface that is on the routers segment -- turn on ip forwarding on machine and have all the machines on your network set to use your box as the default gw.  This way you can passively monitor, if the traffic is not easily visible on the wire..  Another thing you could do is pick up a good old fashion hub -- and have your box share it with the gateway/router..

---

### Post by bruno386 on 2008-11-10
not sure bout aim, but ive successfully  sniffed msn conversations from my other clients on my lan.

step 1)
ettercap MITM attack/arp poison.

step 2)
wireshark to sniff the re-routed packets, which were not encrypted when i tried this, showing me full msn conversations.

---

