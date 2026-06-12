---
title: "Wireless works but very slowly"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by spamzilla on 2007-08-26
I use a SMC2635w NIC for my laptop and it works fine in XP. However in Ubuntu, my connection is slower than a 56k connection and no where near as fast as it should be.

To get wireless access, I clicked connect in Wicd to my wireless network, and I get connected. However, I connect at 0%. I am not sure what is wrong, but I have noticed that on this new installation, I am no longer using "ra0" but instead "wlan0" interface. Could this mean I am missing the driver? If so how do I go about installing a driver for my smc2635w (blue verion 2) NIC?

edit: before now, this NIC has always worked out of the box, and a simple fix of turning off ipv6 in about:config gave me connectivity. This time around, I get connectivity, but a very slow connection.

Cheers :popcorn:

---

### Post by spamzilla on 2007-08-26
Does anyone have any ideas? I'm not using any encryption for now, so that's not the problem.

---

### Post by spamzilla on 2007-08-26
I have got around to trying to install the missing rt2400 driver. However, I have ran into a problem. When I enter 'make' into terminal, I get the following error:

> matt@matt:~/Desktop/rt2400-1.2.1/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-10-386'
  CC [M]  /home/matt/Desktop/rt2400-1.2.1/Module/rtmp_main.o
/home/matt/Desktop/rt2400-1.2.1/Module/rtmp_main.c: In function ‘RT2400_probe’:
/home/matt/Desktop/rt2400-1.2.1/Module/rtmp_main.c:96: error: ‘struct pci_dev’ has no member named ‘slot_name’
/home/matt/Desktop/rt2400-1.2.1/Module/rtmp_main.c:134: warning: passing argument 1 of ‘readl’ makes pointer from integer without a cast
/home/matt/Desktop/rt2400-1.2.1/Module/rtmp_main.c:135: warning: passing argument 1 of ‘readl’ makes pointer from integer without a cast
/home/matt/Desktop/rt2400-1.2.1/Module/rtmp_main.c:153: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/matt/Desktop/rt2400-1.2.1/Module/rtmp_main.c:169: warning: format ‘%lx’ expects type ‘long unsigned int’, but argument 3 has type ‘resource_size_t’
/home/matt/Desktop/rt2400-1.2.1/Module/rtmp_main.c: In function ‘RT2400_open’:
/home/matt/Desktop/rt2400-1.2.1/Module/rtmp_main.c:208: warning: ‘deprecated_irq_flag’ is deprecated (declared at include/linux/interrupt.h:66)
/home/matt/Desktop/rt2400-1.2.1/Module/rtmp_main.c:208: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/matt/Desktop/rt2400-1.2.1/Module/rtmp_main.c:258: warning: passing argument 2 of ‘writel’ makes pointer from integer without a cast
/home/matt/Desktop/rt2400-1.2.1/Module/rtmp_main.c: In function ‘RTMPIsr’:
/home/matt/Desktop/rt2400-1.2.1/Module/rtmp_main.c:378: warning: passing argument 1 of ‘readl’ makes pointer from integer without a cast
/home/matt/Desktop/rt2400-1.2.1/Module/rtmp_main.c:379: warning: passing argument 2 of ‘writel’ makes pointer from integer without a cast
/home/matt/Desktop/rt2400-1.2.1/Module/rtmp_main.c: In function ‘RT2400_set_rx_mode’:
/home/matt/Desktop/rt2400-1.2.1/Module/rtmp_main.c:580: warning: passing argument 2 of ‘writel’ makes pointer from integer without a cast
/home/matt/Desktop/rt2400-1.2.1/Module/rtmp_main.c:586: warning: passing argument 2 of ‘writel’ makes pointer from integer without a cast
/home/matt/Desktop/rt2400-1.2.1/Module/rtmp_main.c: In function ‘rt2400_init_module’:
/home/matt/Desktop/rt2400-1.2.1/Module/rtmp_main.c:692: warning: implicit declaration of function ‘pci_module_init’
make[2]: *** [/home/matt/Desktop/rt2400-1.2.1/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/matt/Desktop/rt2400-1.2.1/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-10-386'
**rt2400.ko failed to build!**
make: *** [module] Error 1

For some reason the driver seemed to 'fail to build.' 

> matt@matt:~/Desktop/rt2400-1.2.1/Module$ sudo make install
[sudo] password for matt:
install 'rt2400.ko' to /lib/modules/2.6.22-10-386/kernel/drivers/net/wireless
install -m 644 -o 0 -g 0 -d /lib/modules/2.6.22-10-386/kernel/drivers/net/wireless
install -m 644 -o 0 -g 0 rt2400.ko /lib/modules/2.6.22-10-386/kernel/drivers/net/wireless
install: cannot stat `rt2400.ko': No such file or directory
**make: *** [install] Error 1**

'sudo make install' also failed :( How can I fix this problem and successfully install the driver?

Thanks :)

---

### Post by spamzilla on 2007-08-26
Ok so I used the cvs tarbal and it seemed to work. However, I now have another problem. I typed 'ifconfig ra0' to see if the driver loaded, and I got the following error message

> ra0: error fetching interface information: Device not found

Oddly enough 'modprobe -c|grep rt2400' finds the driver

> matt@matt:~$ modprobe -c|grep rt2400
alias ra0 rt2400
alias ra0 rt2400
alias pci:v00001814d00000101sv*sd*bc*sc*i* rt2400
alias pci:v00001814d00000101sv*sd*bc*sc*i* rt2400pci


lsmod | grep rt2400 finds the driver too

> matt@matt:~$ lsmod | grep rt2400
rt2400                 79808  0 
rt2400pci              15872  0 
rt2x00pci              10624  1 rt2400pci
rt2x00lib              18688  2 rt2400pci,rt2x00pci
mac80211              167816  4 rc80211_simple,rt2400pci,rt2x00pci,rt2x00lib
eeprom_93cx6            2304  1 rt2400pci


Can anyone help me? :)

---

### Post by kevdog on 2007-08-26
Where did you get the source for your rt2400 drivers??  You should be using the serial monkey rt2400 driver.  The following is a post telling you how to compile the serial monkey rt73 driver. I want you to read the post about 3 times before doing anything.  Once you understand the basics, follow the steps, but everywhere rt73 is listed I want you to substitute rt2400.  This should give you what you want:

[http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey)

---

### Post by spamzilla on 2007-08-26
Hey

I followed those steps and installed the rt2400 driver correctly. My connection is still slow, but not as slow as it was before! Do you have any idea how I can tweak my connection to improve it? I am using OpenDNS IP addresses (208.67.222.222 and 208.67.220.220) at the moment and it seems to help a little.

Thanks for the help :)

---

