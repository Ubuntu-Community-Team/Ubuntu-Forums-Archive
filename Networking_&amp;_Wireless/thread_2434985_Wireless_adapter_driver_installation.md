---
title: "Wireless adapter driver installation"
date: 2020-01-14
forum: Networking &amp; Wireless
---

### Post by pbcrow1 on 2020-01-14
Hi, I recently installed Ubuntu (version 18.04, I believe) on a new computer. I did it as a single boot installation to overwrite what was on the computer previously. After doing this, I'm unable to connect to wireless internet. From looking around online, I believe that the issue is that the driver for the wireless card on my computer (I believe Realtek RTL8821CE) was overwriten or otherwise erased. I've looked online for a few different approaches to solve this, but have been unable to find one that works so far, as I get some error messages when I attempt to solve the issue but I don't understand what the error messages mean.

I'm still relatively new to Ubuntu, but am trying to learn what I can, and would appreciate any assistance. Thanks.

---

### Post by CelticWarrior on 2020-01-14
[https://askubuntu.com/a/990571](https://askubuntu.com/a/990571)

---

### Post by pbcrow1 on 2020-01-14
Thank you for replying. I went to that link and followed the steps, however I got some error messages and it doesn't appear to have worked. The first issue that I ran into was, for the part of the link where it says "Scroll down to line 152 and change the line...", when I scrolled down to that line in the nano makefile screen, I didn't see the text that was listed out, but instead saw something similar yet different. I made the prescribed change anyways though, and then continued with the other instructions, but it didn't work out. Below are the results from the terminal window when I was going through this part. I see that there are "errors" listed, but I don't know what these errors mean (my apologies if the below is an incorrect way to load terminal window information into a post).

parker@parker-HP-All-in-One-24-f0xx:~/Downloads$ cd rtl8821ce
parker@parker-HP-All-in-One-24-f0xx:~/Downloads/rtl8821ce$ nano Makefile
parker@parker-HP-All-in-One-24-f0xx:~/Downloads/rtl8821ce$ nano Makefile
parker@parker-HP-All-in-One-24-f0xx:~/Downloads/rtl8821ce$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-74-generic/build M=/home/parker/Downloads/rtl8821ce  modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-74-generic'
/home/parker/Downloads/rtl8821ce/Makefile:2157: home/parker/Downloads/rtl8821ce/hal/phydm/phydm.mk: No such file or directory
/home/parker/Downloads/rtl8821ce/Makefile:2166: home/parker/Downloads/rtl8821ce/rtl8821c.mk: No such file or directory
make[2]: *** No rule to make target 'home/parker/Downloads/rtl8821ce/rtl8821c.mk'.  Stop.
Makefile:1580: recipe for target '_module_/home/parker/Downloads/rtl8821ce' failed
make[1]: *** [_module_/home/parker/Downloads/rtl8821ce] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-74-generic'
Makefile:2237: recipe for target 'modules' failed
make: *** [modules] Error 2
parker@parker-HP-All-in-One-24-f0xx:~/Downloads/rtl8821ce$ sudo make install
[sudo] password for parker: 
install -p -m 644 8821ce.ko  /lib/modules/4.15.0-74-generic/kernel/drivers/net/wireless/
install: cannot stat '8821ce.ko': No such file or directory
Makefile:2243: recipe for target 'install' failed
make: *** [install] Error 1
parker@parker-HP-All-in-One-24-f0xx:~/Downloads/rtl8821ce$ sudo modprobe 8821ce
modprobe: ERROR: could not insert '8821ce': Required key not available

---

### Post by jeremy31 on 2020-01-15
Disable Secure Boot in BIOS/UEFI settings, download and install [https://launchpad.net/~canonical-hwe-team/+archive/ubuntu/rtl8821ce/+files/rtl8821ce-dkms_5.2.5.2.1.30816.20190425-0ubuntu1_all.deb](https://launchpad.net/~canonical-hwe-team/+archive/ubuntu/rtl8821ce/+files/rtl8821ce-dkms_5.2.5.2.1.30816.20190425-0ubuntu1_all.deb)
Reboot

---

### Post by oldrocker99 on 2020-01-15
There is also ndiswrapper, which allows the Windows driver to be used by selecting the .INFO file from the driver folder, and worked every time for me a decade ago, before the vast majority of wireless drivers were included in the Linux kernel. Ndiswrapper is highly recommended by myself.

---

### Post by CelticWarrior on 2020-01-15
There's no need for ndiswrapper when there are native drivers.

---

### Post by CelticWarrior on 2020-01-15
And I just discovered I have the exact same one in a slim HP notebook, but running 19.10.

All I had to do was```
sudo apt install rtl8821ce-dkms
``` to install the missing driver.

---

### Post by pbcrow1 on 2020-01-15
Everyone, thanks for the help with this. Post #4 above ended up fixing the issue for me. Last question: I had to disable the secure boot as a part of that step. Am I correct in thinking that now that I've installed the driver, I can re-enable the secure boot? Or will that somehow interfere with the driver that I've installed?

---

### Post by CelticWarrior on 2020-01-15
> **pbcrow1 said:**
> Everyone, thanks for the help with this. Post #4 above ended up fixing the issue for me. Last question: I had to disable the secure boot as a part of that step. Am I correct in thinking that now that I've installed the driver, I can re-enable the secure boot? Or will that somehow interfere with the driver that I've installed?

No, you're incorrect. Secure Boot prevents the drivers from loading.

---

