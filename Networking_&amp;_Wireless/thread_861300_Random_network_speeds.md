---
title: "Random network speeds"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by nry on 2008-07-16
Got samba running on my file server running ubuntu.

Yesterday was getting
35MB/s read
25MB/s write

Was happy with this over my gigabit network.

Today it has gone back to 8MB/s

This seems to be happening everyday and it only works at full speed when it want's to.

What would cause this?

---

### Post by VorDesigns on 2008-07-16
Hi,

Depending on many factors your results will vary depending on file size, server load, client and server configuration, suns spots and gremlins.
You didn't mention how large or small the file sizes were so, diagnosing what issues you may have are would be no more than armchair quarterbacking at best.
There are some tweaks that you can apply as far as buffering and rfc adjustments; take a look at nitro.ucsc.edu for links to documentation that will assist you with steps you can take to eliminate the OS as your culprit.
You will not reach maximum throughput with smaller files.
You will note that speeds will ramp up incrementally depending on your client/server configuration as capabilities are negotiated.
Once you have done all that you dare at the OS level, it is time to look at the capabilities of the systems hardware and underlying infrastructure.
I have seen mid range managed 10/100 switches out perform consumer grade gigabit switches and I've seen poorly configured managed switches drag large networks down to a crawl.

---

### Post by nry on 2008-07-16
Well both computers loads are basically minimum. 
I know the netgear gigabit switch I am using can easily perform at 35MB/s as it does so between my laptop and HTPC daily with files ranging from 1GB to 14GB

The files I am using are 4GB and 8GB, both are what was used yesterday to test speeds when I was getting 20MB/s+ so not much has changed on that front.

Also tred installing windows xp on a seperate drive and using this in the server, got 20MB/s onto that drive no problem, with no tweaking.

---

### Post by nry on 2008-07-16
Rebooted the ubuntu machine and it started working how it was before with the fast speeds.

Rebooted it again.

Back down to 8MB/s

Did iperf between the server and my laptop

Laptop running -s = 408Mbits/s
Server running -s = 340Mbits/s

Just did it again after the reboot and 
Laptop running -s = 71Mbits/s
Server running -s = 131Mbits/s

So something funny is going on the server side.

No idea whats going on.

Might just see about switching to WHS at this rate lol

---

