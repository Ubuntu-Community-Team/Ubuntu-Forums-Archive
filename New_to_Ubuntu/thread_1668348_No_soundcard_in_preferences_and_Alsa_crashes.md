---
title: "No soundcard in preferences and Alsa crashes"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by cheapodonuts on 2011-01-16
This is certainly my fault for clicking on buttons and not making a note of what I did. But I was expecting to be able to go back if something didn't work out.
I've been trying to use AMSynth (unsuccessfully) over the last couple of days and have not lost all sound. When I check the sound control properties, there is no hardware visible. And if I try to use Alsamixer, it crashes when I click one 'properties'.


My PC knows the sound card is there, apparently, so what did I do wrong! DOH! :o

cheapo@cheapo-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
cheapo@cheapo-desktop:~$ 

Thanx in advance for any help guys.

Pete.

---

### Post by tryten on 2011-01-16
Hi Pete!
My sound card was lost too. Couldn't find it anywhere. I have ubuntu 10.10 and I heard that a lot of people have problems with alsa in maverick. But now it's working again!! I'm no expert at all, but here is what I did:

 I updated alsa-driver from this ppa: [https://launchpad.net/~ricotz/+archive/unstable]("https://launchpad.net/%7Ericotz/+archive/unstable"). I read somewhere that alsa-driver v 1.0.22 is buggy, and even some builds of 1.0.23. Anyway, the sound didn't come back after that. I remembered that i upgraded the kernel before the sound problem. So I downgraded linux-headers and linux-image to version 2.6.35-24 and purged the 2.6.35-25 packages. I rebooted and guess what, still no sound!
In desperation:  ```
sudo alsa force-reload
```And now - music is coming from my speakers!

Hope I could help u!
//Simon

---

### Post by tryten on 2011-01-17
This is crazy, my old computer was totally silent to day again. Lucky for me, I found a REALLY good guide to fix it, u should try it: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
 
My problems was gone in 5 minutes. So ignore my last post and follow the link.
Regards //Simon

---

