---
title: "Help with Netgear WG111T Wireless Networking"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by c_forq on 2007-03-17
Hello.  I was told that the WG111T had native Linux drivers (being an Atheros chip).  One thing I know, is it is not “just working”.  Can someone point me to a how-to to get this card up and running?  My goal for this is to provide wireless access to other devices, not to connect to a routher (a have a wired connection to this PC, and I would like this PC to act as a router).  Is that possible with this card?  If not what USB Wi-Fi device should I pick up?  Thanks in advance.

---

### Post by Kobalt on 2007-03-17
I think it should be doable with your card. 
Can you please post the output of the following command line : ```
iwconfig
```

---

### Post by c_forq on 2007-03-17
lo        no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
eth0      no wireless extensions.

sit0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

forquerc@forq-desktop:~$ 


But I beleive wlan0 is my PCI card, which I never got working under linux and have given up on.

---

### Post by Kobalt on 2007-03-17
It seems to be ready to be configured. 
You should have a network-monitor icon in the right top corner of your screen : right-click on it and select Configure. Then, enter the label of your wireless interface in the interface bar : type in wether 'wlan0' of 'wmaster0'. If you see a signal jauge then you'll be ready for next step, otherwise post what you experience here.
After that you'll need to enter your essid and wep key : press on Configure to enter everything there (don't forget to specify wheter you're in dhcp or static IP and fill in your IP gateway, etc. in needed). 

Now you should be able to surf wirelessly :)

---

### Post by c_forq on 2007-03-17
As I stated I don't think that wlan0 is my USB wireless, it is my PCI card.  Second of all  I don't want to surf wirelessly, I want other devices to be able to connect to this PC in order to surf wirelessly.

---

### Post by c_forq on 2007-03-17
Also typing in a router and WEP key of one I know did not work (trying wlan0), as I stated before I've given up on getting the PCI card working in Linux.

---

### Post by c_forq on 2007-03-17
Okay, I've tried using ndiswrapper, and this is what comes up without it plugged in:
Installed drivers:
forquerc@forq-desktop:~$ ndiswrapper -l
athfmwdl                driver installed 
netwg11t                driver installed 
rt61            driver installed, hardware present 

Again, the rt61 is my PCI wireless card.

forquerc@forq-desktop:~$ sudo modprobe ndiswrapper
forquerc@forq-desktop:~$ 

When I plug in the USB stick, I get:

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000] Oops: 0000 [#1]

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000] SMP 

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000] CPU:    0

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000] EIP is at kmem_cache_free+0x22/0x50

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000] eax: 00000000   ebx: 35357261   ecx: f5f678c0   edx: f59c7424

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000] esi: 00000292   edi: f59c7424   ebp: 00000000   esp: df93bcc4

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000] Process khubd (pid: 1728, threadinfo=df93a000 task=df86c560)

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000] Stack: f59c742c f70b9880 00000003 f916f789 f916fa4f f59c742c 00000000 00000000 

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000]        02022f98 00000000 00000000 00000000 f70b9880 fa88101c fa8810d0 f90a3c22 

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000]        f70b9964 0000001b fa88101c fa88101c f916ebc6 fa88101c f70b9880 00000000 

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000] Call Trace:

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000]  <f916f789> IoFreeMdl+0x9/0x10 [ndiswrapper]  <f916fa4f> IofCompleteRequest+0x15f/0x1a0 [ndiswrapper]

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000]  <f916ebc6> IofCallDriver+0x36/0x70 [ndiswrapper]  <f917452b> IoSendIrpTopDev+0xbb/0x120 [ndiswrapper]

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000]  <f9174840> pnp_start_device+0x50/0xb0 [ndiswrapper]  <f9174a5a> wrap_pnp_start_device+0x1ba/0x290 [ndiswrapper]

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000]  <f9174d5d> wrap_pnp_start_usb_device+0x6d/0xb0 [ndiswrapper]  <f88a96e6> usb_match_dynamic_id+0x16/0x80 [usbcore]

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000]  <f88a9681> usb_match_id+0x31/0x50 [usbcore]  <f88a9b1a> usb_probe_interface+0x6a/0xa0 [usbcore]

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000]  <c0246134> driver_probe_device+0x44/0xc0  <c02d86e8> klist_next+0x38/0x60

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000]  <c02459b4> bus_for_each_drv+0x44/0x70  <c0246228> device_attach+0x68/0x70

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000]  <c02461b0> __device_attach+0x0/0x10  <c0245888> bus_add_device+0x28/0x110

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000]  <c0244a47> device_add+0xf7/0x150  <f88a88ae> usb_set_configuration+0x31e/0x4d0 [usbcore]

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000]  <f88a37ca> usb_new_device+0x20a/0x2d0 [usbcore]  <f88a4eab> hub_thread+0x79b/0xc80 [usbcore]

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000]  <c0136180> autoremove_wake_function+0x0/0x50  <f88a4710> hub_thread+0x0/0xc80 [usbcore]

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000]  <c0135f8b> kthread+0xab/0xe0  <c0135ee0> kthread+0x0/0xe0

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000]  <c0101005> kernel_thread_helper+0x5/0x10 

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000] Code: 45 ff ff ff 90 8d 74 26 00 83 ec 0c 89 c1 89 7c 24 08 89 d7 89 1c 24 89 74 24 04 9c 5e fa b8 00 e0 ff ff 21 e0 8b 40 10 8b 1c 81 <8b> 03 3b 43 04 73 1a 89 7c 83 14 83 c0 01 89 03 56 9d 8b 1c 24 

Message from syslogd@forq-desktop at Sat Mar 17 17:39:00 2007 ...
forq-desktop kernel: [17179817.996000] EIP: [kmem_cache_free+34/80] kmem_cache_free+0x22/0x50 SS:ESP 0068:df93bcc4

---

### Post by c_forq on 2007-03-17
After restarting with the device init now seems to be coming up, listed as wlan1.

---

### Post by c_forq on 2007-03-17
When trying to connect via the network monitor it seems to take, but the meter just shows a little bit of yellow and there is an organge triangle in the bottom corner.  This still doesn't help in using this computer as a bridge though.

---

