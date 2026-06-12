---
title: "Trouble Connecting To Network In Gusty"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by Palshife on 2007-10-21
Hello everyone! I'm a recent convert to Ubuntu and Linux, and while there has been quite the learning curve, I am steadily getting used to the whole Unix thing.

Where I'm having the most trouble is with wireless--a common problem, I understand. Somehow I was able to get it working properly under Feisty. Had to do a network reset to get it going, but better than it not working at all. But when I upgraded to Gusty, it stopped working at all!

My network is encrypted under WPA2 using AES encryption and does not broadcast its ESSID. I tried using the built in network manager, selecting the appropriate options (WPA2 Personal, AES-CCMP) to no avail, then tried manual configuration (Password type WPA2 Personal, DHCP configuration) with the same result. I even tried using the old method of edting the interfaces file, making sure to add wpa-ap-scan 2, wpa-pairwise CCMP, wpa-group CCMP, and wpa-psk with my hex passphrase, and still nothing.

Have I missed something, or is this a known issue with Gusty so far?

My apologies if posting this isn't appropriate, and thanks in advance to any response.

---

