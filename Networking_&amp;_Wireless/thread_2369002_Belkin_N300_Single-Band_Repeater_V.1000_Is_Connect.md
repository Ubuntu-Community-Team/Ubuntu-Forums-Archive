---
title: "Belkin N300 Single-Band Repeater V.1000 Is Connected But Says No Internet Access"
date: 2017-08-17
forum: Networking &amp; Wireless
---

### Post by davidrqgamer on 2017-08-17
First off right now I am connected to internet from my belkin the problem is that it loses internet access usually every day multiple times however the connectivity to the repeater stays on most of the time. I have also noticed that if chrome says no internet access or privacy issues if I reload my connection to my belkin repeater the internet comes back on instantly. However it is common for the internet to go back down within 25 seconds after I have internet again.... strange thing is some days I have good internet all day. Internet speed is not an issue when it is working it is fast. Also the internet on my phone only very rarely loses internet access when connected to repeater, in other words internet will be working on android cell but not on linux. I do have security enabled on my repeater as well as router. I will post the wireless info scripts below please tell me what is wrong with my repeater or computer.

[ATTACH]276429[/ATTACH]

Thank you.

---

### Post by praseodym on 2017-08-18
Try these module parameters:

```
echo "options rtl8821ae swenc=1 swlps=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl88821ae_options.conf
```
Reboot

---

### Post by davidrqgamer on 2017-08-18
Well i just pasted that in terminal then restarted my computer I guess ill find out if it fixed it. Can you please explain what those commands did?

---

### Post by davidrqgamer on 2017-08-18
Its still going down....if I leave it on trying to connect to website it seems to eventually auto retry connecting to website and succeed though dont think it did that before

---

