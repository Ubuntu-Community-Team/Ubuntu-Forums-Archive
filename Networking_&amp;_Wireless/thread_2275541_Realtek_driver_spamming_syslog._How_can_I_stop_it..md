---
title: "Realtek driver spamming syslog. How can I stop it."
date: 2015-04-27
forum: Networking &amp; Wireless
---

### Post by mts2 on 2015-04-27
I recently installed an Edimax AC1200 Pci-E wireless adapter. This uses the realtek rtl8821.ae driver.  
This is spamming my syslog and I would love someone to tell me how to stop these continuous messages.    

Apr 27 13:52:52 mts-ubuntu kernel: [12253.919877] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband(): 5G   
Apr 27 13:52:53 mts-ubuntu kernel: [12255.271616] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband(): 2.4G   
Apr 27 13:53:55 mts-ubuntu kernel: [12316.905993] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband(): 5G   
Apr 27 13:53:56 mts-ubuntu kernel: [12318.257738] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband(): 2.4G   
Apr 27 13:54:58 mts-ubuntu kernel: [12379.888113] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband(): 5G   
Apr 27 13:54:59 mts-ubuntu kernel: [12381.239826] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband(): 2.4G    

As can be seen above these messages are recorded every minute. Is there a way to stop these kernel messages.  
I have searched online but not found an answer. I hope somebody can help.    

Thanks in advance.

---

