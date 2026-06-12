---
title: "How to use xsupplicant to connect to a 802.1x network?"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by David Shen on 2008-05-18
Hi,

I know the 802.1x network is usually used for wireless network, but my company used it for a wired network...

In windows, I need a certification file to access my company's wired network. I have used the 'openssl pkcs12' tool to convert a .pfx file used in windows to .pem file, which is needed in Linux. But I do not know how to configure the /etc/xsupplicant/xsupplicant.conf file...

My knowledge to this network system is very limited. Please some one help me!


Thanks,
David

---

### Post by kevdog on 2008-05-18
Can you use wpa_supplicant?  xsupplicant is very poorly supported -- their website has been updated in years!

---

### Post by David Shen on 2008-05-18
oh~~I searched with '802.1x' and 'wired network', and I see most results are about xsupplicant, so I think it is more up to date :)

thanks for reply. I will try later :D

---

### Post by David Shen on 2008-05-27
I tried my best...but without luck. Actually, my pc is behind a ISA firewall. But on ubuntu, it is shown as a "wired 802.1x" network. I just wonder if it is possible to use wpa_supplicant to connect to a ISA server?
Or, how can I set up my linux to work with ISA. Of cursor, I know how to browser the web using a proxy. But for other tasks, e.g. apt-get, that proxy just won't work. I do not have control over the ISA server, so I want to know if we have something like a ISA Client in linux.


Thanks!

---

