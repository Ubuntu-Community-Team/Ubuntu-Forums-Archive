---
title: "[SOLVED] Unable to connect Riger DB108-WL"
date: 2014-07-09
forum: Networking &amp; Wireless
---

### Post by dunkuk_gelay on 2014-07-09
Hello... My laptop is Inspiron 14R, and the  wireless adapter is Dell Wireless 1705 802.11b/g/n (2.4GHZ). I'm unable to connect to my friend's wifi network (Riger DB108-WL) which is only happened with Ubuntu 14.04 but there's no connection issue with Win 8.1.

However, both Ubuntu and Win 8.1 doesn't have issue with my three other router at home. One is Asus, and I forgot the other two. 

The symptom I having is the signal bar is very low but my laptop is only few meter from the modem. Even my phone detect full bar wireless signal from this position. Then it took a long time to connect but end up disconnected. I already turn on/ off, disconnect and reconnect but no success. Do let me know what do I need to include so that you guys can help me. Thank you.

---

### Post by patsev-anton on 2014-07-12
lspci -knn | grep "Eth\|Net" -A2

---

### Post by dunkuk_gelay on 2014-07-14
> **patsev-anton said:**
> lspci -knn | grep "Eth\|Net" -A2

06:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Dell Device [1028:020c]
    Kernel driver in use: ath9k
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 08)
    Subsystem: Dell Device [1028:05f3]
    Kernel driver in use: r8169

BTW problem solved and I don't know which one is the culprit. I suspect it's the modem itself but just wondering why Windows and Android doesn't have problem. 

1) Reset the modem to factory restore and change the channel. Previously I just reboot the modem but it doesn't work. Last time I can't reset because I don't have the account detail for re-configuration.
2) Delete wifi history. I just delete my friend's wifi in network list. 
3) Disable and re-enable back the wifi. Skipping this will cause connection error. 
4) Connect to that particular wifi. 

Thank you so much for those who reply.

---

