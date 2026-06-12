---
title: "Ethernet controller: Realtek Semiconductor didn't connect"
date: 2014-07-04
forum: Networking &amp; Wireless
---

### Post by shamsat on 2014-07-04
I upgraded the ubuntu 14.04 kernel from linux-3.13.0-29-generic to linux-3.13.0-30-generic, now the LAN is no more connecting, the ethernet card is:
> 
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)

and driver loaded is:
> 
# lsmod | grep r816*
r8169                  61562  0 
mii                    13654  1 r8169


---

### Post by varunendra on 2014-07-04
And what is the output of -
```
sudo lshw -numeric -C network
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by shamsat on 2014-07-05
Thanks for the reply the new kernel also have problem with sound card so i just fall back to the old kernel linux-3.13.0-29-generic it is working fine.

---

### Post by varunendra on 2014-07-05
Glad you found a solution. Please mark the thread as [SOLVED] using "Thread Tools" link above the top post. Thanks for the feedback! :)

---

