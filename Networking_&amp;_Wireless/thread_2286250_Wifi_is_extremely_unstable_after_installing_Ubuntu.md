---
title: "Wifi is extremely unstable after installing Ubuntu on a Windows machine"
date: 2015-07-10
forum: Networking &amp; Wireless
---

### Post by matthayzon on 2015-07-10
Recently installed Ubuntu on a windows machine and I am now getting  really weak and unstable wifi signal, which previously worked perfectly.
My machine is an HP Envy 15. My Ubuntu version is 14.04 (Unity). The  wifi seems to magically disconnect at random times or take a really  really long time to load a page, I'm basically getting dial up speeds.

  I appreciate any help on resolving this as this is really  frustrating. Let me know if I can include any additional information  from terminal that may help.

The following command: ```
lspci -knn | grep Net -A2
```

Returns:


```
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:197d]
    Kernel driver in use: rtl8188ee
```


I appreciate any suggestions, thanks in advance!

---

### Post by Vladlenin5000 on 2015-07-10
Hi and welcome.

Please read this discussion about the same adaptor in a similar machine: [http://ubuntuforums.org/showthread.php?t=2242121](http://ubuntuforums.org/showthread.php?t=2242121)

---

### Post by matthayzon on 2015-07-11
I appreciate the reply. I tried the advice in the provided post with no success, any other ideas?

---

### Post by psfal on 2015-09-08
I went through a bunch of posts on this issue. I have the same wireless adapter in my HP 450-a24, the only thing that worked was replacing my router, as others have done. [http://ubuntuforums.org/showthread.php?t=2289993&highlight=RTL8188EE+Wireless+Network+Adapter](http://ubuntuforums.org/showthread.php?t=2289993&highlight=RTL8188EE+Wireless+Network+Adapter)
I replaced my old Linksys E2500 router with a new Netgear N900 router and the issue is gone for me. I know this doesn't address the actual faulty driver that caused it in the first place but it's the only answer I found searching the posts on this issue that worked... Best of luck to you :-)

---

