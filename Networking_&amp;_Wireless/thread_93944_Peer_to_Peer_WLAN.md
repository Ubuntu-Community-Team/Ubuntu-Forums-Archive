---
title: "Peer to Peer WLAN"
date: 2005-11-23
forum: Networking &amp; Wireless
---

### Post by arsya on 2005-11-23
Hi,

I have notebook with Wifi and I would like to make connection ( peer to peer / point to point ) to another notebook with Wifi. Can somebody help me what to I should do to make it work.

Thanks in advance.

regards,
Arsya

---

### Post by mlomker on 2005-11-23
You can look through the man pages for iwconfig:  **man iwconfig**

I've never tried it, but you'll have to switch your card to ad-hoc mode using the **sudo iwconfig mode ad-hoc** command.  Because you won't have a DHCP server you'll have to statically set IP addresses, etc.  In short, it might be a bit tricky if you aren't networking savvy.

---

### Post by arsya on 2005-11-26
Thank you very much mlomker,

I have not read this man pages for iwconfig. I will do it later. So, ad-hoc mode is like a setting for using static IP mode for wireless, right?
Usually I use

iwconfig eth0 ...
dhclient...

in order to connect to the wlan using dhcp. But never tried this point to point connection.

Thanks again...


regards,
Arsya

---

