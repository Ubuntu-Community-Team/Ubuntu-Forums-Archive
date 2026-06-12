---
title: "Can't connect to certain sites randomly"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by adobrakic on 2010-07-22
I have Linux Mint 9, 64-bit. I'll randomly lose the ability to connect to certain websites, and get redirected to my ISP's shitty search. For example, I'm currently trying to get to [www.pastebin.com](www.pastebin.com), and I get:

[http://ww11.charter.net/search?qo=pastebin.com&rn=cjdsdRLNhkVs1cH](http://ww11.charter.net/search?qo=pastebin.com&rn=cjdsdRLNhkVs1cH)

However, when I go to [http://isitup.org/pastebin.com](http://isitup.org/pastebin.com) , it says its working fine. I'm connecting through OpenDNS' servers, and I have those settings on my router. Could that be the problem?

---

### Post by Rubi1200 on 2010-07-22
Try changing to the Google DNS servers and see if it makes a difference:

> **Linux**

 In most modern Linux distributions, DNS settings are configured through Network Manager.
 **Example: Changing DNS server settings on Ubuntu**
 
[LIST=1]
[*]In the **System** menu, click **Preferences**, then click **Network Connections**.
[*]Select the connection for which you want to configure Google Public DNS. For example:
[LIST]
[*]To change the settings for an Ethernet connection, select the **Wired** tab, then select your network interface in the list. It is usually called **eth0**.
[*]To change the settings for a wireless connection, select the **Wireless** tab, then select the appropriate wireless network.
[/LIST]
[*]Click **Edit**, and in the window that appears, select the **IPv4 Settings** tab.
[*]If the selected method is **Automatic (DHCP)**, open the dropdown and select **Automatic (DHCP) addresses only** instead. If the method is set to something else, do not change it.
[*]In the **DNS servers** field, enter the Google Public DNS IP addresses, separated by a space: 8.8.8.8  8.8.4.4
[/LIST]


[http://code.google.com/speed/public-dns/docs/using.html#setup](http://code.google.com/speed/public-dns/docs/using.html#setup)

---

