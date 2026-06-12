---
title: "Download Bandwidth 50% of that with windows"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by w4nng on 2008-03-25
Hello 

Got a speed problem that appears to not be IPv6 related

First the good news
ISP link is 10Meg  -  On 1 computer running ubuntu 7.10, I get 10Meg from Speakeasy test.  When I reboot to Win it drops to 6 Meg [ cheers for Ubuntu]

On other older computer I get 5.5Meg via Window boot and 2.8Meg via Xubuntu boot.

Based on web search finding tried disable IPv6 in both 'alias' and in Firefox but it had zero impact.

Any additional advice appreciated.

---

### Post by dmizer on 2008-03-26
disabling ipv6 via alias has been outdated since breezy.  check your ifconfig, and if you see ipv6 addressing that looks something like this:
```
inet6 addr: 2001:5c0:92cf:0:20e:cff:feb9:4ded/64 Scope:Global
inet6 addr: fe80::20e:cff:feb9:4ded/64 Scope:Link
```

if you're still seeing a inet6 address, take a look at this tutorial: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?)

---

### Post by w4nng on 2008-03-26
Thanks Dmizer

Unfortunately this is just an easier way to disable ipv6.  The problem persists with it off.  ipv6 is also on my other computer that does not have problem.   This tends to confirm that my router and ISP can handle it.

Any other thoughts?

---

### Post by stream303 on 2008-03-27
Does changing your mtu do anything?  The default when I run ifconfig shows that I'm using 1500, but some have reported using something lower, like 1492 or so.

Although with two machines connected to the same router, I don't see why this would make any difference.  Does ifconfig on each machine show any different mtu's?  Is the mtu in your router running at default like 1500 or something different?

To temporarily change the mtu, I do something like this:
```

sudo ifconfig eth0 mtu 1492
```

and of course if that doesn't work well, I go back
```

sudo ifconfig eth0 mtu 1500
```

Just something to try...

---

### Post by w4nng on 2008-03-27
Hello Stream303

Thoughtful suggestion.  Unfortunately it didn't work.  Also tried MTU 1000 which made it even slower [but did convince me it was taking]

Your suggestion also triggered memory [from ~ 8 yrs ago] that on WIN98SE config I had same problem until forced link spd to 10 Full Dplx.   

Did same on this xbuntu [& confirmed that it took].  Improved situation from 2800 to 3200 kb  but well below WIN98 boot spd of 5800kb
Did reboot router to make sure.  

BTW: How does one make these eth0 changes permanent -- ie part of boot

---

### Post by dmizer on 2008-03-27
what chipset is your adapter using?  post the output of:
```
lspci
```

---

### Post by w4nng on 2008-03-27
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
01:05.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 10)
01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:09.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)

---

### Post by dmizer on 2008-03-27
according to what i've been reading about that chipset, you may get better results by disabling acpi in the kernel.  so add:
acpi=off

or
acpi=off nolacpi

to the kernel (/boot/grub/menu.lst)

---

### Post by w4nng on 2008-03-28
Hello

Adding either acpi=off or acpi=off nolacpi to the menu.lst had no impact

I also tried updating to current OS [ Xubuntu 8.04]

Interesting problem.

---

### Post by w4nng on 2008-04-08
I noticed that my max download speed incresed after one of the recent batch of 'updates' was installed.   It's gone from ~3000 to 5500kbs   Now it's the same as when I boot into windows.  

Haven't had the time to go throught the logs but the problem is fixed.   

Thanks for the help

---

### Post by w4nng on 2008-04-30
For the record,

I just upgraded to Unbuntu 8.04.

The situation has reversed.  Booting to windows still gives the base-line orginal thru-put, but when booted to Linux it's ~ 1.8X faster then in windows.   That's an amazing improvement over the original 50% of Win98SE

---

