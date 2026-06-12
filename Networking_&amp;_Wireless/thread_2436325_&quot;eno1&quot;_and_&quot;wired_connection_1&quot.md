---
title: "&quot;eno1&quot; and &quot;wired connection 1&quot;"
date: 2020-02-04
forum: Networking &amp; Wireless
---

### Post by alain.roger on 2020-02-04
Hi,


Since i upgraded kubuntu 18.10 to kubuntu 19.10, my network conection by default is not anymore "wired connection 1" but "eno1"
Eno1 appeared alone and has the same MAC address as wired connection 1.


i would like to DEFINITIVELY remove eno1 as existing connection as if eno1 connector is connected to internet (cable) my VPN connection fails everytime i launch it.
If i click on "wired connection 1" connect button, the eno1 dissapears and next i can click on VPN connection...in this case my VPN connection is successful.


So how can i remove DIFINITIVELY the eno1... i mean i do not want to see it back once i reboot my desktop.
thx

---

### Post by alain.roger on 2020-02-09
At every reboot of my computer the "eno1" is back :(

---

### Post by oldfred on 2020-02-09
What does this show?
networkctl -a

---

