---
title: "Broadcom BCM4312 with ndiswrapper problem"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by matthewbpt on 2008-07-22
I have a HP Pavillion dv9000 laptop with Broadcom bcm4312 wireless card. A few months ago I converted to Ubuntu Hardy from Vista and everything went smoothly, even the wireless was very easy to sort out with ndiswrapper once I found the installation instructions, and worked perfectly. Recently though the wireless has become temperamental, the problem is that half the time when I turn the laptop on the wireless card doesn't show up at all, the LED, which is blue when wireless is switched on, stays red no matter which way I have the switch turned, and the network manager doesn't register that there's a wireless card connected, but running lspci shows that Ubuntu knows its there. I have to keep restarting the computer until it finally shows up as connected, sometimes thats jsut restarting it once, but sometimes I restart it about 5 times! It's very inconvenient and I have no idea what the problem is! I used this guide to install the wireless originally [http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990) 
Maybe the problem is that since I installed it with ndiswrapper I've updated the kernel, so indiswrapper was installed on a different kernel...?
Can anyone help me out with this? it's getting very frustrating! Apart from this little problem Ubuntu has been great I'll never go back to Windoze or M$.

---

### Post by matthewbpt on 2008-07-23
*bump* anyone?

---

### Post by matthewbpt on 2008-07-24
*bump*

---

### Post by Ayuthia on 2008-07-24
> **matthewbpt said:**
> I have a HP Pavillion dv9000 laptop with Broadcom bcm4312 wireless card. A few months ago I converted to Ubuntu Hardy from Vista and everything went smoothly, even the wireless was very easy to sort out with ndiswrapper once I found the installation instructions, and worked perfectly. Recently though the wireless has become temperamental, the problem is that half the time when I turn the laptop on the wireless card doesn't show up at all, the LED, which is blue when wireless is switched on, stays red no matter which way I have the switch turned, and the network manager doesn't register that there's a wireless card connected, but running lspci shows that Ubuntu knows its there. I have to keep restarting the computer until it finally shows up as connected, sometimes thats jsut restarting it once, but sometimes I restart it about 5 times! It's very inconvenient and I have no idea what the problem is! I used this guide to install the wireless originally [http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990) 
Maybe the problem is that since I installed it with ndiswrapper I've updated the kernel, so indiswrapper was installed on a different kernel...?
Can anyone help me out with this? it's getting very frustrating! Apart from this little problem Ubuntu has been great I'll never go back to Windoze or M$.
If you compiled ndiswrapper (make, make install), you will need to compile it every time there is a kernel change.  If you installed ndiswrapper from the repositories (via synaptic or apt-get), it should be ok.  If you used the guide in your post, then you will need to recompile ndiswrapper.

---

