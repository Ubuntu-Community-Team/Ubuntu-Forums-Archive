---
title: "Mount NFS from specific interface"
date: 2024-05-22
forum: Networking &amp; Wireless
---

### Post by apatel415 on 2024-05-22
I have a VM with 2 NICs. One is 1G the other is 10G. They are on the same subnet. I have a NAS on the same subnet. and have exported the share to the IP od the 10G NIC. But the nfs mount always initiates from the 1G NIC. I would think there's an easy way to do this but have searched high and low to no avail. Anyone had a suggestion? Yes, I could just run everything through the 10G but I want to figure this out.

---

### Post by TheFu on 2024-05-24
Normally, if there are two NICs on the same network, then they'd be identical models with the same bandwidth.
If they aren't on the same subnet, then routing tables would be used to determine which interface is used for traffic on that subnet.

Easy is subjective.  You'll need to "bound" both interfaces to a single IP.  This also means that your switch will need to support bounding.  It is an 802.something standard.  However, the performance per transfer will be limited to the NIC used at the time. Quality NICs seldom fail.  In decades working with thousands of servers inside data centers, not once did a NIC fail ... er... that wasn't caused by human misconfiguration.  There's no fix for that.  Of course, some cheapo NICs fail.  I've had the most commonly used PC NIC models fail multiple times.  Of course, they didn't actually fail, then caused data corruption for a few weeks before we traced the error to the NIC.  The fix for that is never use the cheap, most-popular NIC vendor that 90% of PC motherboards have built-in.

If redundant connections are so important, then you should also have the same NICs in that redundant set.

---

