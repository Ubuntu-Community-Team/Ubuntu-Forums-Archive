---
title: "Problems getting wifi working."
date: 2009-01-31
forum: New to Ubuntu
---

### Post by Mikkeren on 2009-01-31
My network card is Atheros WN6302A but I can't get it working in Ubuntu.
I've tried using the ndiswrapper and used the .inf file from Windows, but that just tells me that "Hardware Present: No"

So i was hoping someone in here, who knew something about it could help me getting the wireless up and running.

---

### Post by shifty_powers on 2009-01-31
have you tried looking at madwifi?

[http://madwifi-project.org/](http://madwifi-project.org/)

---

### Post by nothingspecial on 2009-01-31
Go to system > administration > hardware drivers then disable anything in there.

Then

```
sudo apt-get install linux-backports-modules-intrepid-generic
```

To load the driver

```
sudo modprobe ath5k
```

To make it load everytime you boot

```
gksudo gedit /etc/modules
```

and add

```
ath5k
```

To the end of the file

save
close
reboot

---

### Post by Mikkeren on 2009-01-31
> **shifty_powers said:**
> have you tried looking at madwifi?

[http://madwifi-project.org/](http://madwifi-project.org/)

I had not, but as far as I can see it requires me to be able to actually have a device shown in ifconfig for my wlan connection already?
Not even lspci shows the card =/

---

### Post by Mikkeren on 2009-01-31
> **nothingspecial said:**
> Go to system > administration > hardware drivers then disable anything in there.

Then

```
sudo apt-get install linux-backports-modules-intrepid-generic
```

To load the driver

```
sudo modprobe ath5k
```

To make it load everytime you boot

```
gksudo gedit /etc/modules
```

and add

```
ath5k
```

To the end of the file

save
close
reboot

Doesn't seem to change anything. Still no wlan

---

### Post by WinterMadness on 2009-01-31
1. MAKE SURE you're installing the Windows XP driver, NOT vista's.
2. The absolute easiest way is to go into synaptic and search for "ndisgtk" that is Ndiswrappers graphical user interface. Much better than the terminal right?
3.After you install the correct driver, click the network manager icon in the notification area (as a windows user, you might know it as the system tray) and youll have a list of wifi networks.

I often find that people rarely give you the obvious answers here, and when people install ubuntu thats what theyre looking.

---

### Post by Mikkeren on 2009-01-31
> **WinterMadness said:**
> 1. MAKE SURE you're installing the Windows XP driver, NOT vista's.
2. The absolute easiest way is to go into synaptic and search for "ndisgtk" that is Ndiswrappers graphical user interface. Much better than the terminal right?
3.After you install the correct driver, click the network manager icon in the notification area (as a windows user, you might know it as the system tray) and youll have a list of wifi networks.

I often find that people rarely give you the obvious answers here, and when people install ubuntu thats what theyre looking.

It still says "Hardware present: No".

Any ideas why it might be doing that?
Or any ideas why it appears as though i have no wlan network card?

---

### Post by Mikkeren on 2009-01-31
Can anyone help me find out why the Atheros WN6302A doesn't show up through a lspci?

```
mik@lolsuhefaids:~$ lspci
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
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
07:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)

```

---

