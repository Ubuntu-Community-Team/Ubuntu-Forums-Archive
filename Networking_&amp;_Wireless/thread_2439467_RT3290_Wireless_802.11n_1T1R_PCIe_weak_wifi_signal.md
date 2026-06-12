---
title: "RT3290 Wireless 802.11n 1T/1R PCIe weak wifi signal - Ubuntu Budgie 18.04 LTS"
date: 2020-03-28
forum: Networking &amp; Wireless
---

### Post by cpagrawal28 on 2020-03-28
Hi 
I am running Ubuntu Budgie 18.04 on my HP Pavilion G6 laptop. I am facing problems with wifi. The wifi signal is poor and the range of wifi signal varies time to time while the laptop and wifi router are placed at same location all the time. With the variation of signal there is variation with link speed too which causes problem when I work on laptop. 
I have done a lot of research on this topic but no success so far. most of the results are for different RTL devices. can anyone please help me on this ? 
Thank You.

---

### Post by praseodym on 2020-03-28
Lets try
```

echo 'options rt2800pci nohwcrypt=1' | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```

---

