---
title: "Qualcomm Atheros Killer E2201 Ethernet not working in ubuntu"
date: 2013-12-22
forum: Networking &amp; Wireless
---

### Post by curtistheiii on 2013-12-22
Hey

I have followed [http://ubuntuforums.org/showthread.php?t=2008332](http://ubuntuforums.org/showthread.php?t=2008332) and have tried the patches on page 1 and page 7. The patch on page 1 give me an error when I do the make command. The patch on page 7 seems to go through successfully, but 
```

sudo modprobe alx
ifconfig

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
Dosent work even after a reboot.

The problem may be because it is E2201 and not E2200

lspci
```

02:00.0 Ethernet controller [0200]: Atheros Communications Inc. Device [1969:e091] (rev 10)

```
modinfo
```

filename:       /lib/modules/3.8.0-29-generic/updates/drivers/net/ethernet/atheros/alx/alx.ko
version:        1.2.3
license:        Dual BSD/GPL
description:    Qualcomm Atheros Gigabit Ethernet Driver
author:         Qualcomm Corporation, <nic-devel@qualcomm.com>
srcversion:     C1A18A7B5B6D43EDA80D3F5
alias:          pci:v00001969d000010A0sv*sd*bc*sc*i*
alias:          pci:v00001969d000010A1sv*sd*bc*sc*i*
alias:          pci:v00001969d00001090sv*sd*bc*sc*i*
alias:          pci:v00001969d0000E091sv*sd*bc*sc*i*
alias:          pci:v00001969d00001091sv*sd*bc*sc*i*
depends:        mdio,compat
vermagic:       3.8.0-29-generic SMP mod_unload modversions 

```
dmesg
```

[    0.964022] alx 0000:02:00.0: alx(94:de:80:6c:e1:95): Qualcomm Atheros Ethernet Network Connection


```

---

### Post by chili555 on 2013-12-22
As you can see, the module alx that's installed now claims your device:> Atheros Communications Inc. Device [[COLOR="#FF0000"]1969:e091[/COLOR]] (rev 10)> filename:       /lib/modules/3.8.0-29-generic/updates/drivers/net/ethernet/atheros/alx/alx.ko
version:        1.2.3
license:        Dual BSD/GPL
description:    Qualcomm Atheros Gigabit Ethernet Driver
author:         Qualcomm Corporation, <nic-devel@qualcomm.com>
srcversion:     C1A18A7B5B6D43EDA80D3F5
alias:          pci:v00001969d000010A0sv*sd*bc*sc*i*
alias:          pci:v00001969d000010A1sv*sd*bc*sc*i*
alias:          pci:v00001969d00001090sv*sd*bc*sc*i*
alias:          pci:v0000[COLOR="#FF0000"]1969[/COLOR]d0000[COLOR="#FF0000"]E091[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v00001969d00001091sv*sd*bc*sc*i*
depends:        mdio,compat
vermagic:       3.8.0-29-generic SMP mod_unload modversionsWe also see that it loads very early in the boot process:> [    [COLOR="#FF0000"]0.964022[/COLOR]][COLOR="#FF0000"] alx[/COLOR] 0000:02:00.0: alx(94:de:80:6c:e1:95): Qualcomm Atheros Ethernet Network ConnectionBut it doesn't seem to go anywhere. I suspect something else is going wrong. 

Please run the command:```
dmesg > curtis.txt
```Find the file curtis.txt in  your user directory and paste it here and give us the link in your reply. [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by curtistheiii on 2013-12-22
I pasted the output here 

[http://paste.ubuntu.com/6619799/](http://paste.ubuntu.com/6619799/)

I dont really know what any of it means :(

---

### Post by chili555 on 2013-12-22
Wow! I see a ton of these:> [    0.000000] *BAD*gran_size: 128K 	chunk_size: 16M 	num_reg: 10  	lose cover RAM: -10M
[    0.000000] *BAD*gran_size: 128K 	chunk_size: 32M 	num_reg: 10  	lose cover RAM: -10M
[    0.000000] *BAD*gran_size: 128K 	chunk_size: 64M 	num_reg: 10  	lose cover RAM: -10M
[    0.000000]  gran_size: 128K 	chunk_size: 128M 	num_reg: 10  	lose cover RAM: 0G
[    0.000000]  gran_size: 128K 	chunk_size: 256M 	num_reg: 10  	lose cover RAM: 0G
[    0.000000]  gran_size: 128K 	chunk_size: 512M 	num_reg: 10  	lose cover RAM: 0G
[    0.000000]  gran_size: 128K 	chunk_size: 1G 	num_reg: 10  	lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 128K 	chunk_size: 2G 	num_reg: 10  	lose cover RAM: -1G
[    0.000000]  gran_size: 256K 	chunk_size: 256K 	num_reg: 10  	lose cover RAM: 1014M
[    0.000000]  gran_size: 256K 	chunk_size: 512K 	num_reg: 10  	lose cover RAM: 1014MFirst, I suggest we get the system to boot without drama before we proceed. I am not experienced in this area; however, I saw this: [http://ubuntuforums.org/showthread.php?p=11677053](http://ubuntuforums.org/showthread.php?p=11677053) (post #4) and this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930007](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930007)> I found that if I turned the amount of memory for the iGPU down to 256, everything works again.Also, I noticed that the dmesg is pretty short, ending at 2.751747; that suggests that the entire boot process is finished in less than 3 seconds. Is that accurate or did you not grab the entire dmesg?

My i3 Intel laptop with 8 Gb of RAM takes north of 15 seconds to boot.

---

### Post by curtistheiii on 2013-12-22
I looked at the posts and I set the memory size to 256 in the bios and nothing has changed. Should I run the patch again? and what does bad grain size mean? I have an i7 with 32 gigs of ram if that makes a difference

---

### Post by chili555 on 2013-12-22
The patch has nothing to add or detract here. You have a working driver *alx* that should work perfectly well if the machine boots perfectly well. I suggest you ask about bad gran here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331) and here: [http://askubuntu.com/](http://askubuntu.com/)

Is the dmesg accurate? Does the machine boot in 3 seconds?

---

### Post by curtistheiii on 2013-12-22
yeah seems to i have reran the dmesg and its always around 2.8

---

### Post by curtistheiii on 2013-12-22
do you think it will make a difference if I run the ubuntu 13.10 insted of the 12.04? I ran a memtest for 2 hours and it came back with 0 errors I have changed the internal graphics to 256 128 and 64 and i havent seen any difference. I guess i can just go buy a lan card or something but i would really like to get this to work. Ill let you know how the 13.10 goes

---

### Post by curtistheiii on 2013-12-22
so updating to Ubuntu 13.10 fixed all the problems apparently.

---

### Post by chili555 on 2013-12-22
> **curtistheiii said:**
> so updating to Ubuntu 13.10 fixed all the problems apparently.Including getting the Bigfoot up and running?

---

### Post by curtistheiii on 2013-12-22
yeah i didnt have to patch or anything drivers must have been updated. Thanks alot for all your help

---

