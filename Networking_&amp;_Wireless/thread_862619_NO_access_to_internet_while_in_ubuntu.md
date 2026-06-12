---
title: "NO access to internet while in ubuntu"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by amsemt on 2008-07-17
Hi I installed ubuntu onto my computer as well using a free program that allows me to be able to boot into either windows vista or ubuntu. It just gives me an option when I turn my computer on and yeah that's basically it. I cant remember the program name right now but thats the setup. Im using an [COLOR=red]HP Pavilion dv2000[/COLOR] laptop and I just can not find a way to connect to my linksys connection when running ubuntu. When running vista it connects just fine and all on its own, however I do have to use a static ip address whenever I want to connect. I've looked around and tried using the terminal but I am completely new so it didnt get me very far and I couldnt find any advice that really solved the problem. The linksys router version is [COLOR=red]1.1[/COLOR] and model is [COLOR=red]WRT54GS[/COLOR] and its an unsecure network. I tried to manage my own connection for a while but couldnt get my head around the fact that it asked for a network key... when I didnt have one! So I gave up on that and today I switched it to roaming. First I selected create new network and that did not work. Then I selected use other network and put in linksys for the name and it still does not work. All it sais when I hover over the grey reception bars is, “wireless connection to 'linksys' (0%)” So anyways I typed the commands you listed in your post and got the information below. I have also tried #sudo gedit/etc/modprobe.d/bad-list and then alias net-pf-10 off but that did nothing and I tried sudo pppoeconf (yes) but it said it could not connect to neither of the wlan0 or eth0 (I think thats what they were called) so I didnt try enetering in the “sudp pon dsl-provider” script. Sorry if this message was too jumbled up but im just trying to get this to work and I will try and clear any confusion up. So any help would be much appreciated. Thanks. 



[COLOR=red]amsemt@amsemt-laptop:~$ sudo lshw -C network[/COLOR]
[COLOR=red][sudo] password for amsemt: [/COLOR]
[COLOR=red]*-network [/COLOR]
[COLOR=red]description: Network controller[/COLOR]
[COLOR=red]product: BCM94311MCG wlan mini-PCI[/COLOR]
[COLOR=red]vendor: Broadcom Corporation[/COLOR]
[COLOR=red]physical id: 0[/COLOR]
[COLOR=red]bus info: pci@0000:01:00.0[/COLOR]
[COLOR=red]version: 01[/COLOR]
[COLOR=red]width: 32 bits[/COLOR]
[COLOR=red]clock: 33MHz[/COLOR]
[COLOR=red]capabilities: pm msi pciexpress bus_master cap_list[/COLOR]
[COLOR=red]configuration: driver=b43-pci-bridge latency=0 module=ssb[/COLOR]
[COLOR=red]*-network DISABLED[/COLOR]
[COLOR=red]description: Wireless interface[/COLOR]
[COLOR=red]physical id: 1[/COLOR]
[COLOR=red]logical name: wlan0[/COLOR]
[COLOR=red]serial: 00:1a:73:0c:1a:ac[/COLOR]
[COLOR=red]capabilities: ethernet physical wireless[/COLOR]
[COLOR=red]configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g[/COLOR]
[COLOR=red]amsemt@amsemt-laptop:~$ iwconfig[/COLOR]
[COLOR=red]lo no wireless extensions.[/COLOR]

[COLOR=red]eth0 no wireless extensions.[/COLOR]

[COLOR=red]wmaster0 no wireless extensions.[/COLOR]

[COLOR=red]wlan0 IEEE 802.11g ESSID:"" [/COLOR]
[COLOR=red]Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated [/COLOR]
[COLOR=red]Tx-Power=27 dBm [/COLOR]
[COLOR=red]Retry min limit:7 RTS thr: off Fragment thr=2346 B [/COLOR]
[COLOR=red]Link Quality:0 Signal level:0 Noise level:0[/COLOR]
[COLOR=red]Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0[/COLOR]
[COLOR=red]Tx excessive retries:0 Invalid misc:0 Missed beacon:0[/COLOR]

[COLOR=red]amsemt@amsemt-laptop:~$ ifconfig[/COLOR]
[COLOR=red]eth0 Link encap:Ethernet HWaddr 00:16:d3:19:be:36 [/COLOR]
[COLOR=red]UP BROADCAST MULTICAST MTU:1500 Metric:1[/COLOR]
[COLOR=red]RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/COLOR]
[COLOR=red]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/COLOR]
[COLOR=red]collisions:0 txqueuelen:1000 [/COLOR]
[COLOR=red]RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)[/COLOR]
[COLOR=red]Interrupt:20 Base address:0x6000 [/COLOR]

[COLOR=red]lo Link encap:Local Loopback [/COLOR]
[COLOR=red]inet addr:127.0.0.1 Mask:255.0.0.0[/COLOR]
[COLOR=red]inet6 addr: ::1/128 Scope:Host[/COLOR]
[COLOR=red]UP LOOPBACK RUNNING MTU:16436 Metric:1[/COLOR]
[COLOR=red]RX packets:320 errors:0 dropped:0 overruns:0 frame:0[/COLOR]
[COLOR=red]TX packets:320 errors:0 dropped:0 overruns:0 carrier:0[/COLOR]
[COLOR=red]collisions:0 txqueuelen:0 [/COLOR]
[COLOR=red]RX bytes:18408 (17.9 KB) TX bytes:18408 (17.9 KB)[/COLOR]

[COLOR=red]amsemt@amsemt-laptop:~$ lspci -nn[/COLOR]
[COLOR=red]00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)[/COLOR]
[COLOR=red]00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)[/COLOR]
[COLOR=red]00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)[/COLOR]
[COLOR=red]00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)[/COLOR]
[COLOR=red]00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)[/COLOR]
[COLOR=red]00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)[/COLOR]
[COLOR=red]00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)[/COLOR]
[COLOR=red]00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)[/COLOR]
[COLOR=red]00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)[/COLOR]
[COLOR=red]00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)[/COLOR]
[COLOR=red]00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2)[/COLOR]
[COLOR=red]00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)[/COLOR]
[COLOR=red]00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)[/COLOR]
[COLOR=red]00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)[/COLOR]
[COLOR=red]00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)[/COLOR]
[COLOR=red]00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)[/COLOR]
[COLOR=red]00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)[/COLOR]
[COLOR=red]00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)[/COLOR]
[COLOR=red]00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)[/COLOR]
[COLOR=red]00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)[/COLOR]
[COLOR=red]00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)[/COLOR]
[COLOR=red]00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)[/COLOR]
[COLOR=red]00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100][/COLOR]
[COLOR=red]00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101][/COLOR]
[COLOR=red]00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102][/COLOR]
[COLOR=red]00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103][/COLOR]
[COLOR=red]01:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)[/COLOR]
[COLOR=red]03:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832][/COLOR]
[COLOR=red]03:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)[/COLOR]
[COLOR=red]03:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 0a)[/COLOR]
[COLOR=red]03:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 05)[/COLOR]
[COLOR=red]03:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)[/COLOR]

---

### Post by amsemt on 2008-07-18
i looked at some other posts and found this code to update it:
 
[COLOR=red]sudo apt-get update
sudo apt-get install b43-fwcutter[/COLOR]
[COLOR=#ff0000][/COLOR] 
[COLOR=black]would that code work for my system also?[/COLOR]
or am i just screwed haha?

---

### Post by falcon61102 on 2008-07-18
You're not screwed and using fwcutter may work for you as I've heard it has worked for others with Broadcom.  I have a similar card and have had good success with ndiswrapper but either way, you should be able to get wireless going.

I'm about to head out the door but if you want a good HowTo for ndiswrapper, here you go:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

That should get you going, if not just post any questions/errors here and there are plenty of people that are good at figuring this out.

---

### Post by amsemt on 2008-07-18
thank you very much. i will try the fwcutter and if that does not work ill move on to trying the ndiswrapper. Ill post my results when i figure it out. thanks again.

---

