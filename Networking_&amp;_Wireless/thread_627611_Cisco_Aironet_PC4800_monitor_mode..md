---
title: "Cisco Aironet PC4800 monitor mode."
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by sysape on 2007-11-30
I've just installed a cisco aironet pci card in my machine which is running Fiesty and like some other users can't seem to get it into monitor  mode. 

Maybe I should be asking this question on the airo driver forum. but I thought I might start here. 

The driver seems to load fine 

```

root@Lugh:~# lspci -v | tail -6
03:06.0 Network controller: AIRONET Wireless Communications PC4800 (rev 01)
        Flags: medium devsel, IRQ 20
        Memory at cffff000 (32-bit, non-prefetchable) [size=128]
        I/O ports at ac00 [size=128]
        I/O ports at a800 [size=64]

root@Lugh:~# lsmod | grep airo
airo                   74400  0 

```

and iwconfig seems to work

```

root@Lugh:~# iwconfig eth1
eth1      IEEE 802.11-DS  ESSID:"Square Mile"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=-112 dBm  Noise level=-112 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

```

but when we try 'iwconfig eth1 mode monitor'  it doesn't change the mode to 'monitor' this also means that kismet doesn't work, nor airsnort,  which is the real problem.

interestingly

```

root@Lugh:~# iwlist eth1 scanning
eth1      No scan results

```

Which could be the same problem. I've been trying to work out if the airo driver/card does support monitor mode or not, and can't find out for sure, but [http://www.*******.net/~kos/wifi/monitor-cisco.html](http://www.*******.net/~kos/wifi/monitor-cisco.html)  (ffs that's b a s t a r d <dot> n e t ) seems to suggest it should. This page [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsCisco](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsCisco)   seems to say the card works with ubuntu. but that I should have the latest firmware which I am currently struggling to get from cisco. 

So what am I asking? er I suppose I'm asking does anyone know how to get monitor mode working on an aironet card under linux, and does anyone know where I can actually download a set of cisco drivers and utils for linux from as [http://tools.cisco.com/support/downloads/pub/MDFTree.x?butype=wireless](http://tools.cisco.com/support/downloads/pub/MDFTree.x?butype=wireless) doesn't seem to have the linux ones.

tvmia 

M

---

