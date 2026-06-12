---
title: "Ubuntu 8.04 Alpha6 with Intel4965AGN wireless of Thinkpad T61"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by indiglo on 2008-03-19
Hi. I installed the ubuntu 8.04 alpha6 on my Thinkpad T61 which have a Intel 4965AGN wireless card. I thought this wireless should work out of the box. However, I could not find the "wlan0" interface after use command "ifconfig". It seems that my 4965agn card didn't recognized. 

Can anyone guide me how to make it works? 
Some messages as follows:

Kernel: 2.6.24-12-generic

# ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

# modinfo iwl4965 | grep version
version:        1.2.0
srcversion:     BFF70BD669F5E9D76F2C9C1

# lspci
...
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
...

Thanks.

---

### Post by honeydew on 2008-03-19
could it of assigned a different name?   run    ```
 ifconfig -a
```  this should give you a list of interfaces.. everyonce in a while after a install I find that it asigns it something obscure like wlan2.. why this happens I have yet to figure out.

---

