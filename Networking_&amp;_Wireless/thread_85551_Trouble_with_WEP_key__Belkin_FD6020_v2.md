---
title: "Trouble with WEP key :: Belkin FD6020 v2"
date: 2005-11-02
forum: Networking &amp; Wireless
---

### Post by Elling on 2005-11-02
Hi -

The card, a Belkin FD6020 is loading fine with the Atmel firmware. The iwlist scan command returns the AP (channel 1 - correct ESSID). The problem is inputting the WEP key and getting it to work. 

Under windows, using the Belkin software, I generated a 128bit key using a passphrase. The problem is that the HEX values are represented as '*' when you view it under windows. I dug through the registry and got a decimal value key and converted it to HEX -- it comes out the correct number of pairs.

I've tried it with all caps and colons between the values and without colons. No joy. Any help from a Belkin 802.11b user out there with making WEP work w/ubuntu?

TIA!

---

### Post by Elling on 2005-11-03
I managed to get the belkin up and running by entering the correct WEP key :rolleyes: 

The card flashes quite a bit, though. It stays lit solid under windows. But it's working, so no complaints ... until I upgrade to Breezy ...

---

