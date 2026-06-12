---
title: "[SOLVED] Help! Can only see certain websites while browsing [weroam]"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by nepenthes on 2007-12-10
Hi all,

I am in the Philippines using a 2G/3G mobile flatrate (PLDT weroam) with my cellphone (Nokia E70/6120) connected via USB.
I am able to connect with Ubuntu using wvdial on one laptop and GPRSec on the other one. However I can reach only a VERY FEW websites, for example [www.inquirer.net](www.inquirer.net), [www.google.com](www.google.com),  [www.starfall.com](www.starfall.com) works. Most other pages don't work.

With Windows XP I had the SAME problem. PLDT send me the following Registry patch (below) that made it work perfectly.
I was wondering if any of the experts here can help me apply this registry tweak to Ubuntu.

Thanks a million,
Nepenthes


[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\NdisWan\Parameters\Protocols\0]
“ProtocolType”=dword:00000800
“PPPProtocolType”=dword:00000021
“TunnelMTU”=dword:000003f4
“ProtocolMTU”=dword:000003f4

---

### Post by Lostincyberspace on 2007-12-10
Can you ping google?

---

### Post by nepenthes on 2007-12-10
Hi,
Thanks for answering. Sorry I was offline, couldn't connect to ubuntuforums without windows *sigh*

I can ping everything without problems. In Firefox I get the "looking for" "connecting to" and then "waiting for" and that' s it.

Google actually also opens with ubuntu (I' ve corrected my statement above). Further does [www.starfall.com](www.starfall.com), CNN (partially). Probably 10% of all pages. The rest only works with a patched windows. It also works on the browser in my cellphone.

---

### Post by Lostincyberspace on 2007-12-10
Try turning turn off Ipv6 search for it in  about:config.

---

### Post by nepenthes on 2007-12-10
No, didn't work. 
Aside from the webpages I can also not access the repositories etc.

---

### Post by nepenthes on 2007-12-12
Ok, I am writing this from beloved Ubuntu connected to my Nokia, opening all websites effortless... :)

Solved the problem by lowering MTU size in /etc/ppp/options
There is an entry '# mtu <n>' changed it to 'mtu 1456'
and it worked immediately using wvdial to connect. Saw some topic, where it recommends to keep on increasing MTU until it stops working, to find optimal MTU. Optimal MTU provides faster internet. The default 1500 was to high for my ISP/Setup.

Thanks all!

PS: Got the MTU hint from the registry patch above.

---

