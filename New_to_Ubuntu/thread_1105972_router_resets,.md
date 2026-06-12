---
title: "router resets,"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by newbie88 on 2009-03-25
Hi folks,

I'm still new to Ubuntu - got this great computer and a friend set me up w/Ubuntu op sys.

But... all kinds of bizarre things are happening - do you think they're related to ubunto op system?

We couldn't establish a connection via wireless router despite wireless capability on computer so have a hardwire to the router.  We  have other computers in the house that connect via wireless connection using Windows XP and IE.

But it seems after I've logged in and done work on the ubuntu system - that the other computers can no longer access via wireless router.  It's been reset.

Does this make sense?  If so, why?

---

### Post by cariboo on 2009-03-25
I would suggest checking ip addresses, as two computers may be trying to use the same ip address.

Jim

---

### Post by halitech on 2009-03-25
> **newbie88 said:**
> Hi folks,

I'm still new to Ubuntu - got this great computer and a friend set me up w/Ubuntu op sys.

But... all kinds of bizarre things are happening - do you think they're related to ubunto op system?

We couldn't establish a connection via wireless router despite wireless capability on computer so have a hardwire to the router.  We  have other computers in the house that connect via wireless connection using Windows XP and IE.

But it seems after I've logged in and done work on the ubuntu system - that the other computers can no longer access via wireless router.  It's been reset.

Does this make sense?  If so, why?

not making a connection with a wireless device at first? sounds entirely possible as very few work out of the box. 

is the computer a desktop or laptop?

post the output of
```
lspci
```and ```
sudo iwconfig
```
should give us an idea what we are dealing with on the hardware side.

like cariboo says, check the IP addresses on both machines (or your router logs) to see if there is a conflict with the IPs.

---

### Post by newbie88 on 2009-03-25
lspci:
00:00.0 Host bridge: nVidia Corporation MCP73 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation Device 07f0 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation GeForce 7100/nForce 630i (rev a2)
01:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
00:00.0 Host bridge: nVidia Corporation MCP73 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation Device 07f0 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation GeForce 7100/nForce 630i (rev a2)
01:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
00:00.0 Host bridge: nVidia Corporation MCP73 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation Device 07f0 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation GeForce 7100/nForce 630i (rev a2)
01:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)

sudo iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


I don't really know about the IP addresses - because of the way things were set up the ip addresses are reassigned regularly so yes, different computers can end up using the same ip address within one day.  But this was the case before ubuntu machine was installed and the router was able to deal with it then...???

What are your thoughts?

---

### Post by halitech on 2009-03-25
first lets cut your info from lspci a little as you have it posted 3 times
```
lspci:
00:00.0 Host bridge: nVidia Corporation MCP73 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation Device 07f0 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation GeForce 7100/nForce 630i (rev a2)
01:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
```

right now I'm thinking I don't see a wireless controller in the list. Are you using a USB wireless adapter or is it one that has builtin wifi?

---

