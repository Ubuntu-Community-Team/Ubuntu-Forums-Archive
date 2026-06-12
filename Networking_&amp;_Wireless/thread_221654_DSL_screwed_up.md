---
title: "DSL screwed up?"
date: 2006-07-23
forum: Networking &amp; Wireless
---

### Post by shultzjr on 2006-07-23
Hi all,

I just setup a U606 box to connect to a Speedstream 5100 connected to att/sbc/yahoo account.  It required pppoe.  I got that configured correctly and the computer could browse.  I went away and I get this call, can't browse the Internet.  Error message is:

plugin rp-pppoe.so loaded.
pppd 2.4.4b1 started by root, uid 0
timeout waiting for pads packets
unable to complete pppoe discovery

I restarted computer once before and everything worked.  Now, all of a sudden it doesn't.  What is going on, and how do I fix it?  I have already tried pppoeconf and it didn't help.  What file do I edit to make sure pppoe starts when the computer is turned on and what do I want to put in that file?

thanks,
charles.....

---

### Post by mips on 2006-07-24
Best option would be to configure the speedstream to do the pppoe & authentication.

---

### Post by shultzjr on 2006-07-24
> Best option would be to configure the speedstream to do the pppoe & authentication.

How do I do that?

thanks,
charles.....

---

### Post by mips on 2006-07-24
Well if you point me to the PDF manual then I could help you.

We also need to know your ISP VCI/VPI details.

---

