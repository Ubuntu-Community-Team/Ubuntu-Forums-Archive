---
title: "sudo modprobe ndiswrapper"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by Frogster on 2008-06-07
Good evening

Can somebody tell me how to make this permanent? 

I have a windows driver and ndiswrapper installed but to get the wireless network working I have to use the command "sudo modprobe ndiswrapper"

I have to do this every time I start the machine.

I know its going to be a real simple fix :)

---

### Post by Ayuthia on 2008-06-07
> **Frogster said:**
> Good evening

Can somebody tell me how to make this permanent? 

I have a windows driver and ndiswrapper installed but to get the wireless network working I have to use the command "sudo modprobe ndiswrapper"

I have to do this every time I start the machine.

I know its going to be a real simple fix :)

Is ndiswrapper in /etc/modules?  You can check by doing the following (in the Terminal):
```
cat /etc/modules|grep ndiswrapper
```If it does nothing, then you need to add it:
```
echo ndiswrapper|sudo tee -a /etc/modules
```

---

### Post by Frogster on 2008-06-07
Thank you:)

---

