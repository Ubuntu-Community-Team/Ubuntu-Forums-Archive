---
title: "Broadcom wifi card doesn't like WEP"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by ddumanis on 2007-11-09
Hi,

I have Gutsy with one of those built-in Broadcomm wireless cards everyone looooves (mine is 4309)...it works fine on unencrypted connections, great in fact, but when I try to hop on a WEP-encrypted connection it just spins and spins, and then the password dialog box comes back... then I enter it, and the password dialog box comes back again.. etc.

Oddly, I didn't have this problem in Feisty (I don't think).

 I'm using the driver that's automatically installed with the restricted drivers manager, and connecting through Network-Manager. Does anyone have better experience with ndiswrapper instead, or some kind of secret tweakage?

Thanks for any help... I would file a bug but thought I'd ask here first.

---

### Post by kevdog on 2007-11-09
Have you tried connecting from the command line to take potential problems with network manager out of the loop??  I cant tell right now if its the driver, network manager, or some interaction between the two.  Command line instructions available in my signature,

---

### Post by toasterboy1 on 2007-11-23
ddumanis sorry to piggyback on your post but I am having similar issues with gutsy and broadcom wireless. I can connect to my wpa protected network at my house but was unable to connect to wep at the hotel or in-laws. It says it is connected but was unable to ping the default gateway or surf the internet. I am using gutsy and wicd and had tried statically assigning the ip address and obtaining it though dhcp. I had not had problems with feisty and wicd before.

kevdog I will also try the command line method next time I am able to.

Update: Could not access with command line. Which made me think I had some serious problem. But seems to work with WICD 1.3.8.

---

