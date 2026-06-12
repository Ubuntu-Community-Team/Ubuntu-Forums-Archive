---
title: "Can't connect to WPA networks"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by yg17 on 2008-08-24
I just got an Inspiron 1525 with the 1395 wireless card and can't connect to WPA networks. I followed [these instructions]("http://ubuntuforums.org/showpost.php?p=5358575&postcount=2") to get wireless working, and I can connect to unsecured networks, but I can't connect to both WPA1 and WPA2 networks. I enter the password, the Network icon in the toolbar shows a green and a blue dot and has the little thing moving for a few seconds, then it just goes away. No error messages or anything. I'm definitely entering the right password, so I'm not sure what's wrong. wpasupplicant is also installed. Any advice? Thanks

---

### Post by mk2 on 2008-08-25
I had the exact same problem on my inspiron 1525. After some searching, I came across this post ([http://ubuntuforums.org/showthread.php?t=704088]("http://ubuntuforums.org/showthread.php?t=704088")) and it solved the problem for me. It seems that the the restricted driver is causing the problems, so first deactivate the restricted driver, reboot, and follow the instructions in the post.

---

### Post by yg17 on 2008-08-25
Thanks. I was able to get it working with ndiswrapper.

---

