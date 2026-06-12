---
title: "No network on Thinkpad 600E + 3COM PCMCIA"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by vitalis on 2007-01-14
Hello,
I've installed Ubuntu 6.10 on IBM Thinkpad 600E with PCMCIA ethernet card 3C589-TP. Can't get network working with ADSL modem/router. I've tested almost all of advices, which I found on Ubuntu forums. Definitely card and modem work - it was Ok with previously installed win2000.

**ifconfig:**
```

eth0      Link encap:Ethernet  HWaddr 00:60:08:22:44:66  
          inet addr:192.168.255.5  Bcast:192.168.255.255  Mask:255.255.255.0
          inet6 addr: fe80::260:8ff:fe22:4466/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:468 (468.0 b)
          Interrupt:3 Base address:0x300 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14784 (14.4 KiB)  TX bytes:14784 (14.4 KiB)

```

**/etc/network/interfaces**
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static

address 192.168.255.5
netmask 255.255.255.0
gateway 192.168.255.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

DHCP does not work - I've tested IP static with modem's settings. 

I can't get ping to my gateway - nowhere.

So, what could be a problem here?

Thanks in advance!
-Vitali

---

### Post by vitalis on 2007-01-14
How to check that HW is detected correctly - maybe some package?

---

### Post by grumpymole on 2007-01-15
Make sure that you have ```
acpi=off pnpbios=off
``` added to your kernel boot parameters.  I have had similar symptoms before.

Regards

Warren
[http://grumpymole.blogspot.com](http://grumpymole.blogspot.com)

---

### Post by vitalis on 2007-01-16
> **grumpymole said:**
> ...added to your kernel boot parameters.
Where I can add it? During GRUB loading in it menu?

---

### Post by grumpymole on 2007-01-16
vitalis,

To test it, you can add it by interrupting grub countdown with Esc.  Select the kernel you normally boot with (the first in the list, I think).  'e' to edit.  Scroll down to "kernel..." line.  'e' to edit this line and you are taken to the end of the line.  Add the parameters there.  ESC to go back.  'b' to boot with the parameters you have just added.  If it helps, then you can make the changes permanent by editing /boot/grub/menu.lst.  Below is a copy of the appropriate section in my menu.lst.  The vga=791 is to help with a problem with the usplash screen in Feisty.

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash acpi=off pnpbios=off vga=791
```

(X)ubuntu on my TP 600E often comes up on my blog.

Regards

Warren
[http://grumpymole.blogspot.com](http://grumpymole.blogspot.com)

---

### Post by vitalis on 2007-01-17
Warren,

I've tested acpi=off and pnpbios=off options during the GRUB starting - do not help.
Look like some deep problem with particular PCMCIA card

I'm going to test Debian Etch distributive with same HW to test a network.

Thank you for the help!

Br
-Vitali

---

