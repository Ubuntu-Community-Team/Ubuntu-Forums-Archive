---
title: "Help Setting Up Network Card"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by xMemphisx on 2008-09-02
Ok, i recently setup an Ubuntu 8.04 server... but the computer i was setting it up for didn't have a working CD drive, so i set the server up on a different machine and swapped the hard drives. The computer that the hard drive is in currently boots up just fine and loads, and it detects an ethernet device (eth1), but it doesn't get an IP address from my router... and i'm not sure how to get the device configured from the command line.

---

### Post by pytheas22 on 2008-09-02
Please post the output of these commands so that we can figure out what's wrong:
```

lshw -C Network
lspci -nn
ifconfig
ifconfig -a
```

---

### Post by xMemphisx on 2008-09-02
Ok here we go:

lshw -C Network

```

WARNING: you should run this program as super-user.
  *-network DISABLED
    description: Ethernet interface
    product: 82801BA/BAM/CA/CAM Ethernet Controller
    vendor: Intel Corporation
    physical id: 8
    bus info: pci@0000:02:08.0
    logical name: eth1
    version: 01
    serial: **:**:**:**:**:d6
    width: 32 bits
    clock: 33MHz
    capabilities: bus_master cap_list ethernet physical
    configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes

```

lspci -nn
```

00:00.0 Host bridge [0600]: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub [8086:1130] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82815 Chipset Graphics Controller (CGC) [8086:1132] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 02)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corpration 82801BA IDE U100 Controller [8086:244b] (rev 02)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 02)
00:1f.4 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller +1 [8086:2444] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801BA/BAM AC' 97 Audio Controller [8086:2445] (rev 02)
02:08.0 Ethernet controller [0200]: Intel Corproation 82801BA/BAM/CA/CAM Ethernet Controller [8080:2449] (rev 01)

```

ifconfig
```

lo       Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

ifconfig -a
```

eth1     Link encap:Ethernet  HWaddr **:**:**:**:**:d6
         BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo       Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by pytheas22 on 2008-09-02
Thanks for the information.  I think the problem is that your ethernet card is down for some reason.  If you run this, can you connect:
```

sudo ifconfig eth1 up
sudo dhclient eth1
```

If that works, we can write a script to bring the device up automatically from now on (without the script, you would have to run the command above again each time you reboot the computer).

---

### Post by xMemphisx on 2008-09-02
Brilliant! It worked perfectly.

Now all i need to know is how to setup that script and i'll be all set

---

### Post by pytheas22 on 2008-09-02
Glad that worked.  To write a script, first open up a blank file:
```

sudo gedit /etc/init.d/internet-fix.sh
```

Add to the file these lines:
```

#!/bin/bash
#this script brings eth1 up, because for some reason it's not brought up automatically

ifconfig eth1 down
ifconfig eth1 up
```

Then save and close the file.

Then make the script executable:
```

sudo chmod +x /etc/init.d/internet-fix.sh
```

And finally, tell the system to run it at boot:
```

cd /etc/init.d
sudo update-rc.d internet-fix.sh defaults
```

This should work; if after a reboot the computer still isn't online automatically, please let me know.

---

### Post by xMemphisx on 2008-09-02
it's not getting an internet address when it boots up. the device itself goes 'up', and can now be seen as soon as the computer starts with a simple 'ifconfig' command, but it's not attempting to get an address at all

[Edit] 

Fixed it. Thank you so much!!!

---

### Post by pytheas22 on 2008-09-02
hmmm, does it still not work even if you left-click the Network Manager icon and then select "Wired Network?"

Another option is to tell the script itself to fetch an IP address via dhclient--this shouldn't be necessary, but who knows.  The downfall to having the script run dhclient is that it will add a few seconds to your boot time, because the system will pause while an IP address is being fetched.  But if you want to do that, change the script that you created earlier to this:
```

#!/bin/bash
#this script brings eth1 up, because for some reason it's not brought up automatically

ifconfig eth1 down
ifconfig eth1 up
dhclient eth1
```

---

### Post by RainKap on 2008-09-06
Very useful post - thank you! My laptopdecided to shut down both wired & wireless network interfaces when I left it switched on with the external power plug not quite in <grr>, and I was seriously considering doing a re-install to get it working. Fortunately I found your guide, which let me bring up the wired network interface, then I was able to re-install wicd and we are now on the air again. Another good advert for the helpful Ubuntu community!

Ian

---

### Post by pytheas22 on 2008-09-06
> Very useful post - thank you! My laptopdecided to shut down both wired & wireless network interfaces when I left it switched on with the external power plug not quite in <grr>, and I was seriously considering doing a re-install to get it working. Fortunately I found your guide, which let me bring up the wired network interface, then I was able to re-install wicd and we are now on the air again. Another good advert for the helpful Ubuntu community!

Glad it worked :)

---

