---
title: "need help connecting print server to business network"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by max_power on 2007-11-07
im trying to hook up a hp directjet print server to a business network which is using a 10.0.0 scheme but the factory settings for the print server are on a 192 scheme. How can I access the web admin interface on the print server if im on a different ip scheme?

i have tried plugging directly into the print server but i still cant ping it. what am i doing wrong here?

thanks

---

### Post by max_power on 2007-11-07
**SOLVED**

What you do is go to command line and type:

route add 192.0.0.192 10.0.0.(what ever ip you want to reserve)

---

