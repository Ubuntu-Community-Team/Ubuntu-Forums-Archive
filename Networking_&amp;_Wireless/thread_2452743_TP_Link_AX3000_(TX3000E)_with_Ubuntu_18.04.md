---
title: "TP Link AX3000 (TX3000E) with Ubuntu 18.04"
date: 2020-10-27
forum: Networking &amp; Wireless
---

### Post by bwill1350 on 2020-10-27
Hello,
I'm still fairly new to Linux so I'm still having some trouble determining what's possible and what's not. I have a leftover TP Link TX3000E wireless/Bluetooth card that I wanted to try to get working on my Ubuntu 18.04 machine. I got it installed into the PCI-E slot and the Bluetooth functioned flawlessly with no additional setup. Unfortunately, the wi-fi capabilities did not. Now according to the TP Link website, it's only out-of-the-box compatible with Windows 10. However, I know from research that the card uses the Intel AX200 chipset and drivers which the Ubuntu kernel should be compatible with. 

So, is there a workaround here that would be reasonable to attempt or am I better off just finding a different wireless card made for Linux? Thanks in advance.

---

### Post by CelticWarrior on 2020-10-27
[https://askubuntu.com/questions/1149116/intel-wifi-support-for-ax200-cyclone-peak](https://askubuntu.com/questions/1149116/intel-wifi-support-for-ax200-cyclone-peak)

---

### Post by bwill1350 on 2020-10-27
Thanks for your response! 
Forgive my lack of experience, but I'm not sure I properly installed the package. Based on the instructions, I installed the PPA with the commands::
[COLOR=#333333]sudo add-apt-repository ppa:canonical-hwe-team/pc-oem-dkms
[/COLOR][COLOR=#333333]sudo apt-get update
Then ran 
[/COLOR]dpkg -l | grep backport-iwlwifi-dkms

I confirmed that I am using the 4.15 kernel and I did reboot my system. The wi-fi settings menu is still saying "No Wi-Fi Adapter Found". Any idea what I may have done wrong? Thanks

---

### Post by morrownr on 2020-10-28
Have you considered backing up your important files and then doing a clean (format) installation of 20.04? That might be easier than what you are trying to do and it should "just work" with 20.04.

---

### Post by bwill1350 on 2020-10-28
I have, actually. I initially installed 20.04 but there were some weird driver issues. I'm pretty sure I could resolve whatever the problem was at this point, I've just been putting it off. This seems like as good of an excuse as any to give it another go, though Will give that a shot after work and update here, thanks.

---

### Post by chili555 on 2020-10-28
Let's find the exact identity of your card:
```
lspci -nnk | grep 0280 -A3
```

---

### Post by Blix775 on 2021-01-01
HI! I am considering buying this card and I need to know if it works in Ubuntu 20.04. Can you give an update on if it worked?

---

### Post by Blix775 on 2021-01-12
I just bought the AX3000 ( after doing my research) and it works out of the box. You just need the kernel 5.1 or later. The speed on the thing is very nice and it receives the signal well.

---

