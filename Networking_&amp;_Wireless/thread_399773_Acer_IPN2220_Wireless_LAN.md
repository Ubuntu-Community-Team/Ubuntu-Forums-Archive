---
title: "Acer IPN2220 Wireless LAN"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by fishboy on 2007-04-02
[FONT="Comic Sans MS"]Hello,

I'm new to the Linux front and Ubuntu Front and have succesfully installed the os on my lappy however i have been trying to install the wireless card before you ask yes it is supported and have installed the driver nearly when i put in the terminal "ndiswrapper -l" it responds: neti2220 driver installed, hardware present then i move on to "sudo depmod -a" this seems to be ok seeing as i just move on so then i enter "sudo modprobe ndiswrapper" this is where i get the problem it responds "FATAL: Module ndiswrapper not found" i installed ndiswrapper using Synaptic PAckage Manager can any one shine some light on the situation.

btw i am a complete newbie! 

Thanks Luke[/FONT]

---

### Post by Floppyjoe on 2007-04-02
What is the output of:
```
ndiswrapper -v
```
This should show you version information.

---

### Post by fishboy on 2007-04-03
utils Error: no version specified!
driver modinfo: could not find module ndiswrapper

---

### Post by patrickfromspain on 2007-04-06
After installing the driver, you have to do sudo ndiswrapper -m and then you can modprobe it.

---

### Post by Floppyjoe on 2007-04-06
> **fishboy said:**
> utils Error: no version specified!
driver modinfo: could not find module ndiswrapper

According to this Ndiswrapper is not installed on your system.

---

