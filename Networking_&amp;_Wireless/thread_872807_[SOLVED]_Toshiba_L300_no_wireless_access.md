---
title: "[SOLVED] Toshiba L300 no wireless access"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by wessie on 2008-07-28
Hi all,

I've spent the better part of 4 days interrogating this website and others in the hopes that I'd manage to get my connection to my router working.

The notebook in question is a Toshiba L300 from which I removed Vista and installed Hardy Heron. After initially having problems with the on board lan I read on a few forum posts that I should disable the 'on board lan' setting in the bios. I eventually got around the bug by upgrading the kernel to version 2.6.24-19. I now have wired access to my router and the net. All this I managed to sort out in about a day thanks to all the support from the ubuntu community.

My attention has since been focused on getting my wireless access to work. I've pretty much given up on it. I've downloaded the ndiswrapper source, applied the 2.6.24 patch, compiled the source and installed the win98 driver as suggested -> no luck. I've tried installing the madwifi drivers -> no luck. 

I'd really appreciate any assistance.

Some of the machine spec (from Toshiba):

WirelessLAN:	RTL8187B_WLAN_Adapter Wireless Network Adapter
LAN:	Realtek RTL8102E Family PCI Express Fast Eternet NIC(NDIS6.0)
CPU:	Intel(R) Celeron(R) CPU 550 @ 2.00GHz
Computer: ACPI (Advanced Configuration and Power Interface) x86 based PC


Some output from the terminal:

uname -a
```
Linux wes-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

ndiswrapper -l
```
net8187b : driver installed
        device (0BDA:8198) present
```


I'd be really happy to provide any further info on request.
I'm really begging for help here.  

Wessie!

---

### Post by wessie on 2008-07-29
any help?.....anyone please

---

### Post by wessie on 2008-08-02
I've done some more searching and found out that the driver created by RealTek for winxp/2k, vista 32bit and vista 64bit support the PID i get when i do a lsusb (0bda:8198). I've tried installing the driver for winxp/2k but unfortunately that still doesn't work.

Is there anyone out there that can help me please!

---

### Post by eram on 2008-08-02
I'm not sure that I totally understand your problem. But could you describe what procedure you did to install and use ndiswrapper?
Maybe I can help as I just did this on my system.

---

### Post by wessie on 2008-08-02
Hi eram,

Thanks for the response but I just (in the last hour or 2) solved my problem. The cause of the problem related to the fact that my chipset is slightly different to the 'common' chipsets. That's why my lsusb output shows ```
0bda:8198
```.

I must give credit to the this post

[http://planeta.rambler.ru/users/crowfish/45208465.html](http://planeta.rambler.ru/users/crowfish/45208465.html)

You'll have to translate it as it's in Russian.

Thanks for the response nonetheless.

---

### Post by eram on 2008-08-02
Great!!!
Glad you got solved it!!!8)

---

### Post by foreilly on 2008-12-23
Sharing the knowledge ... I have wireless working for the rtl8189 on 8.10 Intrepid Ibex, and have posted this note over a wireless link.

I am running on a Toshiba Satellite L300D-13S, starting with a plain install of Ubuntu 8.10 Intrepid Ibex desktop edition, and the solution I found best for my situation was to hack the kernel's builtin rtl8187b module. As it stands, the module does not work for this laptop. I spent lots of time trying to get it working with Ndiswrapper, to no avail. Hacking the kernel and rebuilding did the trick immediately (well, after a reboot, of course). Works for WPA connections, haven't tried WEP yet.

I followed the instructions on this page: [http://sourceforge.net/forum/forum.php?thread_id=2389615&forum_id=652149]("http://sourceforge.net/forum/forum.php?thread_id=2389615&forum_id=652149") by Philip Potter. Basically, after downloading the kernel source for 2.6.27, modify drivers/net/wireless/rtl8187_dev.c:

After

```
/* Realtek */
{USB_DEVICE(0x0bda, 0x8187), .driver_info = DEVICE_RTL8187},
{USB_DEVICE(0x0bda, 0x8189), .driver_info = DEVICE_RTL8187B},
{USB_DEVICE(0x0bda, 0x8197), .driver_info = DEVICE_RTL8187B},

```

insert the line


```
{USB_DEVICE(0x0bda, 0x8198), .driver_info = DEVICE_RTL8187B},
```

Then rebuild and install the kernel. (Standard kernel rebuild/install instructions for Ubuntu found here: [https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile"))

Hope this helps anyone trying to get wireless working on the Toshiba L300D-13S, it's another option to try.

---

### Post by foreilly on 2008-12-26
Update: looks like the above patch is in the new 2.6.28 kernel. Haven't tested if it works yet, but that one liner was all I needed to get my wireless working out-of-the-box.

---

