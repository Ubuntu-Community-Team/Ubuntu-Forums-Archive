---
title: "Hardy wireless suddenly stopped working"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by thedaylights on 2008-10-09
My wireless was working fine last night, then an hour later it stopped. I can't connect now. I must have accidentally shifted the hardware switch for the wireless card because it was off this morning. But even after switching wireless to on I can't connect. It shows the wireless network, but it won't connect.

I'm using a Lenovo X60 t.

I am running the Hardy LiveCD now and connected wirelessly no problem.
This is the output of lshw -C network on my Hardy install.
> anthony@lappy:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: ****censored****
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.5-1 latency=0 module=e1000 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: ****censored****
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

It is the same as the output of lshw -C network on the liveCD.

---

### Post by superprash2003 on 2008-10-09
what is the output of iwconfig ?? have you tried rebooting pc..

---

### Post by thedaylights on 2008-10-09
> **superprash2003 said:**
> what is the output of iwconfig ?? have you tried rebooting pc..

iwconfig output from my Hardy install:
> anthony@lappy:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:[QUOTE]off   Fragment thr=2346 B   
          Power Management:> off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/QUOTE]
And I have rebooted many times - each time I need to run a check on my system (such as iwconfig) and then each time I need internet access I boot to liveCD because wireless works from liveCD.

---

