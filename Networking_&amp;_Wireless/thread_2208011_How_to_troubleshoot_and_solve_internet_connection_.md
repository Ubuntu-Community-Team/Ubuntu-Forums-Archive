---
title: "How to troubleshoot and solve internet connection problem using any browser"
date: 2014-02-26
forum: Networking &amp; Wireless
---

### Post by ps14003 on 2014-02-26
No matter which browser I use, I am unable to use the internet. My modem is working fine and the wired connection is recognized. After restarting the system few times, it starts working again.


How can I troubleshoot and solve this issue? Is it in the 'configure VPN' menu under networks indicator?

---

### Post by varunendra on 2014-02-27
When the internet doesn't seem to be working, please post the outputs of the following commands (to be entered in a 'Terminal', which you can open with 'Ctrl+Alt+T' keys) -
```
uname -mr
lsb_release -cd
sudo lshw -numeric -C network -sanitize
ifconfig -a
nm-tool
route -n
cat /etc/network/interfaces
ping -c4 8.8.8.8
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

