---
title: "Desktop Effects Could Not Be Enabled (already searched)"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by akamigs on 2009-07-07
ubuntu 9.04
had everything working perfectly a week ago until ubuntu ran some stupid "Update Manager". 

Compaq Presario F761US Notebook:
1.9GHz AMD Athlon 64 X2 Dual-Core TK-57
nVIDIA GeForce 7000M

still fairly new to linux but I have searched and tried:

'lspci':
```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

'compiz':
```
/usr/bin/compiz: line 1: Script: command not found
/usr/bin/compiz: line 2: ]0: command not found
/usr/bin/compiz: line 2: root@BS:: command not found
/usr/bin/compiz: line 3: ]0: command not found
/usr/bin/compiz: line 3: root@BS:: command not found
: command not foundne 4: exit
/usr/bin/compiz: line 6: Script: command not found

```

'gedit /usr/bin/compiz'
the opened file gave me this:

Script started on Tue 07 Jul 2009 05:27:00 PM EDT
]0;root@BS: ~root@BS:~# sudo gedt[Kit /usr/bin/compiz

]0;root@BS: ~root@BS:~# exit

exit


Script done on Tue 07 Jul 2009 05:28:13 PM EDT

'SKIP_CHECKS=yes compiz --replace ccp &'
```
[1] 5198
bs@BS:~$ /usr/bin/compiz: line 1: Script: command not found
/usr/bin/compiz: line 2: ]0: command not found
/usr/bin/compiz: line 2: root@BS:: command not found
/usr/bin/compiz: line 3: ]0: command not found
/usr/bin/compiz: line 3: root@BS:: command not found
: command not foundne 4: exit

```

'mkdir -p .config/compiz/; echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager'
```
[1]+  Exit 127                SKIP_CHECKS=yes compiz --replace ccp
```

I've tried using NVIDIA accelerated graphics driver (version 173) and (version 180)[Recommended] and neither improve the situation. 

I read something about reinstalling xserver-xgl via the Synaptic Package Manager yet there is no exact match unless its xserver-glx.

Thanks

---

### Post by Pogeymanz on 2009-07-07
I think Compiz must have gotten messed up somehow. Try reinstalling compiz-core.

---

### Post by akamigs on 2009-07-07
> **Pogeymanz said:**
> I think Compiz must have gotten messed up somehow. Try reinstalling compiz-core.

I just don't understand why it was working until I ran the Update Manager. I'll try reinstalling it.

---

### Post by Pogeymanz on 2009-07-08
I wish I could tell you... Sorry.

Good luck. Post back if that doesn't fix it.

---

### Post by akamigs on 2009-07-08
still no luck

---

### Post by akamigs on 2009-07-08
my new 'compiz' gives me:
```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Software Rasterizer: Segmentation fault
Not present. 
Checking for nVidia: present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

---

### Post by Crafty Kisses on 2009-07-08
Not sure if you have used this yet, but look into [Compiz-Check.]("http://forlong.blogage.de/entries/pages/Compiz-Check")

---

### Post by mc4man on 2009-07-09
While the error message isn't quite what I'd expect it's worth trying this.
run in terminal
```
gconf-editor
```

Go apps -> metacity -> general and see if the line "compositing manager" is enabled. If so **disable** and try compiz/ desktop effects again.

---

### Post by akamigs on 2009-07-09
OKAY, so I reinstalled compiz and now I have no visual after boot up. It boots up, displays the ubuntu logo loading bar, then instead of it displaying the sign on screen it shows nothing (black screen).

---

### Post by akamigs on 2009-07-09
alright, i just reinstalled the entire system and everything works now

---

### Post by Elep.Repu on 2009-07-09
> **akamigs said:**
> alright, i just reinstalled the entire system and everything works now
lol. That's incredible that it had to come to that.
I'm sorry to hear it.

---

