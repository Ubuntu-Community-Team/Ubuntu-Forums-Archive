---
title: "Completely new to Ubuntu :("
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by travis712 on 2006-11-26
I need help with something. I tried using the supplied guide on connecting to the internet, but so far I don't have a clue :P.

Heres the deal

I can boot into ubuntu fine; but before I boot I get an error. Something to the extent of that it can't connect to the internet so the GNOME can't function properly. So I go to network, and it says "No network devices found".

I'm running my desktop to a splitter in my room, then the lead from that is coming from the main router in our house. no wireless. What do I need to do? Please, if there is a guide for me, please supply it. Step by step would be wonderful, but any help would be appreciated.

---

### Post by Gannin on 2006-11-26
Do you know what make and model of network adapter you have?

---

### Post by travis712 on 2006-11-26
Sorry for being redudent, should I be looking at my splitter(what my pc is first hooked up to) or the actual router? The router being what the internet first goes to. Please lmk :).

---

### Post by Gannin on 2006-11-26
I'm talking about the thing the network cable plugs into on the computer itself, on the back of the computer.  That's going to be your network adapter.

---

### Post by travis712 on 2006-11-26
Ah, im using onboard lan on my asustek p4sdle.

---

### Post by hal10000 on 2006-11-26
You say before you boot you get an error.
What does the error message print?
After booting ubuntu, open a terminal window and type: [COLOR="Red"]lspci[/COLOR]. YOu will get an outut similar to this one:
```

00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)

```
You should see a line with "Network controller: ...." Post the line or the whole output of the command.

---

### Post by travis712 on 2006-11-26
I'll do this tomorrow, thanks. 

Also, for clarification: I get the error after I boot ubuntu, and after I log in, but before i get to the desktop.

---

### Post by travis712 on 2006-11-28
travis@ubuntuTRAVSROOM:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corp. 82801EB (ICH5) Serial ATA 150 Storage Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 00f1 (rev a2)
0000:02:05.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
0000:02:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:02:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
travis@ubuntuTRAVSROOM:~$

ethernet controller?

---

### Post by travis712 on 2006-11-30
anyone? please?

---

### Post by Gannin on 2006-11-30
When you go to the Networking configuration window, is anything listed there?

---

### Post by travis712 on 2006-12-04
> **Gannin said:**
> When you go to the Networking configuration window, is anything listed there?

No there isn't, when I go to the network tools page it say's 
"Network Devices not found"

---

### Post by travis712 on 2006-12-04
Little off topic question, should this thread be moved into one of the more general subforums here? Noticed this area doesn't get too much traffic, and my questions not exactly complex. I know everyone here knows more about linux then I do, lol. I just need some help, I want ubuntu running :(

---

### Post by hal10000 on 2006-12-13
Your lspci command says that there is an ethernet controller realtek RTl-8139C placed in your system.

Try to search for the kernel module which is the right one for your card. In a terminal window type [COLOR="Red"]lsmod | grep 8139[/COLOR]. If you get an answer, then your kernel module is loaded correctly. If you don't get an answer then try [COLOR="Red"]find /lib/modules/$(uname -r) -name "*8139*.ko"[/COLOR]. You should find an answer like ```
/lib/modules/2.6.17-10-generic/kernel/drivers/net/8139cp.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/net/8139too.ko
``` and maybe some more lines that contain the string 8139. Because I don't have the same network card, I don' know which one is the right for you. So you have to modprobe all of the above. Type [COLOR="Red"]sudo modprobe 8139cp[/COLOR] and [COLOR="Red"]sudo modprobe 8139too[/COLOR] and all other listed from the find-command (note: modprobe works _without_ the pathname and the .ko suffix). Then go to the network configuration window again and configure your network.
If you still don't find a network device, then your card may be damaged. If you have windows running on that computer, try to get a connection under windows. If you have no windows, buy a new network card (or borrow a card from a friend) and try again.

---

### Post by travis712 on 2006-12-18
My network card is perfectly fine.

---

