---
title: "Wireless connection WEP: Shared issues"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by jmetal88 on 2006-12-09
I am attempting to connect to my 2Wire wireless router using a Linksys WPC11 v 4 card on Xubuntu 6.10 with my router set to WEP: Shared, and it isn't working. It works fine on WEP: Open, but using that option makes me unable to connect my Nintendo DS via the Nintendo WFC, and that is something I would really like to be able to do. Windows XP connects fine with WEP: Shared enabled on my router.

Can someone help me figure out how to make Linux pick up my connection on this card when WEP: Shared is enabled?

Thanks!

---

### Post by jmetal88 on 2006-12-10
I felt the need to mention that I have also tried WiFi-Radar and Wireless Assistant, and neither were successful (even when selecting shared key on Wireless Assistant). Anyone have any ideas yet?

---

### Post by FrodoB on 2006-12-10
Edit the /etc/network/interfaces file and find the line where your WEP key is set and change it to:

wireless-key restricted XXXXXXXXXXXXXXXXXXXXXXX

Where the xxxx is you current WEP key, which you do not touch and add the word restricted as shown above.

Start the editor from a terminal window:

 sudo gedit /etc/network/interfaces



Use sudo ifdown wlan0 and sudo ifup wlan0 to test, change wlan0 to your interface name.

---

