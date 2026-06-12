---
title: "Slow Gigabit PCMCIA"
date: 2005-10-06
forum: Networking &amp; Wireless
---

### Post by Liquidcycle on 2005-10-06
I'm moving over to gigabit ethernet so that I can edit video off of a central RAID array stored in a closet.  i'm using a Dell 5160 laptop (maxed out, plenty of CPU power and ram) that I just upgraded to Breezy.  I wasn't able to find much information online about PCMCIA NIC compatibility in linux (what I did find was several years old, so basically not relevant), so I decided to break down and buy a bunch of NICs and return the ones that didn't work.  So far I have tried a TrendNET card and a Hawking card, with similar results:

In windows I have been able to get several streams of video running simultaneously, no problem.

In Ubuntu I have not been able to get smooth playback of even one stream.  It takes roughly 6 minutes to transfer a 1 gigabyte file.  Running nttcp:

     Bytes  Real s   CPU s Real-MBit/s  CPU-MBit/s   Calls  Real-C/s   CPU-C/s
l  8388608    0.71    0.01     94.5119   4474.5209    2048   2884.28  136551.5
1  8388608    0.72    0.04     93.6010   1720.9607    5819   8116.13  149224.3

     Bytes  Real s   CPU s Real-MBit/s  CPU-MBit/s   Calls  Real-C/s   CPU-C/s
l  8388608    0.45    0.01    149.6713   4474.5209    2048   4567.61  136551.5
1  8388608    0.45    0.04    148.2410   1766.3016    5776  12758.97  152024.0

The first results are through my built-in 100T connection, and the second set of results is from the gigabit card.  50% improvement... okay.  But I would expect (on a 32-bit bus) to at least be seeing around 500MBits/s or more here, right?

I'm wondering if there's something I need to install, though it seems to be handling speeds over 100MBit/s without a problem, so I can't imagine it's a driver issue.  I also have D-Link and Netgear NICs unopened, but the identical results on the first two NICs made me hesitant to play with them until I know what's going on here.

Also, I haven't set up the RAID array yet, so that isn't a factor (though, with these nttcp scores it seems irrelevant anyway).

Help!

---

### Post by Liquidcycle on 2005-10-06
Quick follow up:

In windows the same 1GByte transfer takes just over 60 seconds.  Thus:

Windows: 1000MB/60sec = 133MBit/s
Linux: 1000MB/360sec = 22MBit/s

This seems really bad...  I'm guessing in windows that the harddrive may be more of an issue than the bandwidth, though even that seems a bit low...

---

### Post by Mr. Electric Wizard on 2005-10-07
I'm kind of in the same boat as you, granted, my speeds are not as slow as yours...
I thought my Gigabit network would be a lot faster than it is currently.  I have been keeping at a steady 105Mb - 120Mb.
I have not tested from windows machine to windows machine yet though...

Hopefully somebody can shed some light on this issue.

---

### Post by Liquidcycle on 2005-10-07
Yeah, this is bizarre.  I would figure there might be a limit on speed because I'm using a 32-bit bus, but it shouldn't be this low.  I may have to try some alternate network setups to see if I can ferret this out.  I know that at least *part* of the problem is with this cardbus card in linux, due to the increase in speed in windows...

Also, I tried the D-Link last night with identical results.

The server is ubuntu breezy with a gigabit NIC.  The switch seems to clearly indicate that the links in both directions are gigabit.  It correctly indicates when they aren't.

Does anybody know of any way to test each system in isolation, rather than through the network?  This might help locate any issues above and beyond the Cardbus NIC support.

Thanks,
Adam

---

### Post by Liquidcycle on 2005-10-09
Bueller?  Bueller?

Anyone?

Help?

-Adam

---

### Post by Liquidcycle on 2005-10-12
Bumpity bump bump.

Somebody has to have *some* idea, right?  Is there anything else I can/should be testing?

-Adam

---

### Post by Mathboy on 2005-12-05
Same speed in both directions (to and from the Ubuntu server)?

---

### Post by Liquidcycle on 2005-12-06
Yeah, according to nttcp (and iperf, I think).  Windows (on the client) is the same in both directions as well, only _much_ faster.  It's almost definitely a TCP problem and not samba, and it appears that it's almost definitely an issue with the client machine.

---

