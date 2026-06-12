---
title: "wlan gone?"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by mgame2k on 2008-04-01
So I'm running 7.10 everything is going great. Then I guess my cpu just got to hot. The computer shut down. This means that the Linux didn't shut down properly. When it came back on my wireless card wasn't listed anymore.

If I do lsmod I can see the module still running. If I do lspci I can see that the card itself is still installed. However, if I go into network control. I only see the eth cards. Wireless card ra0 or wlan0 completely not listed.

Anyone here have any idea how to fix this problem? If anything I guess I can reinstall and start completely over. I'd like to use that as a last option.

---

### Post by prshah on 2008-04-01
> **mgame2k said:**
> 
If I do lsmod I can see the module still running. If I do lspci I can see that the card itself is still installed. However, if I go into network control. I only see the eth cards. Wireless card ra0 or wlan0 completely not listed.

Were you using ndiswrapper or was your card natively supported?

If you were using ndiswrapper then do ```
sudo modprobe ndiswrapper
``` otherwise "sudo modprobe whatever-your-card-driver-is".

If you don't know your card driver, ```
lspci | grep -i wireless
``` will give us a clue.

---

### Post by mgame2k on 2008-04-01
my card is natively supported. I couldn't find my windows cd to get the inf file for the ndiswrapper.

---

