---
title: "Dell D600 with Wifi but limited to 1Mb/s connection  rate - 8.04 Beta"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by fishfreek on 2008-04-20
Im running the 8..04 beta with a Dell D600 using a broadcom wireless card.  I have wifi working but when I look at the network manager connection details it says I am connected at a rate of 1Mb/sec instead of the 11Mb/s or 54Mb/s for 801.11b or g.  Something else I noticed is under the connection information it does not have any information listed for Driver.

I would like to get the speed of this connection up a bit as its hard to transfer files at such a low rate.

---

### Post by fishfreek on 2008-04-21
Anyone have an idea?

---

### Post by al_magest on 2008-04-21
I had the same problem, but with a different card.  You can try manually setting the data rate to 54 Mb, and test to see if speed improved.  Try:
```
sudo iwconfig wlan0 rate 54M
```
If that doesn´t work, you might have to roll your own 2.6.25 kernel, which apparently fixes quite a few wireless issues present in 2.6.24, the kernel Hardy Heron uses.

Or, just do what I did and go back to 7.10.

---

### Post by fishfreek on 2008-04-22
Thanks.  That appeared to have worked.  Im gonna restart and see if it holds.  Now it reports 54Mb/s as the connection speed and a ftp transfer verifies its faster than before by far.

---

