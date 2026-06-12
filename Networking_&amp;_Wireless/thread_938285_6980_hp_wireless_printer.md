---
title: "6980 hp wireless printer"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by justaguylinux on 2008-10-04
Hi just wondering how to reset my hp wireless 6980 printer.
had it up and working now the printer state says "idle" had this happen once before and beat the system untill i got it working again. i did a reinstall under windows and got it working under win but it still is "idle" in 8.04 ubuntu. any advise thanks
justaguy

---

### Post by Sub101 on 2008-10-04
On my HP printer I went to:
System ==> Admin ==> Printing ==> New

Then select AppSocket/HP Jetdirect and enter the IP of the printer leaving the port as is. (9100) That should be all there is to it.

---

### Post by justaguylinux on 2008-10-05
i tryed that and printer is still idle
the host is where the net location goes ?
the old setting was  hp:/net/Deskjet_6980_series?ip=192.168.2.4
the new setting is socket://http://192.168.2.3:9100
printer still show idle
thanks for any advise

---

### Post by Sub101 on 2008-10-05
I would try it without the http?

---

### Post by justaguylinux on 2008-10-05
Thanks i tryed a few things like removing http and so on than just added a new printer and cutpaste the old ip with 9100 behind it add it worked.

---

### Post by justaguylinux on 2008-10-05
thanks

---

