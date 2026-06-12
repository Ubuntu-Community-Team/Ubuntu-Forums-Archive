---
title: "lenovo e485 running ubuntu 19.04 with rtl8822be:  &quot;no networks&quot; issue"
date: 2019-09-18
forum: Networking &amp; Wireless
---

### Post by neosoyo on 2019-09-18
hi guys, 

same problem as everyone regarding realtek drivers, i've updated the kernel and wifi stop working.

Wireless-info.txt: [https://pastebin.com/j9b64ufp](https://pastebin.com/j9b64ufp)

i tried to compile the driver from github but some concepts are new to me, like "blacklist" a module (how to do it?) and possible symbolic link error that could lead to "modprobe: error: could not insert 'r8822be': exec format error".

can someone please help me to figure out?

my actual status now is: i have rtlwifi_new compiled and (i supposed) installed in my system, i'm booting insecure (to running non-official modules, right?), but i really don't know if i handled modprobe correctly (the Wirelless-info shows rtl8822be module, not r8822be)..

ps: my smartphone can see a wi-fi hotspot created by notebook, but can't login.

best regards,
sbo

---

