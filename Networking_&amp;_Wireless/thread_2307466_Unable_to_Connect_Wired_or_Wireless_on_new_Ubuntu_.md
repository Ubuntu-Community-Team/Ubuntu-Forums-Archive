---
title: "Unable to Connect Wired or Wireless on new Ubuntu Server (LTS) Installation"
date: 2015-12-25
forum: Networking &amp; Wireless
---

### Post by robo731 on 2015-12-25
I'll start by warning you that I am brand new to Ubuntu and Linux. I have looked at several potential solutions so far, but none have been successful so far. I have managed to get both network interfaces "up" such that ```
lshw -C network
``` no longer says disabled next to each interface heading. That's all I've been able to do so far. My network is secured with WPA2, but even the wired connection is not working.

---

### Post by kc1di on 2015-12-26
What wireless card is the server using?  
of

---

### Post by praseodym on 2015-12-26
Please run the wireless-script as shown in the footer of kc1di

---

### Post by robo731 on 2015-12-29
The wireless card is an Intel Centrino Wireless N-2230.

I am unable to connect to the internet at all so I downloaded the script and put it on a USB. I'm not sure what to do next though. The directions are for Ubuntu, but I'm running Ubuntu Server, so I'm restricted to the CLI with no desktop or GUI.

Also, sorry for my late response. I was away for a few days. Thank you for replying.

---

### Post by praseodym on 2015-12-29
Alternatively, please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
```
as screenshots to show the hardware

---

### Post by robo731 on 2015-12-30
Here's the output[IMG]http://puu.sh/mdVkG/3097d32aa9.jpg[/IMG]

---

### Post by chili555 on 2015-12-30
Please see: [http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552)

---

### Post by robo731 on 2015-12-30
That did the trick. Thank you so much. Is there a way to set it up for lan as well such that it will connect via lan if an ethernet connection is availible and will connect via wireless if not?

---

### Post by chili555 on 2015-12-31
> **robo731 said:**
> That did the trick. Thank you so much. Is there a way to set it up for lan as well such that it will connect via lan if an ethernet connection is availible and will connect via wireless if not?There may be but it's beyond my limited expertise. You might start a new thread.

---

### Post by robo731 on 2015-12-31
Will do. Thanks for the help.

---

