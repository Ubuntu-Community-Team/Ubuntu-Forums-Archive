---
title: "WPA does not work - but I'm connected??"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by kkaras on 2009-08-08
Hi Guys, I could really use some help here! I simply can not get my WPA to work.

I have an SMC "SMCWUSBT-G2" usb wireless modem and the matching router. The router has the newest firmware. As SMC does not supply a linux driver, I use ndiswrapper.

With WPA enabled, I can not get 'data through' to the router. If I disable the WPA encryption, I have no problems. It works on Windows with WPA.

Whith WPA enabled, the NetworkManager does state that I'm connected, but I am not able to get any 'data through': In Wireshark I can see that no ARP or DHCP requests is replied by the router. The only PDUs I get from the router is EAPOL KEY (which is part of the WPA protocol). From the wpa_supplicant log, I get the following, which I interpret as encryption is working:


CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:13:f7:53:ef:00 (SSID='stace' freq=2472 MHz)
Associated with 00:13:f7:53:ef:00
WPA: Key negotiation completed with 00:13:f7:53:ef:00 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 00:13:f7:53:ef:00 completed (auth) [id=0 id_str=]
WPA: Key negotiation completed with 00:13:f7:53:ef:00 [PTK=CCMP GTK=CCMP]
WPA: Key negotiation completed with 00:13:f7:53:ef:00 [PTK=CCMP GTK=CCMP]
WPA: Key negotiation completed with 00:13:f7:53:ef:00 [PTK=CCMP GTK=CCMP]
Associated with 00:13:f7:53:ef:00
CTRL-EVENT-SCAN-RESULTS 
WPA: Key negotiation completed with 00:13:f7:53:ef:00 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 00:13:f7:53:ef:00 completed (reauth) [id=0 id_str=]


The above continues until I do something to abrupt the connection. From the /var/log/messages I get the following when I plug the USB into my laptop:


Aug  8 09:58:34 ubuntu kernel: [ 2121.017447] device wlan0 left promiscuous mode
Aug  8 09:58:34 ubuntu kernel: [ 2121.048742] ndiswrapper: device wlan0 removed
Aug  8 09:58:35 ubuntu kernel: [ 2122.448043] usb 1-5: new high speed USB device using ehci_hcd and address 5
Aug  8 09:58:36 ubuntu kernel: [ 2122.613469] usb 1-5: configuration #1 chosen from 1 choice
Aug  8 09:58:36 ubuntu kernel: [ 2122.756053] usb 1-5: reset high speed USB device using ehci_hcd and address 5
Aug  8 09:58:36 ubuntu kernel: [ 2122.904963] ndiswrapper: driver smcusbt (SMC,04/24/2006,1.5.0.102) loaded
Aug  8 09:58:36 ubuntu kernel: [ 2122.915530] ndiswrapper (ZwQueryValueKey:2330): not fully implemented (yet)
Aug  8 09:58:36 ubuntu kernel: [ 2123.412060] usb 4-2: reset low speed USB device using ohci_hcd and address 2
Aug  8 09:58:37 ubuntu kernel: [ 2123.565758] wlan0: ethernet device 00:13:f7:51:f8:06 using NDIS driver: smcusbt, version: 0x10005, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 083A:4507.F.conf
Aug  8 09:58:37 ubuntu kernel: [ 2123.662870] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Aug  8 09:58:41 ubuntu kernel: [ 2127.512889] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug  8 09:59:50 ubuntu kernel: [ 2197.142193] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


Help is very much appreciated!

---

### Post by kkaras on 2009-08-08
I don't know whether it is related or not, but I saw the following in /var/log/messages when I plugged the wired cable into the laptop:


Aug  8 10:12:42 ubuntu kernel: [ 2969.000048] ------------[ cut here ]------------
Aug  8 10:12:42 ubuntu kernel: [ 2969.000056] WARNING: at /build/buildd/linux-2.6.28/net/sched/sch_generic.c:226 dev_watchdog+0x219/0x230()
Aug  8 10:12:42 ubuntu kernel: [ 2969.000060] NETDEV WATCHDOG: eth0 (sis900): transmit timed out
Aug  8 10:12:42 ubuntu kernel: [ 2969.000063] Modules linked in: wlan nfs lockd nfs_acl sunrpc video output input_polldev sbp2 lp joydev snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq pcmcia ppdev snd_timer snd_seq_device psmouse sis_agp pcspkr serio_raw yenta_socket rsrc_nonstatic pcmcia_core ndiswrapper asus_laptop i2c_sis96x snd soundcore snd_page_alloc shpchp agpgart irda led_class parport_pc parport crc_ccitt usbhid ohci1394 ieee1394 sis900 mii floppy fbcon tileblit font bitblit softcursor
Aug  8 10:12:42 ubuntu kernel: [ 2969.000118] Pid: 0, comm: swapper Tainted: P           2.6.28-14-generic #47-Ubuntu
Aug  8 10:12:42 ubuntu kernel: [ 2969.000122] Call Trace:
Aug  8 10:12:42 ubuntu kernel: [ 2969.000134]  [<c0139aa0>] warn_slowpath+0x60/0x80
Aug  8 10:12:42 ubuntu kernel: [ 2969.000144]  [<c01569b3>] ? getnstimeofday+0x53/0x110
Aug  8 10:12:42 ubuntu kernel: [ 2969.000149]  [<c01549a5>] ? sched_clock_cpu+0xd5/0x170
Aug  8 10:12:42 ubuntu kernel: [ 2969.000154]  [<c02cb8ad>] ? strlcpy+0x1d/0x60
Aug  8 10:12:42 ubuntu kernel: [ 2969.000161]  [<c042e0d2>] ? netdev_drivername+0x32/0x40
Aug  8 10:12:42 ubuntu kernel: [ 2969.000165]  [<c0442ca9>] dev_watchdog+0x219/0x230
Aug  8 10:12:42 ubuntu kernel: [ 2969.000170]  [<c043857b>] ? neigh_table_init_no_netlink+0x14b/0x1d0
Aug  8 10:12:42 ubuntu kernel: [ 2969.000174]  [<c0437d50>] ? neigh_periodic_timer+0x0/0x190
Aug  8 10:12:42 ubuntu kernel: [ 2969.000181]  [<c0144527>] ? mod_timer+0x37/0x80
Aug  8 10:12:42 ubuntu kernel: [ 2969.000184]  [<c0437e76>] ? neigh_periodic_timer+0x126/0x190
Aug  8 10:12:42 ubuntu kernel: [ 2969.000188]  [<c0143af0>] run_timer_softirq+0x130/0x200
Aug  8 10:12:42 ubuntu kernel: [ 2969.000192]  [<c0442a90>] ? dev_watchdog+0x0/0x230
Aug  8 10:12:42 ubuntu kernel: [ 2969.000195]  [<c0442a90>] ? dev_watchdog+0x0/0x230
Aug  8 10:12:42 ubuntu kernel: [ 2969.000202]  [<c013f197>] __do_softirq+0x97/0x170
Aug  8 10:12:42 ubuntu kernel: [ 2969.000206]  [<c013f2cd>] do_softirq+0x5d/0x60
Aug  8 10:12:42 ubuntu kernel: [ 2969.000210]  [<c013f445>] irq_exit+0x55/0x90
Aug  8 10:12:42 ubuntu kernel: [ 2969.000217]  [<c0106853>] do_IRQ+0x83/0xa0
Aug  8 10:12:42 ubuntu kernel: [ 2969.000226]  [<c0181937>] ? rcu_needs_cpu+0x37/0x50
Aug  8 10:12:42 ubuntu kernel: [ 2969.000230]  [<c01051f3>] common_interrupt+0x23/0x30
Aug  8 10:12:42 ubuntu kernel: [ 2969.000237]  [<c0121f75>] ? native_safe_halt+0x5/0x10
Aug  8 10:12:42 ubuntu kernel: [ 2969.000241]  [<c010afcd>] default_idle+0x5d/0x60
Aug  8 10:12:42 ubuntu kernel: [ 2969.000245]  [<c010285d>] cpu_idle+0x6d/0xd0
Aug  8 10:12:42 ubuntu kernel: [ 2969.000253]  [<c04ee48e>] rest_init+0x4e/0x60
Aug  8 10:12:42 ubuntu kernel: [ 2969.000256] ---[ end trace 2bd650f39bfab51a ]---

---

### Post by kkaras on 2009-08-10
How can I find out if the ndiswrapper is working properly?

---

### Post by redbook4574 on 2009-08-10
> **kkaras said:**
> Hi Guys, I could really use some help here! I simply can not get my WPA to work.

I have an SMC "SMCWUSBT-G2" usb wireless modem and the matching router. The router has the newest firmware. As SMC does not supply a linux driver, I use ndiswrapper.

With WPA enabled, I can not get 'data through' to the router. If I disable the WPA encryption, I have no problems. It works on Windows with WPA.

Whith WPA enabled, the NetworkManager does state that I'm connected, but I am not able to get any 'data through': In Wireshark I can see that no ARP or DHCP requests is replied by the router. The only PDUs I get from the router is EAPOL KEY (which is part of the WPA protocol). From the wpa_supplicant log, I get the following, which I interpret as encryption is working:


CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:13:f7:53:ef:00 (SSID='stace' freq=2472 MHz)
Associated with 00:13:f7:53:ef:00
WPA: Key negotiation completed with 00:13:f7:53:ef:00 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 00:13:f7:53:ef:00 completed (auth) [id=0 id_str=]
WPA: Key negotiation completed with 00:13:f7:53:ef:00 [PTK=CCMP GTK=CCMP]
WPA: Key negotiation completed with 00:13:f7:53:ef:00 [PTK=CCMP GTK=CCMP]
WPA: Key negotiation completed with 00:13:f7:53:ef:00 [PTK=CCMP GTK=CCMP]
Associated with 00:13:f7:53:ef:00
CTRL-EVENT-SCAN-RESULTS 
WPA: Key negotiation completed with 00:13:f7:53:ef:00 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 00:13:f7:53:ef:00 completed (reauth) [id=0 id_str=]


The above continues until I do something to abrupt the connection. From the /var/log/messages I get the following when I plug the USB into my laptop:


Aug  8 09:58:34 ubuntu kernel: [ 2121.017447] device wlan0 left promiscuous mode
Aug  8 09:58:34 ubuntu kernel: [ 2121.048742] ndiswrapper: device wlan0 removed
Aug  8 09:58:35 ubuntu kernel: [ 2122.448043] usb 1-5: new high speed USB device using ehci_hcd and address 5
Aug  8 09:58:36 ubuntu kernel: [ 2122.613469] usb 1-5: configuration #1 chosen from 1 choice
Aug  8 09:58:36 ubuntu kernel: [ 2122.756053] usb 1-5: reset high speed USB device using ehci_hcd and address 5
Aug  8 09:58:36 ubuntu kernel: [ 2122.904963] ndiswrapper: driver smcusbt (SMC,04/24/2006,1.5.0.102) loaded
Aug  8 09:58:36 ubuntu kernel: [ 2122.915530] ndiswrapper (ZwQueryValueKey:2330): not fully implemented (yet)
Aug  8 09:58:36 ubuntu kernel: [ 2123.412060] usb 4-2: reset low speed USB device using ohci_hcd and address 2
Aug  8 09:58:37 ubuntu kernel: [ 2123.565758] wlan0: ethernet device 00:13:f7:51:f8:06 using NDIS driver: smcusbt, version: 0x10005, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 083A:4507.F.conf
Aug  8 09:58:37 ubuntu kernel: [ 2123.662870] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Aug  8 09:58:41 ubuntu kernel: [ 2127.512889] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug  8 09:59:50 ubuntu kernel: [ 2197.142193] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


Help is very much appreciated!

I know this is probably not very helpful, I recently had similar problem using ndiswrapper with network manager and a BT router. I then found using wicd connected ok with a fixed ip, but a native linux driver works with no problems ie dhcp.

---

### Post by kkaras on 2009-08-10
I have tried wicd without any luck, and I do not know of a native linux driver for that wireless card...

---

### Post by phillw on 2009-08-10
I believe this gentleman solved it ...

[http://packman86.wordpress.com/2008/02/24/wifi-usb-drivers-in-linux/](http://packman86.wordpress.com/2008/02/24/wifi-usb-drivers-in-linux/)

Hope you have similar success.

regards,

Phill.

---

### Post by kkaras on 2009-08-11
That's exactly what I did (and tried some other stuff too), but I can get i to work

---

### Post by kkaras on 2009-08-11
Should have been: ... can not get it to work...

---

### Post by Threbus5 on 2009-08-11
You appeared to state that with WPA disabled the wireless card worked.
That suggests compatability between the card and network hardware.

The computer's inability to achieve WPA connectivity could result from a WPA misconfiguration. (Just because the machine says that it is connected does not mean that it is connected well enough to provide network services. Think about it, at some point you surely have observed a listing of available networks - some encrypted and some not. Under those conditions your computer is connected to all of those networks too but it cannot necessarily exchange data over them.)

I always look for the simple solution.

Did you verify that the WPA key for the computer matches the wireless network's key?

Good luck.

---

### Post by buster2 on 2009-08-11
I have the same problem. I have two Laptops with belkin dongles.
one running xandross one running ubuntu 9.04. setup with ndiswrapper.
xandross works great with wpa or no security.
ubuntu works great with no security. go into router change security to wpa /wpa2 personel
xandross still perfect
ubuntu connects shows full 68% strength but wont access internet.

---

### Post by alphacrucis2 on 2009-08-11
> **buster2 said:**
> I have the same problem. I have two Laptops with belkin dongles.
one running xandross one running ubuntu 9.04. setup with ndiswrapper.
xandross works great with wpa or no security.
ubuntu works great with no security. go into router change security to wpa /wpa2 personel
xandross still perfect
ubuntu connects shows full 68% strength but wont access internet.

Do you have mode set to 'Infrastructure'?

---

### Post by buster2 on 2009-08-11
Yes mode is set for infrastructure

---

### Post by kkaras on 2009-08-11
Threbus5: Yes, the key is correct. Any other suggestion?

What I find really strange is that in the two setups (with WPA enabled or without WPA) the only difference is the configuration of the WPA password. 

Hence, I'm thinking there might be a problem with the communication between the ndiswrapper and the component that does the encryption/decryption. 
Any one knows where logging of the ndiswrapper is placed???

---

