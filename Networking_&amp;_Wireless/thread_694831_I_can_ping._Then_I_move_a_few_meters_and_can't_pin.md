---
title: "I can ping. Then I move a few meters and can't ping. Signal is still very good."
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by rtoma on 2008-02-12
This one is strange.

5 meters away from the access point: 

1) I can scan for AP (iwlist scan)
2) I can connect (iwconfig eth1 essid .... key ....)
3) I can ping to the AP (ping 192.168.0.1)
4) I can ping to the net (ping [www.yahoo.com.ar](www.yahoo.com.ar))

Result: everything works

10 meters away from the access point:

1) I can scan for AP (iwlist scan) and signal is ok (77%)
2) I can connect (iwconfig ....)
3) I CAN'T PING to the AP
4) Obviously I can't ping to the net

Result: I loose the connection.


In windows it worked. So I assume it's not the hardware but the driver.

Any suggestion besides of trying other drivers? Did it happen to you, too?

I am working with a Dell Latitude D620 and the wirless hardware seems to be (lshw -C network) a: BCM4312 (but I am not so sure to beleive it... should I?)

Thanks in advance!!

---

