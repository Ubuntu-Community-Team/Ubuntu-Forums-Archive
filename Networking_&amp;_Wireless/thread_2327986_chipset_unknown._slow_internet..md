---
title: "chipset unknown. slow internet."
date: 2016-06-16
forum: Networking &amp; Wireless
---

### Post by lord_aizen on 2016-06-16
Hello. Newbie on ubuntu.
I just bought Dell-vostro i5 ubuntu 14.04 LTS. The wifi is very slow and  just installed aircrack-ng.
airmon-ng cannot detect 
 chipset=unknown,. How can I speed up my wifi? And is it possible to install drivers like atheros/realtek drivers?

airmon-ng 
chipset=unknown driver= iwlwifi- [phy0] (monitor mode enabled on mon0)

---

### Post by ajgreeny on 2016-06-16
What does ```
sudo lshw -c network
``` show

---

