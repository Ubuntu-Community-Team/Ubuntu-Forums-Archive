---
title: "wireless card not enabled"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by foobard on 2008-10-20
OK, so I've done some digging on solving this problem and I'm stuck. What happened is this. I upgraded my hardy install to Intrepid Beta two days ago. The upgrade killed my wifi connection.

So. Intel wireless card, Broadcom ethernet card. 

  lshw -C network

indicates that the wireless card is not enabled.

  ifconfig wmaster0 up

gives me the error message:

  SIOCSIFFLAGS: Operation Not Supported

I have googled and googled and I'm stuck. Any ideas?

thanks

---

