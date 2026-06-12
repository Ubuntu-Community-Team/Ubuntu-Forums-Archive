---
title: "Lubuntu on Inspiron 1525"
date: 2014-06-04
forum: Networking &amp; Wireless
---

### Post by spode2 on 2014-06-04
I have installed Lubuntu 14.0.4 on a Dell Inspiron 1525 and cannot get the wireless to work. I have tried the many  certain cures suggested, none of which work for me. 

I  am new to this, but the problem might be that when I go to Software  and Updates/Additional drivers, the Broadcom card has two choices, the  STA driver or do not use the card. I have removed the STA driver files with  Synaptic and command line but the software and updates package still insists on showing it rather than the b43 driver. This may not be the problem, but  the best I can get is an exclamation mark on the taskbar network icon. Ethernet  works fine, and so did the wireless under Windows. Card PCI ID is 14e4:4315 (rev 1)

I would welcome some diagnostic help, thanks.

---

### Post by mörgæs on 2014-06-04
Everything you need is in the sticky notes.

---

### Post by spode2 on 2014-06-05
Clearly not. I have done what they say and it does not work. That is why I posted here. Are you really sure that the notes apply to Lubuntu? It seems odd that the additional drivers tab always shows the STA driver, even when it has been thoroughly purged.

---

### Post by spode2 on 2014-06-05
I have found the problem, and how to get around it, but not the cure. The Network Connections preferences are not being applied to the card when they are saved. Using iwconfig to apply the ESSID and Key gave instant connection.

---

