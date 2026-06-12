---
title: "How can I activate my wireless network card?"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by elektronaut on 2006-11-07
Hi everyone,

I just got a new laptop, an Acer Aspire 5550AWXMI (apparently some special configuration only to be sold by a chain of computer stores here in Germany, similar to Aspire 3670). Certainly, the first thing I did was to completely wipe Windows from the disk :D  and install Edgy Eft. So far, everything except wifi seems to work fine. It's got an Intel 3945 wireless card built in. The module is loaded, but I don't get the wireless interface. I guess it's because the card has to be activated in the hardware. There is a switch for enabling the wifi, but it doesn't work. Unfortunately I didn't find any option in the BIOS to enable it permanently, as suggested in other threads. So how can I enable the card now?

```
$ lspci|grep 3945
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
$ lsmod|grep ipw
ipw3945               124576  0 
ieee80211              35272  1 ipw3945
$ ps -e|grep ipw
 5190 ?        00:00:00 ipw3945/0
 5191 ?        00:00:00 ipw3945/0
$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
sit0      no wireless extensions.
```

---

### Post by elektronaut on 2006-11-08
O.K., I got a bit further. `tail -f /var/log/messages` shows me that the wlan switch is recognized:
```
Nov  8 13:29:48 acer-5550 kernel: [17179874.936000] atkbd.c: Unknown key pressed (translated set 2, code 0xd5 on isa0060/serio0).
Nov  8 13:29:48 acer-5550 kernel: [17179874.936000] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
Nov  8 13:29:49 acer-5550 kernel: [17179875.344000] atkbd.c: Unknown key released (translated set 2, code 0xd5 on isa0060/serio0).
Nov  8 13:29:49 acer-5550 kernel: [17179875.344000] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
```
So the wireless card is recognized, the module is loaded, pushing the switch is recognized... how is it possible to link the switch to the wireless card now?

---

### Post by elektronaut on 2006-11-09
Does this help in diagnosing the problem?

```
$ lshw
...
           *-network
                description: Network controller
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@03:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ipw3945
                resources: iomemory:d8000000-d8000fff irq:169
```

---

### Post by andreas64 on 2006-11-09
Hi elektronaut,

Please install the restricted-modules for your kernel. After that, your wireless NIC should be detected and will work.

Andreas

---

### Post by elektronaut on 2006-11-09
:-D YEEESSS!:-D  

Finally the problem is solved. You were right, Andreas, I just figured this out before I saw your post. I already copied **/sbin/ipw3945d-2.6.17-10-generic** from the restricted modules, as suggested [here]("http://ubuntuforums.org/showpost.php?p=1715171&postcount=51"), but this
```
$ ps -e|grep 3945
 2957 ?        00:00:00 ipw3945/0
 2958 ?        00:00:00 ipw3945/0
```
showed me that **3945d** was not running. After ```
$ sudo /sbin/ipw3945d-2.6.17-10-generic
``` eth1 is finally there! I didn't think that I would have to call it, I thought it would somehow be automatically loaded after a reboot. Should I put it in System > Configuration > Sessions > Start Programs? Or is there a way to attach it to the keycode that I found in the system messages when I pushed the wlan switch? That would be sweet... If there is a possibility to use the wlan switch, would this be the best way? Or should the switch be attached to a script that calls `rmmod/insmod ipw 3945` and other stuff?:-k

---

### Post by martinquested on 2006-11-09
> Hi elektronaut,

Please install the restricted-modules for your kernel. After that, your wireless NIC should be detected and will work.

Andreas

I have a Compaq Presario V6030US (in the V6000 series) which may be suffering the same problem.  I'm a bit of a newbie and would like to follow Andreas' advice - I just don't know what that means to install the restricted-modules.  Can you clarify how I do that?  Thanks!

Martin

---

### Post by anguste on 2006-11-10
> **martinquested said:**
> I have a Compaq Presario V6030US (in the V6000 series) which may be suffering the same problem.  I'm a bit of a newbie and would like to follow Andreas' advice - I just don't know what that means to install the restricted-modules.  Can you clarify how I do that?  Thanks!

Martin

Hi,

perhaps an easy way to do this is that, open System - Administration - Synaptic Package Manager

make a "Search/Find" and type "restricted modules", you will get some results.

---

### Post by elektronaut on 2006-12-03
For fellow travellers who pass by here and just want to use the ipw3945 daemon and deinstall the rest of the restricted-modules package: Just copy the daemon from /sbin/ipw3945d-2.6.17-10-generic to a temporary location, deinstall, and put it back there. Then add the following line to /etc/rc.local: ```
/sbin/ipw3945d-2.6.17-10-generic

```That's it. If you have a switch on your laptop which you want to use for activating your wireless card, and it's not connected hardware-wise, [look here](http://ubuntuforums.org/showthread.php?t=303897).

---

