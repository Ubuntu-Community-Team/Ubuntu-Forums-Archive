---
title: "Linksys wrt54Gt"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by rahulms on 2008-08-24
hi!
I have a Dell 1525 Ubuntu laptop. My problem is not able to save the wireless settings,so I saw a post and thought of using ndiswrapper to solve the problem. Only half way thru did I realize that I am not able to find inf and sys files for my router (wrt54G). I checked the CD and also the folder on my windows machine, the driver there does not work on mu ubuntu machine.
I am sure there is a way but this has been stalking my work.. any ideas guys!!

thanks in advance
rahul

---

### Post by caljohnsmith on 2008-08-24
Was wireless working fine before you used ndiswrapper, but you just weren't able to save your wireless network settings? Do you know what your wireless card chipset is? 

Please post the output of:
```
sudo lshw -C network
ifconfig
iwconfig
```

---

