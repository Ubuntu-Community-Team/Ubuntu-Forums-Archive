---
title: "Change monitor resolution"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by PDA1 on 2009-11-26
I can't get my monitor (Proview) to show any resolution over 800 x something or another.

I want to go higher.

The system > Preferences>monitor doesn't change anything.

What do I do?

---

### Post by Jon Monreal on 2009-11-26
You may not have the proper drivers installed for your video card. Could you go to a terminal (Applications -> Accessories -> Terminal), type "lspci" (minus the quotes) and press enter. Find the line that says "VGA compatible controller", and post what it says here? Thanks.

---

### Post by PDA1 on 2009-11-26
Here's what I've got.....


kids@kids-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
04:09.0 Modem: Motorola SM56 Data Fax Modem (rev 04

---

### Post by Jon Monreal on 2009-11-26
Try going to System -> Administration -> Hardware Drivers. Under that, you should see drivers with "NVIDIA" at the beginning of their name. Click on the one that says [Recommended] at the end. In the bottom right hand side, there should be a button above the close button that says "Activate"; click this button.

Be aware that this will install proprietary drivers for your graphics card.

---

### Post by MaxIBoy on 2009-11-26
Basically, if you don't mind installing closed-source proprietary software which doesn't respect your freedoms, the most functional drivers can be installed via Jon's method. It's a philosophical descision.

---

### Post by PDA1 on 2009-11-26
> **Jon Monreal said:**
> Try going to System -> Administration -> Hardware Drivers. Under that, you should see drivers with "NVIDIA" at the beginning of their name. Click on the one that says [Recommended] at the end. In the bottom right hand side, there should be a button above the close button that says "Activate"; click this button.

Be aware that this will install proprietary drivers for your graphics card.



Messed up!!!!

When I rebooted the computer it said- Mode Not Supported (or something like that)

Now, I can't see anything on the screen at all!

What do I do now?

---

### Post by Jon Monreal on 2009-11-26
Reboot your computer. When it says "Press 'ESC' to enter the menu...", do so. Go down to the option that says "(recovery mode)". Let recovery mode load, and then when you get a list of options select "Drop to root shell". Type into the shell "sudo dpkg-reconfigure xserver-xorg" (minus the quotes) and press enter. Try following [this guide]("http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure"). If you need additional help, you can always post here.

---

### Post by clanky on 2009-11-26
> **MaxIBoy said:**
> Basically, if you don't mind installing closed-source proprietary software which doesn't respect your freedoms, the most functional drivers can be installed via Jon's method. It's a philosophical descision.

What's philosophical about it driver A works, driver B doesn't work, but the free software foundation will approve of my choice.

FFS it's not like proprietary drivers were developed by Hitler in order to eradicate half of humanity.

---

