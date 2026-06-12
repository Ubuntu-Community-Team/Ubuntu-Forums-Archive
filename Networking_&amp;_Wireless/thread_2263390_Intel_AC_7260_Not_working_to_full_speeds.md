---
title: "Intel AC 7260 Not working to full speeds"
date: 2015-01-31
forum: Networking &amp; Wireless
---

### Post by richard103 on 2015-01-31
Recently, I installed Xubuntu 14.04 on my laptop and noticed that when updating, for example my wireless speeds were not as good as on ethernet. On ethernet I could get around 900kb/s while on my ac7260, the speed was only about 350kb/s. I've tried updating firmware and doing all sorts of dns tweaks and such but not much has helped. Does anyone have any suggestions? Thanks.

---

### Post by weatherman2 on 2015-01-31
What kind of access point (wireless router) are you connecting to, and how is security setup?

If you are using an 802.11n access point, and it is secured, you should be using WPA2 Personal + AES (unless you are using some sort of enterprise form of WPA2).  If you use WEP or WPA (not WPA2) or TKIP not AES, you will slow to 802.11g speeds - maximum 54Mbps.

Also, what is the output of this command:

```
sudo grep iwlwifi /etc/modprobe.d/*
```

?

---

### Post by richard103 on 2015-01-31
I am using a 2.4ghz technicolor router and have WPA-2 security setup. 

For the command, this is what I get:
/etc/modprobe.d/iwlwifi.conf:# /etc/modprobe.d/iwlwifi.conf
/etc/modprobe.d/iwlwifi.conf:# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
/etc/modprobe.d/iwlwifi.conf:# microcode file installed on the system.  When removing iwlwifi, first
/etc/modprobe.d/iwlwifi.conf:# remove the iwl?vm module and then iwlwifi.
/etc/modprobe.d/iwlwifi.conf:remove iwlwifi \
/etc/modprobe.d/iwlwifi.conf:(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \

---

### Post by richard103 on 2015-01-31
I solved the problem by going into iwconfig and turning power management off. Thanks for your help though.

---

