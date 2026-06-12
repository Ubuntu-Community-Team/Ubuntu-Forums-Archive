---
title: "wireless performance in ubuntu 10.04 netbook with realtek rtl8187se wireless card"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by cmackay on 2010-04-17
Hello:

I tried to install ubuntu netbook edition 10.04 beta 2 on an msi wind u100, with a Realtek RTL8187SE wireless device. Using both live cd and final installation, the wireless connection last about 3 or 4 minutes tops. I have been googleing and it seems that this has been problem since 8.10. Other people say that it might be a problem with WPA encryption but i have the same problem with WEP.

I also tried to use ndiswrapper with Win drivers through ndisgtk, blacklisting the rtl8187se module first. The hardware was detected, i was able to see my router but unable to connect to, both using WAP or WEP

Does anyone knows how to solve this issue? Is there a specific driver that should be compiled that actually works? 

Thanks

---

### Post by readycarpenter on 2010-04-17
many wireless drivers are proprietary, which ubuntu will only package open source. there are a few generic open source drivers that are installed, but are not as solid as the manufacturers. 

did you see if there are any proprietary drivers via
system>admin>hardware drivers

cheers

---

### Post by cmackay on 2010-04-17
There are no propietary drivers in use, at least no one is displayed.

---

### Post by readycarpenter on 2010-04-17
are you online? can you get online via a wired connection, just long enough to run system>admin>hardware drivers.

these "hardware drivers" are proprietary drivers, and will not list any available unless you are online, then it will download from another server, so that ubuntu is not including proprietary drivers, but gives an alternative that does not go against there open source policy.

cheers

---

### Post by cmackay on 2010-04-17
Hello RC

I checked again online and there are no propietary drivers in use or available. What i did about an hour ago was to boot a live session with 9.04 to see how the wireless worked. It worked like a charm for over an hour with no problem at all. I made an lsmod and the rtl8187se was loades, the same one loaded in 10.04. The only difference I found was on the kernel 2.6.28-11 on 9.04 and 2,6,32-19 on 10.04. Could be this a kernel issue instead of a particular driver issue?

---

