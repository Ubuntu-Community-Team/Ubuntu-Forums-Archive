---
title: "dropped packets"
date: 2015-11-21
forum: Networking &amp; Wireless
---

### Post by adagio on 2015-11-21
A quick networking question.

If `ifconfig` reports 20% dropped packets on a download - could this cause a file transfer that should be 50Mb/s to slow down to at most 1Mb/s?

---

### Post by ian-weisser on 2015-11-21
Dropped packets are not the cause. They are merely another symptom.
The packets are being dropped for a reason. Malformed by server, garbled in transit, etc.
That reason may (or may not) also be the cause of reduced bandwidth.

---

