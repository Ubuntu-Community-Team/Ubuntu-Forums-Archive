---
title: "A question about iperf3"
date: 2016-09-16
forum: Networking &amp; Wireless
---

### Post by cazz on 2016-09-16
I have a question about the tool iperf3

When I use it 
**iperf3 -c x.x.x.x**
I get then some nice information about the speed in my network
It also give me two value

*sender* and *receiver*

I know what the sender is but the value of receiver is that the same as -R?

I mean I can use reverse like
**iperf3 -c x.x.x.x -R**
to see the upload speed from the client to the server but if I just need to run one command then it is greate.

---

### Post by TheFu on 2016-09-16
iperf lies.  I've never gotten the throughput it claims I'll get. Never.  If you want to see how quickly the systems and network can push data across, then get some sample data of the type and size you'll be pushing and use that.  Many transfer tools have statistics built in.

iperf lies, but if you want the max possible, never attainable throughput, then I suppose it can be useful.  It does provide a consistent check.

So if you use **rsync** to move data (and you should!), use the --stats and --progress options. Very helpful.

For your specific questions, I'd have to read the manpage - and suspect everyone else here would too.  My installed version of iperf (v2.0.5) doesn't have the -R option. It does have the -r option and the manpage says: 
```
       -r, --tradeoff
              Do a bidirectional test individually

```

I generally use -s for the server-mode.  But don't forget that iperf lies. You'll never see that throughput.

---

