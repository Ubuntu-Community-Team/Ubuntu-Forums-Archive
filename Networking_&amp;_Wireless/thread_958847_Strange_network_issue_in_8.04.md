---
title: "Strange network issue in 8.04"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by K_T on 2008-10-25
Hi!

Here's what happened. After a kernel update to version 2.6.24-21 my Internet connection stopped working. Right-clicking the network applet and choosing “Connection Information” reveals that the IP-address, Broadcast address etc. are set to 0.0.0.0. Network Tools shows the devices; loopback, eth0 and sometimes eth0:avahi (what is that?). Trying to configure the eth0 or the eth0:avahi device renders a “the interface does not exist”-message. Going back to kernel 2.6.24-19 did not make any difference. I figured it was some kind of driver issue and gave up.

After a week or two using Win XP (this is a dual-boot machine) I decided to try to sort this problem out. I booted up 2.6.24-19 and suddenly everything worked fine. I concluded that it must have been an issue with the new kernel after all, and installed the StartUp-Manager to change the default boot option. Some, as far as I know, unrelated updates were also installed through the Update Manager. I  don't know if I messed up or if there's some bug in the StartUp-Manager, but instead of setting 2.6.24-19 as default and removing all the other kernel options from grub as I wanted it to, 2.6.24-21 was set as default. The computer booted up 2.6.24-21 and all of a sudden Internet was working with this kernel too.

I concluded that some update must have solved the problem. So I carried on as usual, minding my own business, but after a reboot (there were a few of them in between) Internet stopped working again. Same issue.

What is going on here? Please help!

P.S.
I'm not using a router, the network is set to roaming mode and the network adapter is the ga-p35-ds3 onboard one.

Best regards
K_T

---

### Post by pytheas22 on 2008-10-25
Maybe it's just flaky hardware, if you're getting inconsistent behavior like this for no reason.  There may be a way to work around it, however.  The next time you boot up and the connection doesn't work, please run these commands and post the output:
```

lspci -nn
lshw -C Network
dmesg | grep -e eth
ifconfig
```

Also, the next time that you boot and it works, try rebooting again several times, without making any software changes in between.  Is the behavior still inconsistent then, when you're certain that nothing is changing on Ubuntu's end?

---

### Post by K_T on 2008-10-26
Thank you for your reply. Since the network works under Win XP I assume it's not a hardware issue. But I could of course be wrong. Here are the outputs (I blanked out the hardware address, IP-addresses and some, AFAIK, unnecessary info).

```

K_T@asd:~$ lspci -nn 
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01) 

```

```

K_T@asd:~$ lshw -C Network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: eth0 
       version: 01 
       serial: 00:00:00:00:00:00 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes 

```

```

K_T@asd:~$ dmesg | grep -e eth 
[   27.338675] eth0: RTL8168b/8111b at 0xf8844000, 00:00:00:00:00:00, XID 38000000 IRQ 219 
[   30.934600] Driver 'sd' needs updating - please use bus_type methods 
[   30.935858]  sda:<4>Driver 'sr' needs updating - please use bus_type methods 
[   47.766211] r8169: eth0: link up 
[   47.766221] r8169: eth0: link up 
[  115.027505] eth0: no IPv6 routers present 

```

```

K_T@asd:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxxx/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1 
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:210 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:342 (342.0 B)  TX bytes:17667 (17.2 KB) 
          Interrupt:219 Base address:0x4000 

eth0:avahi Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:169.xxx.x.xx  Bcast:169.xxx.xxx.xxx  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1 
          Interrupt:219 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2303 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2303 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:117553 (114.7 KB)  TX bytes:117553 (114.7 KB) 

```

---

### Post by pytheas22 on 2008-10-26
Have a look at [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798"), [this bug report]("https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/181081") and [this thread]("http://ubuntuforums.org/showthread.php?t=773701").  They sound like they may be related to your issue (they deal with the same exact ethernet chipset, PCI ID 10ec:8168 ).  The bug reports say that the issue is fixed in Ubuntu 8.10 and that it should be fixed in Ubuntu 8.04, so I'm not sure why it has suddenly started occurring on your Hardy system if it didn't happen before.  You may want to enable the hardy-backports repository and install updates based on it.

You can also try a couple of other things that people say helped.  First, power down your computer and unplug the power cable for a minute (and remove the battery if it's a laptop), then boot back up.  This may help because it forces the ethernet card to reset itself.

It might also help to reinsert the ethernet driver.  Does it make a difference if you type:
```

sudo modprobe -r r8169
sudo modprobe r8169
```

---

### Post by K_T on 2008-10-26
Shutting down and unplugging before restart worked like a charm. This is consistent with the previous behavior, the computer actually was unplugged for a few days before I, again, attempted to fix the problem.

So apparently the kernel update, or some other update done simultaneously, broke the Ethernet driver? I don't think I'm going to attempt to fix it permanently since Intrepid is due in 4 days.

Thanks for your help!

---

### Post by pytheas22 on 2008-10-26
If powering down and up again solved the problem, then it was probably an issue where Windows puts the card to sleep and the Linux driver can't wake it up.  This is a known problem with some Realtek cards.  You can set it in Windows not to power the card down anymore in order to avoid this issue in the future; see [this post]("http://ubuntuforums.org/showpost.php?p=3443923") for how to do that.

On the other hand, the Intrepid driver might be able to wake the card up from its Windows sleep, or this may have been a weird quirk that's unlikely to occur again, so it may not be necessary to change the settings in Windows.

---

### Post by K_T on 2008-10-29
> **pytheas22 said:**
> If powering down and up again solved the problem, then it was probably an issue where Windows puts the card to sleep and the Linux driver can't wake it up.  This is a known problem with some Realtek cards.  You can set it in Windows not to power the card down anymore in order to avoid this issue in the future; see [this post]("http://ubuntuforums.org/showpost.php?p=3443923") for how to do that.

On the other hand, the Intrepid driver might be able to wake the card up from its Windows sleep, or this may have been a weird quirk that's unlikely to occur again, so it may not be necessary to change the settings in Windows.
Well, that makes even more sense. It's funny how even when it's Ubuntu that is not working, it's Windows fault. ;) Thanks again.

---

