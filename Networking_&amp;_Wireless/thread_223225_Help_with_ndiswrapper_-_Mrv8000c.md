---
title: "Help with ndiswrapper - Mrv8000c"
date: 2006-07-26
forum: Networking &amp; Wireless
---

### Post by s13_mills on 2006-07-26
I am having trouble getting my wireless card to work in breezy - for the meanwhile I have got a lan cable running through the lounge! :???: 

I have installed ndiswrapper-utils using synaptic package manager, then I managed to get ndiswrapper to install the driver for my card - the Mrv8000c chipset.

I get the following info in the terminal when the following commands are run - I think the problem may be with modprobe ndiswrapper, but I am very new to linux and have no idea how to fix it! Any help would be greatly appreciated!!!

andrew@mills:~$ modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

andrew@mills:~$ ndiswrapper -l
Installed ndis drivers:
mrv8000c        driver present, hardware present

andrew@mills:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:11:BE:4E:65
          inet addr:10.1.1.6  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::211:11ff:febe:4e65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15972 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4656047 (4.4 MiB)  TX bytes:1636968 (1.5 MiB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76725 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76725 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:22008423 (20.9 MiB)  TX bytes:22008423 (20.9 MiB)

andrew@mills:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Please also note I have installed the wifi-radar tool, and it appears to work but when I click connect it just continues trying to connect forever!

Any help with this will be greatly appreciated - I must have read 100 articles on how to do it and none of them are working for me!!!

---

### Post by s13_mills on 2006-07-27
OK - so I am making some progress with this - right now I am uploading this post with my wireless connection, so I have made considerable head-way by using the command:

modprobe -f ndiswrapper

I understand this forces the module to load, meaning that the wlan0 interface appears and can be easily configured from the System>Administration>Networking section.

My problem is now this: ndiswrapper won't load on startup, giving the following error:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Unknown symbol in module, or unknown parameter (see dmesg)

the dmesg output is very long, mostly complaining about symbols etc...

I have read a few articles about this error, and the verdict seems to be that it is because the kernel version does not match ndiswrapper - any way of checking this anyone? Also, I resolved (read: I don't want to do this) to recompile my kernel but I did not in the end as I could not find the source for it on synaptic. I have kernel version 2.6.12-10-386 of ubuntu.

Thank you in advance for any help!

---

### Post by s13_mills on 2006-07-31
I have made further progress with this error and ostensibly fixed it - All I needed to do was edit the /etc/network/interfaces file, changing the ubuntu placed text to:

iface wlan0 inet dhcp
pre-up modprobe -f ndiswrapper
post-down rmmod ndiswrapper
wireless-essid ******
wireless-key **********

Note that this still gives the same error on boot(continues booting normally afterward), as I think that when ubuntu sees wlan0 and does not find a native card, it tries to modprobe ndiswrapper, which fails as before, however, when it encounters the pre-up modprobe -f, it forces it as I previously had to with the terminal.

Anyway, like I said above, I struggled with this, so I hope it helps someone get their wireless card working quicker than I did!

---

