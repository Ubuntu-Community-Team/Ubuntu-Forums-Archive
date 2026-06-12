---
title: "Atheros AR242x HW Rev. not supported"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by Margate on 2008-11-10
Hi,
My daughter wants to use Ubuntu, but she need support for wireless in school, home and other places, she have a brand new FSC Amilo Pa 3515 with a build in AR242x wireless card. I installed 8.10 and everything works fine apart from wireless. I have tried with new restricted drivers there don't support Atheros HW (rev 04). I managed to load and actually see a wireless card with madwifi and linuxwireless drivers, however i was not able to bring radio on with the Fn-F1 keypress, but i think it is another story; because I don't see increments in interrupts from i8042 controller when I 
```
watch 'cat /proc/interrupts'

```
and press Fn-F1. 
i8042 counter are incremented when I press Fn-F3, Fn-F4, Fn-F5 and Fn-F7 where turns on Video, also with xev I see same symptoms, no response with Fn-F1 others okay.

So my status for the moment is:
madwifi loads and give me a card in ifconfig and iwconfig, but am not able to turn radio on with Fn-F1

restricted drivers load modules, but fails on HW revision.

My reason for choosing 8.10 was much better support for wireless card and especially I hoped atheros restricted drivers would help me out.


These outputs are made with restricted drivers loaded

lspci
```
08:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 04)

```

lsmod | grep ath
```
ath5k                 107648  0 
mac80211              207920  1 ath5k
led_class              12164  1 ath5k
cfg80211               40084  2 ath5k,mac80211
ath_pci                99096  0 
wlan                  211952  1 ath_pci
ath_hal               198864  1 ath_pci

```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:1f:16:06:4b:49  
          inet addr:192.168.1.32  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67358 (67.3 KB)  TX bytes:42882 (42.8 KB)
          Interrupt:219 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)

pan0      Link encap:Ethernet  HWaddr 66:83:1d:00:a5:10  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

/var/log/syslog
```
Nov 10 07:34:30 lunas kernel: [  199.045075] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Nov 10 07:34:30 lunas kernel: [  199.074049] wlan: 0.9.4
Nov 10 07:34:30 lunas kernel: [  199.089944] ath_pci: 0.9.4
Nov 10 07:34:30 lunas kernel: [  199.090405] ath_pci 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 10 07:34:30 lunas kernel: [  199.090436] ath_pci 0000:08:00.0: setting latency timer to 64
Nov 10 07:34:30 lunas kernel: [  199.115586] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
Nov 10 07:34:30 lunas kernel: [  199.115625] ath_pci 0000:08:00.0: PCI INT A disabled
Nov 10 07:34:46 lunas kernel: [  214.597142] cfg80211: Using static regulatory domain info
Nov 10 07:34:46 lunas kernel: [  214.597155] cfg80211: Regulatory domain: US
Nov 10 07:34:46 lunas kernel: [  214.597161] ^I(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 10 07:34:46 lunas kernel: [  214.597171] ^I(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
Nov 10 07:34:46 lunas kernel: [  214.597178] ^I(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Nov 10 07:34:46 lunas kernel: [  214.597184] ^I(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Nov 10 07:34:46 lunas kernel: [  214.597190] ^I(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Nov 10 07:34:46 lunas kernel: [  214.597196] ^I(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Nov 10 07:34:46 lunas kernel: [  214.597202] ^I(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
Nov 10 07:34:46 lunas kernel: [  214.597208] cfg80211: Calling CRDA for country: US
Nov 10 07:34:46 lunas kernel: [  214.668728] ath5k_pci 0000:08:00.0: enabling device (0000 -> 0002)
Nov 10 07:34:46 lunas kernel: [  214.668747] ath5k_pci 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 10 07:34:46 lunas kernel: [  214.668764] ath5k_pci 0000:08:00.0: setting latency timer to 64
Nov 10 07:34:46 lunas kernel: [  214.668804] ath5k_pci 0000:08:00.0: registered as 'phy0'
Nov 10 07:34:46 lunas kernel: [  214.678822] ath5k phy0: failed to wakeup the MAC Chip
Nov 10 07:34:46 lunas kernel: [  214.678862] ath5k_pci 0000:08:00.0: PCI INT A disabled
Nov 10 07:34:46 lunas kernel: [  214.692064] ath5k_pci: probe of 0000:08:00.0 failed with error -5
Nov 10 07:41:38 lunas anacron[5385]: Job `cron.weekly' started
Nov 10 07:41:38 lunas anacron[6313]: Updated timestamp for job `cron.weekly' to 2008-11-10
Nov 10 07:43:13 lunas syslogd 1.5.0#2ubuntu6: restart.
Nov 10 07:43:13 lunas anacron[5385]: Job `cron.weekly' terminated
Nov 10 07:43:13 lunas anacron[5385]: Normal exit (1 job run)

```

Do I have one issue with Fn-F1 and another with wireless;

will I be able to get madwifi working if Fn-F1 is solved,

I properly have to wait for updated restricted atheros drivers, I understand they are in heavily development for the moment. 

Kind Regards
Margate

---

### Post by iliaarpad on 2008-11-12
I seem to have a similar problem. The button that would turn wireless on/off doesn't seem to do anything. I tried both Kubuntu 8.04 and Kubuntu 8.10 to no avail.

Thanks for reading!

---

