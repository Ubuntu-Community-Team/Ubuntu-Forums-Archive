---
title: "Wireless Dropping"
date: 2017-11-29
forum: Networking &amp; Wireless
---

### Post by ponxer26 on 2017-11-29
Hello a week ago I made a post about having network issues,
This was resolved at the time, but as soon as I shut down and started again I had to do the fix again,

The code i was given was
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=2
iwlist scan | egrep -i 'ssid|level'
echo "options rtl8723be ant_sel=2"


Is there a way to make this run on Start up/make it stick permanently?

Thanks,

---

### Post by Hadaka on 2017-11-30
Hi please open a terminal then copy and paste one line at a time...

```
echo rtl8723be | sudo tee -a /etc/modules
echo options rtl8723be ant_sel=2 | sudo tee -a /etc/modprobe.d/rtl8723be.conf 
```
boot and test wireless
Thanks.

---

### Post by ponxer26 on 2017-12-03
Thank you very much appears to have worked.

---

