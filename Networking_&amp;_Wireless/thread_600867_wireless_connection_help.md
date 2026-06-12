---
title: "wireless connection help"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by lacynaws on 2007-11-02
I have a Compaq Presario laptop with a built in wireless card but can not connect to internet wirelessly. Any suggestions?

---

### Post by Birdman1962 on 2007-11-02
gutsy or feisty?
trying to connect or nothing no networks in range?
wpa or wep security?
mac filtering?
b or g?

---

### Post by name101 on 2008-01-02
Hello everyone this is also the first time i am using Linux :D

gutsy or feisty?
Feisty version 7.04
trying to connect or nothing no networks in range?
Not displaying anynetworks at all. i have set the manager to Roaming. i have tried to manually connect using the SSID broadcast name and the the password
wpa or wep security?
WEP hexidecimal 10char long
mac filtering?
not on the routor
b or g?
both... i hope. im sure it will run both.

the computer specs if needed.
Compaq Presario V3000
2GB Ram
80GB HDD 60 for Vista 10 for Linux and the rest for recovery
6150go Nvidia GFX card.
the wireless card is a Nvidia. something or other sorry im a little new to this and im not too sure where to find the info.. thanks for any help.


~Regards
Name101

---

### Post by The Tronyx on 2008-01-02
> **name101 said:**
> 
the wireless card is a Nvidia. something or other sorry im a little new to this and im not too sure where to find the info.. thanks for any help.


In a terminal type:
> 
sudo lspci | grep nVidia

That should give you more info about your wireless card and make solving this problem easier. :)

---

### Post by name101 on 2008-01-02
thanks for the reply.
i typed the command in and the terminal and did not have any luck

```
sudo: lspi: command not found
```

hrmmm. 
did i type the command wrong?
i did try a few things but i have thrown myself into the deep end and a little lost.

---

### Post by The Tronyx on 2008-01-02
That is not the correct command.  lsp**c**i

sudo lspci | grep nVidia

---

### Post by name101 on 2008-01-02
oops my bad :P

well because nVidia is the gfx card as well ill post the entire script.

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
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
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

im not entirely sure if it is a nVidia W/less card i thought it was... but im not to sure.

---

