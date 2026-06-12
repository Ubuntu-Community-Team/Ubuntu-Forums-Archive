---
title: "Beklin USB Problems"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by ShakeyJake on 2007-05-03
Hey everyone, newbie here so be patient!

Ive just got my Linux box and Im trying to connect to my network. Im using the Belkin USB antennae so theres no driver issues or anyhing I think.

It can 'see' the network, its  in the top-right hand corner (by the time, volume etc) and then it asks me for the WEP key etc etc but when I click connect itll try for a few mins and then wont. Any ideas whats going on?

Thanks in advance:
Jack

---

### Post by dannyboy79 on 2007-05-03
every piece of hardware needs a driver for it to work for your FYI. maybe you mean that you heard that this usb adapter is supported "out of the box" in ubuntu and you think you don't need to install additional drivers but that's not really what you said. anyway, I can certainly help,  please post the output from the following commands entered into a terminal

dmesg | tail

lspci -v

---

### Post by ShakeyJake on 2007-05-03
This is  a bit of a problem, as I got a lot of text from that. I appreciate the help though!

Without further adue:

dmesg | tail 
[ 4234.860000] sdd: Mode Sense: 0b 00 00 08 
[ 4234.860000] sdd: assuming drive cache: write through 
[ 4234.860000]  sdd: sdd1 
[ 4234.872000] sd 3:0:0:0: Attached scsi removable disk sdd 
[ 4234.872000] sd 3:0:0:0: Attached scsi generic sg3 type 0 
[ 4253.700000] usb 2-1: new high speed USB device using ehci_hcd and address 7 
[ 4254.004000] usb 2-1: configuration #1 chosen from 1 choice 
[ 4254.404000] wmaster0: Selected rate control algorithm 'simple' 
[ 4254.588000] wlan0: starting scan 
[ 4255.544000] wlan0: scan completed 
user@ubuntu:~$ lspci -v 
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2) 
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0 
        Flags: bus master, 66MHz, fast devsel, latency 0 
        Capabilities: <access denied> 
 
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2) 
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0 
        Flags: 66MHz, fast devsel 
 
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2) 
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0 
        Flags: 66MHz, fast devsel 
 
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2) 
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0 
        Flags: 66MHz, fast devsel 
 
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2) 
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0 
        Flags: bus master, 66MHz, fast devsel, latency 0 
 
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2) 
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0 
        Flags: bus master, 66MHz, fast devsel, latency 0 
        Capabilities: <access denied> 
 
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2) 
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0 
        Flags: 66MHz, fast devsel 
 
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2) 
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0 
        Flags: 66MHz, fast devsel 
 
00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2) (prog-if 00 [VGA]) 
        Subsystem: ASUSTeK Computer Inc. Unknown device 81cd 
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21 
        Memory at fb000000 (32-bit, non-prefetchable) [size=16M] 
        Memory at e0000000 (64-bit, prefetchable) [size=256M] 
        Memory at fc000000 (64-bit, non-prefetchable) [size=16M] 
        [virtual] Expansion ROM at 88000000 [disabled] [size=128K] 
        Capabilities: <access denied> 
 
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2) 
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0 
        Flags: bus master, 66MHz, fast devsel, latency 0 
        Capabilities: <access denied> 
 
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3) 
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0 
        Flags: bus master, 66MHz, fast devsel, latency 0 
 
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3) 
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0 
        Flags: 66MHz, fast devsel, IRQ 255 
        I/O ports at 4c00 [size=64] 
        I/O ports at 4c40 [size=64] 
        Capabilities: <access denied> 
 
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3) 
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0 
        Flags: 66MHz, fast devsel 
 
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI]) 
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0 
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16 
        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K] 
        Capabilities: <access denied> 
 
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI]) 
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0 
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18 
        Memory at fe02e000 (32-bit, non-prefetchable) [size=256] 
        Capabilities: <access denied> 
 
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP]) 
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0 
        Flags: bus master, 66MHz, fast devsel, latency 0 
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8] 
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1] 
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8] 
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1] 
        I/O ports at f400 [size=16] 
        Capabilities: <access denied> 
 
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO]) 
        Subsystem: ASUSTeK Computer Inc. Unknown device 81c0 
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20 
        I/O ports at 09f0 [size=8] 
        I/O ports at 0bf0 [size=4] 
        I/O ports at 0970 [size=8] 
        I/O ports at 0b70 [size=4] 
        I/O ports at e000 [size=16] 
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K] 
        Capabilities: <access denied> 
 
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode]) 
        Flags: bus master, 66MHz, fast devsel, latency 0 
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=128 
        I/O behind bridge: 0000c000-0000cfff 
        Memory behind bridge: fdd00000-fddfffff 
        Prefetchable memory behind bridge: fde00000-fdefffff 
        Capabilities: <access denied> 
 
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2) 
        Subsystem: ASUSTeK Computer Inc. Unknown device 81cb 
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16 
        Memory at fe028000 (32-bit, non-prefetchable) [size=16K] 
        Capabilities: <access denied> 
 
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3) 
        Subsystem: ASUSTeK Computer Inc. Unknown device 816a 
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17 
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K] 
        I/O ports at dc00 [size=8] 
        Capabilities: <access denied> 
 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
        Flags: fast devsel 
        Capabilities: <access denied> 
 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
        Flags: fast devsel 
 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
        Flags: fast devsel 
 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
        Flags: fast devsel 
        Capabilities: <access denied> 
 
01:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI]) 
        Subsystem: ASUSTeK Computer Inc. Unknown device 2a22 
        Flags: bus master, medium devsel, latency 32, IRQ 19 
        Memory at fddff000 (32-bit, non-prefetchable) [size=2K] 
        I/O ports at cc00 [size=128] 
        Capabilities: <access denied>

---

### Post by ShakeyJake on 2007-05-03
Anyone? Im looking in similar threads now but I still cant find anything.

Thanks in advance,
Jack.

---

### Post by dannyboy79 on 2007-05-03
yep, you're having the same problem as me, I was trying to gert my belkin usb adapter (wireless) to work in Edgy and I had the same thing in my dmesg about wlan0 and I just couldn't for the life of me get it to work, then I even tried the ndiswrapper but that didn't work either but I haven't treied the link I have posted yet.

ok, are you guys using Edgy or Feisty? If you have the Belkin FDblah blah usb model, there is a great thread here: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

also, I read here ([http://ubuntuforums.org/showthread.php?t=430726](http://ubuntuforums.org/showthread.php?t=430726)) that the native rtblahblah drivers work in Feisty but are you using Feisty?

---

### Post by ShakeyJake on 2007-05-03
Yup,  Im using Fiesty.

Its a Belkin F5D7050B, if that helps. Yes, the same one everyone else is having trouble with!

---

### Post by dannyboy79 on 2007-05-03
> **ShakeyJake said:**
> Yup,  Im using Fiesty.

Its a Belkin F5D7050B, if that helps. Yes, the same one everyone else is having trouble with!

very weird, according to that link I posted, he was stating that his is working without doing anything. he didn't respond to my questions though so it's possible that he isn't telling is something. i'll PM him and then post back here. did you read the other link I provided, there is a solution!

---

### Post by ShakeyJake on 2007-05-03
There is a solution, but im afraid i dont understand. My ubuntu (and linux for that matter!) experience started about 3 hours ago.

Any chance you can give me the newbie version?

TIA,
Jack.

---

### Post by dannyboy79 on 2007-05-03
> **ShakeyJake said:**
> There is a solution, but im afraid i dont understand. My ubuntu (and linux for that matter!) experience started about 3 hours ago.

Any chance you can give me the newbie version?

TIA,
Jack.

I have already linked you to the guide, it doesn't get anymore newbie centric than that, sorry. don't be afraid of the terminal and just dive in and do it. that's all there is to it. ha, i just made a rhyme. 

a couple pointers for you. ALWAYS, first backup a file you're going to edit. that would be done with

sudo cp /location/filename /location/filename-backup

the cp command is copy. sudo is used to gain administrative privalages temporarily, you simply use the password you created when you created your username. DON'T get this confussed with the ROOT password, it's not!! Ubuntu by default does NOT have a root password, they don't want you logging in as root, that's why they use sudo. (NOTE: major damage can occur quickly if you're logged in as root)

other than that, the guide tellls you exactly what to do, now if you're doing this from a machine that had internet access and it's not your ubuntu machine, you're going to have to download all the files per the guide and transfer them over to your ubuntu box using usb stick or burn them to a cd or whatever. 
good luck, if you have problems, don't post here, post it at the guide, the guy who wrote it is very helpful.

---

### Post by mas99 on 2007-05-03
I was told that belkin actually shipped usb wifi dongles with two different chipsets - but the same part number.   That certainly matches my experience of failing to get a belkin working on edgy.   (I did eventually with the serialmonkey rt73)

best bet is to check the device manager for the usb id's and google for confirmation of the actual device details.

---

### Post by ShakeyJake on 2007-05-04
Right, Im trying the method mentioned in the threads I was linked to.

But, I cant seem to get past the first step :-(

I can try installing the linux-386 kernel, but it says there is no kernel 386. And when I try rebooting, the kernel im looking for in GRUB (386) isnt there.

Anyone? I am using a dual core (Athlon 4600+) so I do have to do the first step, right?

Sorry to be such a PITA.

---

### Post by dannyboy79 on 2007-05-07
are you using synaptic to find the 386 kernel? if you didn't install it than of course it won't be a selection within grub after you reboot. if you're using fiesty than I am not sure as I believe the guide is for dapper and edgy. your best bet wqould be to post in there not here as the person who wrote the guide would probably be able to tell you if those drivers work in fiesty etc etc.

---

