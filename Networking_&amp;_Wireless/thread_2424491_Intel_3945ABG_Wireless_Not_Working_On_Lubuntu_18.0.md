---
title: "Intel 3945ABG Wireless Not Working On Lubuntu 18.04.3 LTS"
date: 2019-08-09
forum: Networking &amp; Wireless
---

### Post by fecavy on 2019-08-09
Hey there,

I am unable to get my Intel 3945ABG Wireless card working on Lubuntu 18.04.3 LTS with the latest updates installed.

My install is a fresh install - I did not change anything related to networking.

My device is a Medion MD96350 (WIM 2140) Notebook PC, if that's helpful.

I followed the instructions before posting an ran the wireless info script. Its output can be found [here]("https://paste.ubuntu.com/p/Hm4fspP92m/").

The network manager GUI in the bottom right corner displays a message like "Device is not ready" in the wireless networking section.

Can anyone help me with this?

Help is very appreciated.

---

### Post by fecavy on 2019-08-12
Any ideas?

---

### Post by chili555 on 2019-08-12
> **fecavy said:**
> Any ideas?Not really.

I suspect that the reason that your question got no replies at all is that your paste shows absolutely nothing wrong at all. We see nothing remarkable and therefore fixable.

The only thing I see that is a remote possibility is that you have a working ethernet connection. I suspect that Network Manager will default to the faster and more secure ethernet. Please try detaching the ethernet and reboot. Does the interface scan?```
sudo iwlist wlp10s0 scan
```Are there any clues in the log?```
dmesg | grep -e iwl -e wlp
```

---

