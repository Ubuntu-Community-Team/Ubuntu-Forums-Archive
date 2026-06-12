---
title: "Live CD - wireless connection problem"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by owise1 on 2008-11-07
I tried the 8.10 version of Xubuntu (and later ubuntu with same results) with an older machine with a netgear wireless card.  I have used that card with ndiswrapper successfully with other linux distros.

Firstly the live CD does not have ndiswrapper available from startup - bit dumb but I found that I could install via synaptic from the CD.  Ran the driver install and modprobe ndiswrapper brought up a new interface waln0 as expected.  The Network Manager tool then picked up the card and showed my wireless network.  A click or two plus the WEP key and the applet shows that I am connected - woohoo.  Clicking properties showed an IP address and all looked well....but there actually was no connection.

Could not ping the router or any external address.  ifconfig showed no ip address but iwconfig showed card associated with my network and the WEP key.  NOt sure what is going on here.  Any suggestions??

Dave

---

### Post by owise1 on 2008-11-10
I appears that there is a problem with the way network headers have changes in the latest kernel release in 8.10 - see below:

From [http://lwn.net/Articles/304791/](http://lwn.net/Articles/304791/)

"The problem stems from changes that were made to clean up the TCP option code that were merged back in July as part of the 2.6.27 merge window. TCP options are a mechanism to expand the functionality of the protocol as conditions change. There are a handful of commonly used options that the two endpoints of a connection can agree to use, for things like maximum segment size (MSS), window scaling, selective acknowledgment (SACK), and timestamps. Options have been added over time to provide more internet robustness and performance as well as to support higher-bandwidth physical connections.

A perfectly reasonable, if unintended, consequence of the code change was that the the options were put into the header in a slightly different order. According to the relevant RFCs, options can appear in any order in the option section of the TCP header. But, some home and/or internet routers seem to expect a fixed order; refusing to make connections if the order is "wrong". In particular, it would seem that the MSS option needs to appear before the SACK option."

It appears that a lot of punters are having wireless probs after upgrade.  Will be trying the work-around later tonight to see if that works by turning off TCP timestamps- 

sysctl -w net.ipv4.tcp_timestamps=0

Cheers

Dave

---

