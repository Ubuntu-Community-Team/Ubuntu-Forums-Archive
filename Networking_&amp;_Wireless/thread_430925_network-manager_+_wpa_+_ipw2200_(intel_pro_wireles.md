---
title: "network-manager + wpa + ipw2200 (intel pro wireless)"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by bjorn2k on 2007-05-02
Hi, I have a dell inspiron 9300 laptop (centrino) with the intel pro wireless 2200 (ipw). I managed to get WPA/TKIP to work with this card on ubuntu 6.10 (wpa-supplicant editting some config files).
Last month i ran 7.04 beta on my laptop. With wpa-supplicant i managed to get it work again (editting config files and al that).
But, everywhere on forums i read that this should work out of the box with the network-manager on feisty fawn (7.04), without the hassle of manually editting config files.
So, i installed the new feisty fawn and double clicked on the correct SSID in the network manager and i get the same problem again -> enter your WEP key. I'm 100% sure that i have to enter a WPA/TKIP key. How can it be that it asks for a WEP key? And how can i fix it? Is there a way to manually override it? (without editting config files).

---

### Post by tmagee16 on 2007-05-03
I have the same computer with the same WPA Enterprise challenge.  I need to reference a certificate file as well.  Not to be too ridiculous, but how do you verify that the 9300 is seeing the Intel 2200 card correctly?
I'll watch to see if someone give you an answer to your question as well.

---

### Post by bjorn2k on 2007-05-04
Kind of fixed it. With roaming enbaled i can enter the wpa key. If i use network-manager it still doesn't work.

---

