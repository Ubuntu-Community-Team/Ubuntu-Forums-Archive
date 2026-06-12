---
title: "Help with my Network!"
date: 2004-11-11
forum: Networking &amp; Wireless
---

### Post by andy_sp1ke on 2004-11-11
Hi

In my past attempts at Linux i have never managed to get my wireless card to work, Ubuntu so far has done more than the others as it has detected my PCMCIA card. Ok Heres the details, 

The card is a Belkin F5D6020 and its a B rated card. The device manager in Ubuntu has found the card and provides the following infomation on it, it looks to be fully loaded up and installed. Just not activated. 

IWconfig returns results saying that no wireless extensions are present? how do I create a Wlan0 to appear next to the eth0 in Ubuntu? the guides I have found for linux in general tell me to add some lines to /etc/sysconfig/network-scripts ([http://www.siliconvalleyccie.com/linux-hn/wmp11-linux.htm](http://www.siliconvalleyccie.com/linux-hn/wmp11-linux.htm)) but that folder is not on Ubuntu for me? Any help would be greatly appreciated. 

Andy

Have looked to see what modules are loaded (LSMOD) and refering to the pcmcia bus is

yenta_socket           19328  1
pcmcia_core            63156  2 ds,yenta_socket

---

### Post by Enygma on 2004-11-11
Have you tried ndiswrapper? It allows you to use the Windows driver in Linux.
Check out the Ubuntu Ndiswrapper Howto here: [http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-07.7773155363](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-07.7773155363)

Follow that and you should be able to set up wlan0 without any problems.

---

### Post by spirospr on 2004-11-11
Well i don' t know much but because i'm trying to set up my wireless card i can give you some resources i have found.

As i saw here [http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz) your card is supported and it is based on a Amtel chip. visiting this site could supply some information :

[http://atmelwlandriver.sourceforge.net/news.html](http://atmelwlandriver.sourceforge.net/news.html)

also

[http://www.ubuntuforums.com/showthread.php?t=785&highlight=wifi](http://www.ubuntuforums.com/showthread.php?t=785&highlight=wifi)

If you make some aditional reasearch at the forum you will find more information.

Good luck....

---

### Post by spirospr on 2004-11-11
Well i don' t know much but because i'm trying to set up my wireless card i can give you some resources i have found.

As i saw here [http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz) your card is supported and it is based on a Amtel chip. visiting this site could supply some information :

[http://atmelwlandriver.sourceforge.net/news.html](http://atmelwlandriver.sourceforge.net/news.html)

also

[http://www.ubuntuforums.com/showthread.php?t=785&highlight=wifi](http://www.ubuntuforums.com/showthread.php?t=785&highlight=wifi)

[http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-07.7773155363](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-07.7773155363)

If you make some aditional reasearch at the forum you will find more information.

Good luck....

---

