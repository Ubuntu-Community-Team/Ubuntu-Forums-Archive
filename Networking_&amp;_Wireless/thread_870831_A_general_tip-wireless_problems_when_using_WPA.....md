---
title: "A general tip-wireless problems when using WPA...."
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by nickdbliss on 2008-07-26
I see so many people are having problems using their wireless connections,when it comes to WPA-PSIK authentication method. I had similar issues before, with my **Broadcom Corporation BCM4312 802.11a/b/g (rev 01)**. Network manager was used and it would go into loop asking for password. With some lil modifications, it solved my problem. So i wanted to share what i did ,in a hope that it may work for you as well before you try something else. If it doesnt, then it was my duty to make you aware as a linux user. Cheers.

Here what i did:

1) I installed the windows driver using ndiswrapper. 
[http://ubuntuforums.org/showthread.php?t=827799](http://ubuntuforums.org/showthread.php?t=827799)

It was up n running fine. i was able to connect using no security. But when i equipped my router with wpa-tkip security, network manager was asking for password again n again.

2) After reading guides n google search, i found out that it was related to wpa_supplicant. But i already had wpa_supplicant installed. Did changes in wpa_supplicant.conf and interfaces files but it didnt work.

3) Eventually, i just reinstalled network manager, commented out everything in the interfaces file (/etc/network/interfaces) except
auto lo
iface lo inet loopback
and used to fill password in hex when network manager asked. 

End result: I am having a flawless wireless connection. Working fine ever since. Few other people i helped, used this and it worked for them. For some it didnt. 
Anyways, hope it works for you. Cheers.
It also worked with **Intel PRO/Wireless 2200BG card**.

---

