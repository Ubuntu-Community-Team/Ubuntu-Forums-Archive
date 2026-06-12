---
title: "wireless not working after updates process"
date: 2014-05-14
forum: Networking &amp; Wireless
---

### Post by Nico_Zambrano on 2014-05-14
Hi All

I have Ubuntu 12.04. After downloading updates from Ubuntu Software  Center my wireless is not working. Before downloading the updates it was  working fine. Now I am not able to see the Mobile Network and Wireless  option, though Wired connection is working fine. Please help me to  resolve this problem. I dont know how to fix it and sorry about my poor english. :confused:

---

### Post by varunendra on 2014-05-17
Welcome to the forums Nico_Zambrano!

As a wild guess based on some experience, please try this first -

Open a terminal (Ctrl-Alt-T) and run the following command in it -
```
sudo apt-get purge bcmwl-kernel-source
```
Then reboot and see if your wifi is working again. If yes, this fix is permanent and you don't need to do anything else. Just remember NOT to install the proprietary driver (also called "wl" or "STA" driver) for your card again (else the problem will be back, and the fix will be same as above).

However, if it does not get your wireless back, please run the following commands in the terminal and post back their outputs here -
```
uname -mr
lsb_release -d
lspci -nnk | grep -iA2 net
lsusb
lsmod
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

