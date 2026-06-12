---
title: "[SOLVED] Ubuntu can't find/use my card."
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by DOS4dinner on 2008-07-02
Today, I finally installed Ubuntu onto my windows XP machine. The installation went flawlessly. However, Ubuntu cannot seem to find my wireless card (MSI PC60G). Someone on the wiki said it works, but I have no clue how to get it running. I do have the driver CD handy. Also, I tried the lspci -v | less code and it did not appear there at all. Any ideas?

UPDATE: Problem solved. I just failed to notice the "connect computers" in the corner of the screen. Feel free to post Facepalm pictures.

---

### Post by pytheas22 on 2008-07-02
> I tried the lspci -v | less code and it did not appear there at all

That's strange (unless the card is USB, in which case it wouldn't appear in lspci; use lsusb instead).  What does the command:
```

lshw -C Network
```

tell you?  If possible, copy and paste the output from that command here, but if it's hard to do that (because you don't have any Internet connection on Ubuntu), please at least tell me if you see any mention of the word "wireless" in the output of that command.

---

### Post by DOS4dinner on 2008-07-02
Tried the command. Thanks to the power of pen and paper, here is the output:

Description: Wireless Interface
Product: RT2561/RT61 802.11g PCI
Vendor: RaLink
Physical ID: 1
bus info: pci@0000:02:01.0
Logical name: wmaster0
Version: 00
Serial: 00:1d:92:11:38:fc
Width: 32 bits
clock: 33 MHz
Capabilities: pm bus_master cap_list logical Ethernet physical wireless
Configuration: Broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g

Past this it mentioned ethernet port stuff. Now, it says RaLink but mine is an MSI...maybe they made eachothers cards or something.

---

### Post by Famicommander on 2008-07-02
What exactly have you tried to get it working?

---

### Post by DOS4dinner on 2008-07-03
> **Famicommander said:**
> What exactly have you tried to get it working?

I have not tried that much, but I pretty much did what the GUI has to offer. I tried that hardware test thing. All it said was that I was not connected to the internet with no real information. I could have missed something massive though. I did not try turning it off roaming mode and entering in the data of the router I am connecting to. Do I need to do this? In windows, the router came with a program that went out and found routers it could connect to. Is there a "use this to setup your card" screen I am missing? 

Also, when it does "just work", what happens? Does ubuntu find your card and just make it work like magic?

---

### Post by Famicommander on 2008-07-03
When it does find your card, yeah, it is relatively easy.

---

### Post by Famicommander on 2008-07-03
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsMsi](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsMsi)

It worked out of the box for Gutsy Gibbon. I wonder what went wrong in the transition to Hardy...

---

### Post by DOS4dinner on 2008-07-03
Nevermind. It works perfectly, I am just an idiot for not noticing the computers in the corner that connect to the internet. Where is a facepalm smiley?

---

