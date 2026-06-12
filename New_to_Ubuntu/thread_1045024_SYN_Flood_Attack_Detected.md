---
title: "SYN Flood Attack Detected"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by S0m3th1ngw13rd on 2009-01-20
While looking through my router logs I noticed a lot of:
 
Jan/19/2009 23:47:29 	SYN Flood Attack Detect	 	 	 Packet Dropped
Jan/19/2009 23:47:28 	SYN Flood Attack Detect	 	 	 Packet Dropped
Jan/19/2009 23:47:27 	SYN Flood Attack Detect	 	 	 Packet Dropped
Jan/19/2009 23:47:26 	SYN Flood Attack Detect	 	 	 Packet Dropped


got a little bit worried did a little research and determined that it is coming from using ShieldsUp. Wasn't 100% sure, so I went back to [https://www.grc.com](https://www.grc.com) and clicked the All Service Ports scan thing again. Sure enough the logs immediately showed it was from them. After this I started breathing normal again. Whew. Learning more and more by the minute.

---

### Post by jrusso2 on 2009-01-20
Its just a port scan. Not a syn flood.  Its being misinterpreted as that.

---

