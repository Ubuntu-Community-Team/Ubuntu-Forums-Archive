---
title: "[SOLVED] How can I monitor my outgoing internet traffic?"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by Absorbed on 2007-07-04
I install Ubuntu Feisty yesterday, have installed Firestarter, and it keeps blocking incoming bittorrent traffic:

Time: Jul  4 11:25:29 Source: 83.xx.xx.xx Destination: 10.0.0.6 In IF: eth0 Out IF:  Port: 6881 Length: 42 ToS: 0x00 Protocol: UDP Service: BitTorrent
Time: Jul  4 11:27:59 Source: 84.xx.xx.xx Destination: 10.0.0.6 In IF: eth0 Out IF:  Port: 6881 Length: 48 ToS: 0x00 Protocol: TCP Service: BitTorrent
Time: Jul  4 11:29:23 Source: 74.xx.xx.xx Destination: 10.0.0.6 In IF: eth0 Out IF:  Port: 6881 Length: 93 ToS: 0x00 Protocol: UDP Service: BitTorrent

This just continues indefinitely, a new incoming connection every 1/2 minutes. I'd like to find out whether there are outgoing bittorrent connections coming from my computer, so I can stop them, or if it is something else. Is there a command or program I can use to check this?

---

### Post by oimon on 2007-07-04
there is a simple utility called iptraf that will show you the incoming and outgoing traffic.
sudo apt-get install iptraf 
then run iptraf from a terminal window.

also, running the netstat -an command should show you the tcp port connections established/waiting etc

---

