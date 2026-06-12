---
title: "ipw3925 (Intel/PRO Wireless 3945ABG) slow download speeds compared to Windows"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by SundeepG on 2007-07-14
Hey guys, sorry for posting this same problem again, but all the other threads I checked didnt have any solution to them. I just recently installed Ubuntu 7.04 and am a complete newb to Linux. However, I seem to be getting this same problem that many ppl with this driver (ipw3945) are experiencing. When I boot to windows XP, I can get download speeds of 5.5mbps, with an upload of around 1.5mbps. However, _when running in Linux_, my downloads usually _cap out around 40KB/_s, with a speed test result of around **800-1200kbps downstream** (jumps a lot), yet my upload speeds are fine at **1.5mbps upstream**. As you can see, I am only experiencing problems in my downstream rate. I am running the latest stable version of the ipw3945 driver:

**driverinfo:**
sghuman@sghuman-laptop:~$ iwconfig eth1
eth1      IEEE 802.11b  ESSID:"MSHOME"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:50:F2:72:C2:22   
          Bit Rate:11 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          **Link Quality=79/100  Signal level=-55 dBm  Noise level=-56 dBm**
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  **Invalid misc:10740**   Missed beacon:0

sghuman@sghuman-laptop:~$ modinfo ipw3945
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/ipw3945/ipw3945.ko
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.0mp
description:    Intel(R) PRO/Wireless 3945 Network Connection driver for Linux
srcversion:     9B03103B15A8FE1824967C2
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
depends:        ieee80211
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default 0 off) (int)
parm:           auto_create:auto create adhoc network (default 1 on) (int)
parm:           led:enable led control (default 1 on)
 (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)

**Broadband Reports TweakTest Results:**
[http://www.dslreports.com/tweakr/block:2256a63?service=cable&speed=6000&os=Linux&via=normal](http://www.dslreports.com/tweakr/block:2256a63?service=cable&speed=6000&os=Linux&via=normal)

I found other threads (non-Ubuntu) related to this problem, but with no solutions. Some of the facts they brought up was the signal strength only being 1dB higher than the noise floor in people who experienced this problem and the invalid misc # being really high. Can anyone help me out here?

Thanks

---

### Post by jeyno on 2007-09-27
Hey Sundeep, I see you posted this a few months back - now that's a long time to cope with a slow connection.  I wonder have you resolved this?  if so, how?  I experence EXACTLY the same symptom.

---

### Post by ubuntuross on 2007-09-30
I have this same problem.  Does anyone know of a solution?

ross

---

### Post by J-Rod on 2007-09-30
I also have the same issue, different card though. Thinkpad R40 Cisco 350 minipci. Had no problems with the card in windoze, running Feisty, and it's very slow compared to my wired speed on the main, and the wireless speed when Ubuntu is loaded on this laptop. I have disabled ipv6, but that is about it so far, I haven't found much for improving speeds, most of the threads seem to be based on getting the wireless to work at all. :)

---

### Post by suliman on 2007-11-18
I as well have been experiencing slow download speeds with the ipw3945 (which is in an Acer 5610 laptop).  Have tried many of the suggestions, was hoping gutsy would do the trick, but no such luck.  I would also very much appreciate a fix/workaround for this problem.

Still very confused why signal is only 1 dB higher than noise ??

---

### Post by turt1e on 2007-11-21
I was having similar problems with Fiesty and came to the conclusion that it was due to using Network-manager.  Once I disabled network-manager from starting up under Sessions -> Startup Programs tab, and then installed WiFi Radar my network speeds are now what they should be.

---

