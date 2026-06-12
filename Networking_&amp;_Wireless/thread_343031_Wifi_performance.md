---
title: "Wifi performance"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by bkeithly on 2007-01-20
Anyone know of any tricks that can speed up my wifi?

I have a G network, but I rarely get over 300k.   Not a massive deal, but it would be nice when I am trying to move larger files....

---

### Post by teaker1s on 2007-01-20
are you using native linux driver or ndiswrapper?

---

### Post by RandomJoe on 2007-01-20
Have you ruled out environmental causes?

Is the AP sitting next to a 2.4GHz cordless phone system or microwave?  Or perhaps even a computer that operates in that range.  Or just next to a lot of other electronic gear (that's going to generate noise regardless).  I had my AP in my "server closet" along with several computers and lots of electronic gear initially, but got mediocre performance.  My problem was more range than speed, but I found by moving it out of the closet to another location in the house both improved dramatically.

Are you trying to move the files between two computers sharing the same AP?  Wireless networking is half-duplex, and only one radio can talk at a time so you definitely take a speed cut when talking between to machines on the same AP.  In very rough terms, 56Mbps (G) is only really going to give about 28Mbps real throughput, cut that in half again since the AP has to parrot everything the first machine sends it so 14Mbps.  You should still be seeing better than your apparent 3Mbps, of course.

I'm assuming you are referring to transferring files between two machines of your own.  Obviously, if you mean downloading files, your Internet connection bandwidth is the restriction.  I only mention this because I've had people forget that their cable/DSL connection isn't as fast as the wireless...

---

### Post by bkeithly on 2007-01-25
Hey thanks for the suggestions.

I trouble shot wifi networks for hotels for a while and I totally agree with all your interference theories.

But the odd thing is I pretty much get the same speed even if I am right next the the AP.

I know freebsd has a "high perfomance" ssh patch that is supposed to bust ssh/scp and other forms of SCP transfer performance...

---

### Post by bkeithly on 2007-01-25
Oh ya I am using Ndiswrapper...

Is this known to effect performance?

---

