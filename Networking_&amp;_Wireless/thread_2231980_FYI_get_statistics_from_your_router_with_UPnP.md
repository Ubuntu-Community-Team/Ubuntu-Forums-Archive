---
title: "FYI: get statistics from your router with UPnP"
date: 2014-06-29
forum: Networking &amp; Wireless
---

### Post by sanderj on 2014-06-29
A FYI:

If your router has UPnP IGD activated, and you have the Ubuntu package "miniupnpc" installed, you can get traffic statistics from your router with:

```
upnpc -s

```

With some awk scripting, you can show the received Internet traffic bytes:

```
upnpc -s | awk '/Bytes/ { print $NF/(1024*1024) " MB received" } /No IGD/ { print $0 } '

```
Example results:

```
$ upnpc -s | awk '/Bytes/ { print $NF/(1024*1024) " MB received" } /No IGD/ { print $0 } '
4060.62 MB received
```

The counter seems to be 32-bit, or even 32-bit two's complement, so there is rollover

```
$ upnpc -s | awk '/Bytes/ { print $NF/(1024*1024) " MB received" } /No IGD/ { print $0 } '
378.168 MB received
```

If there is no UPnP IGD device, you will get this:

```
$ upnpc -s | awk '/Bytes/ { print $NF/(1024*1024) " MB received" } /No IGD/ { print $0 } '
No IGD UPnP Device found on the network !
```

Remarks:
- on at least two routers, I discovered only the wireless traffic was counted, not the wired traffic. :-(
- different people have different ideas about UPnP. I don't want to be involved in such a discussion. Please start your own thread.
- with some scripting, you can feed this info into MRTG

---

