---
title: "Wireless internet connection drop."
date: 2009-04-05
forum: New to Ubuntu
---

### Post by Amorata on 2009-04-05
Hey,

Posted here since my knowledge in Linux is limited.

I have the same problem discussed in this bugreport:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182473?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182473?comments=all)

**Symptoms are**: low network connection quality and that the network drops connection when traffic up-load is over a certain level. In download I have none experience of this problem. I have to modprobe my driver in and out and restart the network to get back up. This is, as you probably understand, quite annoying when I'm live streaming or downloading torrents. There is also NO entries in the logs about this drop of connectivity?!? So I won't bother gluing in any of them. It also seems like everything is in order; icon on desktop shows connection and lights on card is idle but no connection.

Firstly: After checking dmesg i found that this "might" have been caused by an obsolete firmware to my 3com wireless networkcard:

[INDENT][   36.316594] firmware: requesting isl3886pci                                                                                                                                 
[   37.739943] 0000:06:00.0 (p54pci): cannot find firmware (isl3886pci)                                                                                                        
[   37.739963] firmware: requesting isl3886                                                                                                                                    
[   37.795060] phy0: p54 detected a LM86 firmware                                                                                                                              
[   37.795076] phy0: FW rev 2.7.0.0 - Softmac protocol 4.1                                                                                                                     
[   37.795086] phy0: you are using an obsolete firmware. visit [http://wireless.kernel.org/en/users/Drivers/p54](http://wireless.kernel.org/en/users/Drivers/p54) and grab one for "kernel >= 2.6.28"![/INDENT]   

Well. I have fetched the file which name is: 2.13.1.0.arm and now I have no idea of what to do with that file. The "how-to" on site is somewhat kryptic to me: [http://wireless.kernel.org/en/users/Drivers/p54#firmware](http://wireless.kernel.org/en/users/Drivers/p54#firmware)

and I would appreciate if someone could guide me trough what to actually do with that file...

Second: After reading the bug report I have a strong suspicion that this actually won't fix the problem and that this is a kernel bug. I have very poor skills in programming so I can't help that way. But if anyone has had the same problem, and have a operative solution that would be highly appreciated.

lspci -vvnn yields this:
[INDENT]06:00.0 Network controller [0280]: 3Com Corporation 3com 3CRWE154G72 [Office Connect Wireless LAN Adapter] [10b7:6001] (rev 01)
        Subsystem: 3Com Corporation Device [a727:6001]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
        Latency: 64 (2500ns min, 7000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at 2c000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [dc] Power Management version 1
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: p54pci
        Kernel modules: p54pci, prism54

[/INDENT]
Iwconfig gives this result:
[INDENT]wlan0     IEEE 802.11bg  ESSID:"Room_With_A_Moose"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:10:06:AF:9C
          Bit Rate=1 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          **Link Quality=59/100  Signal level:-62 dBm  Noise level=-86 dBm**
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/INDENT]
As you can see; the quality and levels are totally off. I'm seated 7 meters from the modem and has straight air access to it...

uname -a:
[INDENT]Linux Devils-Angel 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
[/INDENT]

version: 
[INDENT]Ubuntu 2.6.27-11.27-generic
[/INDENT]

Thanks for any assistance 
Amorata

---

### Post by zigga15 on 2009-04-05
Had the same problem.. It is because your reception is too low.

I got a new access point for around $100 AUD and moved it closer to my room, it never dropped out again after that.

Basically if it is below half way it will drop out. Windows machines do it as well. (I have a windows partition on one of my computers which does the same thing as the linux boot).

If you are using a USB receiver like I was try and 3-4 meter extension or moving it around, basically you need to get your reception up over half way.

If you have trouble re-connecting and cant afford to upgrade any of the stuff I mention then you need to manually flush the IP routing tables, arp cache etc. Or just reset the router.

---

### Post by Amorata on 2009-04-05
Thanks for the fast reply. Greatly appreciated :) You are completely correct. It is the low connection quality that makes the connection drop.

As I mentioned I think this is related to the bug mentioned in the bug report and that it is that bug that makes the connection low, not the modem itself or my network card. There it is stated that the bug is the cause of the poor reception quality and therefor the loss of connection.

---

