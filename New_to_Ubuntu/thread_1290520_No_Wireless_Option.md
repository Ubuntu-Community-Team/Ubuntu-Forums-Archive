---
title: "No Wireless Option"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by Amockineuropa on 2009-10-13
I have Ubuntu with Windows dual boot. My internet works fine while in Windows and I have internet (via ethernet) while in Ubuntu. However I do not have a wireless option (ie Enable Wireless) when I right click on Network Mgr. How do I install the Wireless option so I can use my laptop via wireless. I have a Atheros PCI Wireless (168c:002b). Yes! I researched this via this site/google but to no avail.

---

### Post by sandyd on 2009-10-13
can you post the output of these commands ? 
between ```
 tags i mean 

[code]
lspci

```
```

lshw -c Network

```
```

iwconfig

```

---

### Post by Amockineuropa on 2009-10-13
I recognize you so first thanks for helping. Besides I luv Toronto. How do I save the data I find on Terminal and then post it here?

---

### Post by nothingspecial on 2009-10-13
Just copy and paste.

---

### Post by Amockineuropa on 2009-10-13
Hope this works:
 
amockineuropa@amockineuropa-laptop:~$ lspci


00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge


00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)


00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)


00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)


00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]


00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller


00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller


00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller


00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)


00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)


00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller


00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge


00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration


00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map


00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller


00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control


01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]


02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)


08:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)


amockineuropa@amockineuropa-laptop:~$ lshw -c Network


WARNING: you should run this program as super-user.


*-network UNCLAIMED 


description: Network controller


product: AR9285 Wireless Network Adapter (PCI-Express)


vendor: Atheros Communications Inc.


physical id: 0


bus info: pci@0000:02:00.0


version: 01


width: 64 bits

---

### Post by Amockineuropa on 2009-10-13
Well LINUX was wrong!

---

### Post by nothingspecial on 2009-10-13
If you have a wired connection try

```
sudo apt-get update && sudo apt-get install linux-backports-modules-jaunty
```

---

### Post by nothingspecial on 2009-10-13
> **Amockineuropa said:**
> Well LINUX was wrong!

That`s just my sig.

I read it in my early days of using linux and it`s worth remembering.

If you do stuff (especially as root) then linux _**will**_ do it - it won`t ask you if you`re sure .......

And after you`ve done it, there`s no undo (or whatever), it`s done.

That`s the way it works.

---

### Post by Amockineuropa on 2009-10-13
Ok I did that

---

### Post by nothingspecial on 2009-10-13
> **Amockineuropa said:**
> Ok I did that

So did it help?

Try rebooting or 
```

sudo /etc/init.d/networking restart
```

---

### Post by Amockineuropa on 2009-10-13
Worked like a charm. Bless U.

---

### Post by nothingspecial on 2009-10-13
No problem. Night night.  ;)

---

