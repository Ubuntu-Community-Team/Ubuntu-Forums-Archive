---
title: "Wifi not working in Ubuntu 13.10!"
date: 2013-12-18
forum: Networking &amp; Wireless
---

### Post by bigtinyman on 2013-12-18
Hi all,

I'm a new Linux and Ubuntu user. Installed the OS a few days ago. I'm using Ubuntu 13.10, and am having issues connecting to wifi. I know it's not a router issue, as all my other devices (including this computer on the Windows OS) can connect to the wifi. Only Ubuntu cannot. I did some research, and it looks like a lot of other users are experiencing the same problem. I tried some of their tips for fixing the problem, nothing worked out, or I didn't understand how to do what they recommended. So I'm here asking for more help.

Detailed description of the problem: I try to connect to wifi. I select the wifi I want to connect to, and when prompted for the password, I type it in and hit "connect". The prompt box will disappear, and the wifi icon in the upper right corner will animate as if trying to connect. Shorty after, the same prompt box appears again, and asks to enter the password again, and without surprise, the wifi is not connected. This will happen repeatedly.

My dear internet friends, how can I fix this problem?

---

### Post by tfrue on 2013-12-20
Just a quick question, is your WiFi card USB or PCI?

Please post the ouput from these commands,

If PCI, open a terminal and type:
```
lspci
```
If USB, type:
```
lsusb
```

And one last one:
```
ifconfig -a
```

---

