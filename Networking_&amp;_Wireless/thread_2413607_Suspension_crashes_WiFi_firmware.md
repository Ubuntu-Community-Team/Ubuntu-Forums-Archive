---
title: "Suspension crashes WiFi firmware"
date: 2019-02-27
forum: Networking &amp; Wireless
---

### Post by darwinii on 2019-02-27
Whenever I put my laptop into suspension my WiFi card is killed, as to be expected. However when waking my laptop network manager reports "device not ready." Further probing gives me an error stating my firmware has crashed, as well as "failed to reset chip: -5".

Running the three commands,
```

sudo rmmod ath10k_pci
sudo modprobe ath10k_pci
sudo ifup -a

```   

makes network manager report "device not managed".

I have already tried ```
sudo systemctl restart Network-Manager
``` to no avail.

Dell's OEM kernel did not have this issue, and if indeed this cannot be fixed, how can I go about installing Dell's linux kernel?

---

