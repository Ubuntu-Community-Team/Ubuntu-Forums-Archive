---
title: "Problem with sound and networking"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by sajd on 2010-10-06
Hi, i am newbie at ubuntu, and i was looking on google to find solution of this problem but i havent find yet :) so let's start explaning the problem.I have installed ubuntu 10.04 to my pc (Mainboard MSI P4N DIAMON,HDD 200GB, 2GB RAM,VGA 8600gt 512mb ddr3), when i play some music the network adapter is blocked and it fall down if i am connected on some network and the sound is also blocked,it repeats like scratched cd when you play on a cd player.If i choose STOP NETWORKING all problem with the sound disapears, it works all fine.Also if i am on internet and i watch youtube, i've got the same problem. how can i fix the problem :) any suggestions ? and sorry for my bad english :)

---

### Post by cariboo on 2010-10-06
MSI motherboards are kind of strange, as when you run:

```
lspci
```

The Ethernet device never shows up. So could you post the output of:

```
sudo lshw -C 
```

To run the above command, open a Applications->Accessories->Terminal, then copy and paste the command.

You can then copy and paste the results in your next post.

---

### Post by sajd on 2010-10-06
after LSPCI it gives me this: 



00:00.0 Host bridge: nVidia Corporation Device 0071 (rev a1)
00:00.1 RAM memory: nVidia Corporation Device 007f (rev a1)
00:00.2 RAM memory: nVidia Corporation Device 0075 (rev a1)
00:00.3 RAM memory: nVidia Corporation Device 006f (rev a1)
00:00.4 RAM memory: nVidia Corporation Device 00b4 (rev a1)
00:01.0 RAM memory: nVidia Corporation Device 0076 (rev a1)
00:01.1 RAM memory: nVidia Corporation Device 0078 (rev a1)
00:01.2 RAM memory: nVidia Corporation Device 0079 (rev a1)
00:01.3 RAM memory: nVidia Corporation Device 007a (rev a1)
00:01.4 RAM memory: nVidia Corporation Device 007b (rev a1)
00:01.5 RAM memory: nVidia Corporation Device 007c (rev a1)
00:01.6 RAM memory: nVidia Corporation Device 007d (rev a1)
00:02.0 PCI bridge: nVidia Corporation Device 007e (rev a2)
00:04.0 PCI bridge: nVidia Corporation Device 007e (rev a2)
00:05.0 PCI bridge: nVidia Corporation Device 007e (rev a2)
00:06.0 PCI bridge: nVidia Corporation Device 007e (rev a2)
00:09.0 RAM memory: nVidia Corporation Device 003f (rev a1)
00:0a.0 ISA bridge: nVidia Corporation Device 0030 (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP04 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP04 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP04 USB Controller (rev a1)
00:0b.2 USB Controller: nVidia Corporation MCP04 USB Controller (rev a2)
00:0e.0 Bridge: nVidia Corporation MCP04 Ethernet Controller (rev a2)
00:0f.0 IDE interface: nVidia Corporation MCP04 IDE (rev f2)
00:12.0 PCI bridge: nVidia Corporation MCP04 PCI Bridge (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
06:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46)
06:05.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
06:07.0 Network controller: RaLink RT2561/RT61 802.11g PCI



and after lshw -c


Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.14)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
	-numeric        output numeric IDs (for PCI, USB, etc.)

---

### Post by sajd on 2010-10-19
Anyone to help me ? :)

---

### Post by dimoftheyard on 2010-10-19
The second command did not work, could you run

```
sudo lshw
```

without the -C? And, of course, post the output here. For improved readability you could put that output in CODE delimiters (Putting [ CODE ] before the text, and [ / CODE ] after it, but both without the spaces. I can't figure out how to  write that here without starting a CODE-environment myself :) ).

---

