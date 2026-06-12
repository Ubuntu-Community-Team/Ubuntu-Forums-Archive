---
title: "Wireless connectivity lost again"
date: 2014-05-19
forum: Networking &amp; Wireless
---

### Post by Dada_Maheshvaranan on 2014-05-19
Dear friends, 

Two weeks after I reinstalled Ubuntu 14.04, I suddenly again lost sight of all wireless networks and the ability to plug in with an ethernet cable. It seems reinstalling everything didn't actually solve the problem.

I attach the wireless-info.txt file. I would be deeply grateful if someone can help me with this.

---

### Post by Hadaka on 2014-05-19
hi, please do..
```
echo "options nowhwcrypt=1" | sudo tee -a  /etc/modprobe.d/ath9k.conf
```

you also are missing your country code...you may fix that by entering it in place of the " XX "..must be uppercase
im in the us so mine is US.
**Country codes ->[http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)

```
sudo sed -i "s/REGDOMAIN=/REGDOMAIN=XX/" /etc/default/crda
```
BOOT
thanks

---

