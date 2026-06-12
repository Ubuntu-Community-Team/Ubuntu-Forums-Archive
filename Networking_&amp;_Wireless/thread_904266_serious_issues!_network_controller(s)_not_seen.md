---
title: "serious issues! network controller(s) not seen"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by davbren on 2008-08-29
I've just bought a brand new laptop, I was aware that it had new technology in it but i wasn't aware that the network controllers were new too! Neither one of my network cards work.

lspci produces:

```

02:00.0 Network controller: Intel Corporation Unknown device 4232
06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev13)
```

As my NIC cards dont work I have no net connection on the laptop, not particularly convenient as I think the new kernel has support for these...

---

### Post by overdrank on 2008-08-29
Moved to Networking & Wireless  :)

---

### Post by davbren on 2008-08-31
> 
I have written to Marvell, but they haven't answered to me yet. Later I have downloaded Yukon Linux Driver Install Package (Linux Kernel 2.4.20 & Higher, 1/24/07, 10.0.4.3 (install_v10.0.4.3.tar.bz2)) and tried to install it, but there was error:

72: Syntax error: "(" unexpected

Maybe I tried wrong driver to install? Or everything what I can do it only wait a new driver from Marvell?

I saw this in a different post from '07 it seems that this is an ongoing problem, because I'm getting this exact error... I have also written to MArvell in hope of gettinga  response and a resolution to the problem.

In the mean time does anyone know how I can get my ethernet to work?? 

Please, Please, Please, Please, Please, help! :(

---

### Post by Len_C on 2008-09-05
I compiled the Marvell Yukon sk98lin driver for kernel versions
2.6.24-16-generic und 2.6.24-19-generic. I don't have a Marvell Technology Group Ltd. 88E8055 PCI-E Card. So I don' know if the driver works.

Download for  kernel version 2.6.24-16-generic: [http://media.ubuntuusers.de/forum/attachments/1572741/sk98lin.tar.bz2](http://media.ubuntuusers.de/forum/attachments/1572741/sk98lin.tar.bz2)


Download for  kernel version 2.6.24-19-generic: [http://media.ubuntuusers.de/forum/attachments/1574640/sk98lin.tar.bz2](http://media.ubuntuusers.de/forum/attachments/1574640/sk98lin.tar.bz2)

Save the driver package (sk98lin.tar.bz2) for your kernel in directory /opt
Then type:

```
cd /opt
sudo -s 
tar xjf sk98lin.tar.bz2 
cp -R sk98lin /lib/modules/$(uname -r)/kernel/drivers/net
depmod -a
echo 'blacklist sky2' | tee -a /etc/modprobe.d/blacklist
echo sk98lin | tee -a /etc/modules
```

Then reboot.

Here are my instructions for compiling the driver: [http://forum.ubuntuusers.de/post/1572741/](http://forum.ubuntuusers.de/post/1572741/) (unter point 2)
english translation: [http://translate.google.at/translate?u=http%3A%2F%2Fforum.ubuntuusers.de%2Fpost%2F1572741%2F&sl=de&tl=en&hl=de&ie=UTF-8](http://translate.google.at/translate?u=http%3A%2F%2Fforum.ubuntuusers.de%2Fpost%2F1572741%2F&sl=de&tl=en&hl=de&ie=UTF-8)

---

### Post by davbren on 2008-09-05
Hi cheers for that, I'm sure the installation was successful. There seems to be a bigger problem here. My eth0 doesn't seem to exist... on typing ifconfig -a I only get the loopback entry. Nothing about eth0. I'm not using a virtual machine. I also looked in modprobe.conf and its empty.

Cheers.

---

### Post by Len_C on 2008-09-05
What does

> uname -r
lsmod | grep sk98lin
dmesg | grep sk98lin
lsmod | grep sky2
cat /etc/udev/rules.d/70-persistent-net.rules


produce?

---

### Post by Crafty Kisses on 2008-09-05
Hmmm, post results of > lsusb

---

### Post by davbren on 2008-09-05
> dave@dave-samsung:~$ uname -r
2.6.24-19-generic


dave@dave-samsung:~$ lsmod | grep sk98lin
sk98lin               190872  0 


dave@dave-samsung:~$ dmesg | grep sk98lin
[   29.917365] sk98lin: Network Device Driver v10.70.1.3


dave@dave-samsung:~$ lsmod | grep sky2
sky2                   47492  0 


dave@dave-samsung:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.


This is the output...

---

### Post by jab69 on 2008-09-05
I've the same problem with the 88E8055 PCI-E Gigabit Ethernet Controller in a Samsung R710 notebook.

> **Len_C said:**
> What does



produce?

uname -r              
2.6.24-16-generic

lsmod | grep sk98lin  
sk98lin   190872  0

dmesg | grep sk98lin  
[  45.809810] sk98lin:  Network Device Driver v10.70.1.3

lsmod | grep sky2     
*Nothing, direct a prompt*

cat /etc/udev/rules.d/70-persistent-net.rules 
(same as Davbren)

---

### Post by Len_C on 2008-09-05
1.
Type: 

> sudo gedit /etc/udev/rules.d/70-persistent-net.rules

and add the following entry to the file

> # PCI device 0x11AB:0x4320 (sk98lin)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0a:fg:45:d6:ac", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


(note: instead 00:0a:fg:45:d6:ac you must fill in the mac address of YOUR lan-device >  [http://www-dcn.fnal.gov/DCG-Docs/mac/index.html](http://www-dcn.fnal.gov/DCG-Docs/mac/index.html) )

2.
Although the sky2 driver was blacklisted by

> echo 'blacklist sky2' | tee -a /etc/modprobe.d/blacklist 

this driver is still loaded.

Type

> sudo gedit /etc/rc.local

Change this file as follows:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
rmmod sky2
rmmod sk98lin
modprobe sk98lin
/etc/init.d/networking restart
exit 0

3.
Reboot.

---

### Post by Len_C on 2008-09-05
1.
Type: 

> sudo gedit /etc/udev/rules.d/70-persistent-net.rules

and add the following entry to the file

[SIZE="2"]> # PCI device 0x11AB:0x4320 (sk98lin)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0a:fg:45:d6:ac", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"[/SIZE]


(note: instead 00:0a:fg:45:d6:ac you must fill in the mac address of YOUR lan-device >  [http://www-dcn.fnal.gov/DCG-Docs/mac/index.html](http://www-dcn.fnal.gov/DCG-Docs/mac/index.html) )

2.
Although the sky2 driver was blacklisted by

> echo 'blacklist sky2' | tee -a /etc/modprobe.d/blacklist 

this driver is still loaded.

Type

> sudo gedit /etc/rc.local

Change this file as follows:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
rmmod sky2
rmmod sk98lin
modprobe sk98lin
/etc/init.d/networking restart
exit 0

3.
Reboot.

---

### Post by davbren on 2008-09-05
Hmm I'm still getting nothing... 

When I type ifconfig -a I'm still only seeing the loopback

---

### Post by jab69 on 2008-09-05
I can't find my MAC-adress!
Output ifconfig -a is only lo and no eth0 on the laptop.

---

### Post by davbren on 2008-09-05
do you not dual boot? I booted into windows and opened command prompt and typed ipconfig /all

---

### Post by Len_C on 2008-09-05
jab69: if you have also windows installed have a look at

[http://www-dcn.fnal.gov/DCG-Docs/mac/xp.html](http://www-dcn.fnal.gov/DCG-Docs/mac/xp.html) (same procedure in windows xp).

If you have filled in your mac address in /etc/udev/rules.d/70-persistent-net.rules (see obove posting) and ifconfig
shows after rebooting still no lan device (eth0) I guess, the driver doesn't work.

---

### Post by davbren on 2008-09-05
hmmm, marvell seem to think that the driver does indeed work. I did everything you've asked me to and still no luck. Thank you very much for your time. If you think of anything else, dont hesitate to say..

Thank you.
David.

---

### Post by jab69 on 2008-09-05
:oops:
Found it and tried it.
Didn't work here.

---

### Post by davbren on 2008-09-05
This is just really lame!

---

### Post by Kevbert on 2008-09-05
I believe you have a dual band Intel 5100/5300 adapter which supports 802.11a/b/g/Draft N wireless. The best link I could find was [here]("http://ubuntuforums.org/showthread.php?t=879134"). If that fails you could try searching on the Intel.com website for linux 5100/5300 drivers (you may need to use ndiswrapper).

---

### Post by zugol on 2008-09-19
Hi, I'm plannig to buy this computer, did you finally make your network controller works properly ?

Thanks.

---

### Post by davbren on 2008-09-19
Hi to follow-up. I have the networking working using Intrepid Alpha 5. Thats both the ethernet and the wifi :) 

Also the card reader works. and headhone socket, external monitor port. I haven't tried the expresscard slot or the HDMI port. The webcam doesn't work as yet. I'm not sure how to get that to work. Its a Symtek. Also the brightness controller doesn't work. I think thats about it....

I hope thats some help.

---

### Post by zugol on 2008-10-05
No way to install Intrepid beta... Waiting for stable release...

---

