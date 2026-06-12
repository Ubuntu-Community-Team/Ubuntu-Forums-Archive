---
title: "gstreamer audio packet size too small"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by mhs1pk on 2009-09-17
Hi everyone,

First of all sorry if i dont follow some rules but this is really my first post on any forum :)

Following is my gstreamer pipeline:

```
gst-launch-0.10 audiotestsrc do-timestamp=true ! msgsmenc ! msgsmpayloader  min-ptime=2000000000 ! udpsink host=127.0.0.1 port=2222 sync=false bytes-to-serve=1300 preroll-queue-len=1000
```I receive the packets locally on my machine and process them. The problem is that the rtp packet size is very small and I receive a lot of packets. What is needed is that more data is combined in one udp packet ( multiple rtp packets in on udp packet ) and then sent by gstreamer. But I cannot seem to be able to tell it somehow.

As you can see I have tried different parameters but no success.

Please help me out here!!!

Regards,
Hassan

---

### Post by nicolargo on 2009-09-28
Hi mhs1pk,

do you found a solution for this issue ?

Nicolas

---

### Post by mhs1pk on 2009-09-28
No, not yet :(

---

