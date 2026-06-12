---
title: "Laptop HDMI Out to TV"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by trentscott on 2010-07-16
I have an HP Pavilion dm3 netbook and I'd like to use its HDMI port to send video out to my TV screen. Unfortunately, when I plug the cable in and press Ctrl + F4 (the command to change output screens), nothing happens.

I know the other Ctrl functions work (volume, display brightness, hibernate, etc.), but this one doesn't seem to do anything. I also have only one monitor showing up under Preferences > Monitors (although that may be normal). Does anyone have an ideas as to how I can get this working?

Thanks in advance.

---

### Post by sandyd on 2010-07-16
what video card do you have?

---

### Post by trentscott on 2010-07-16
AMD Vision ____ (something). Is there a command I can run in terminal to figure it out?

---

### Post by rtlustyo on 2010-07-17
Make sure you have at least the proprietary ATI/AMD driver installed by going to System > Administration > Hardware Drivers. 

If you don't just google ATI drivers for Ubuntu. 

Then go to System > Preferences > ATI Catalyst Control Center  (Administrative), then to Display Manager. You should be able to  configure the HDMI display there, just make sure the cable is plugged in  and the TV is turn on so it receives the signal.

---

### Post by Mark Phelps on 2010-07-17
> **trentscott said:**
> AMD Vision ____ (something). Is there a command I can run in terminal to figure it out?

Yes ... lspci.  Look for a line containing VGA.

Also, don't just go downloading and installing ATI drivers.  If your card is not one of the newer HD 3x/4x/5x series, forcing the install of ATI drivers will trash your display.

---

### Post by trentscott on 2010-07-18
I installed the AMD driver from System > Administration > Hardware Drivers and did a full system reboot, things seem to work fine but still no HDMI. Looks like the TV picked up a signal because other inputs (e.g. VCR, DVD, etc.) say "No signal" but I only get a black screen on the HDMI input (on the TV). Here's the output of lspci:

```
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```

Any other thoughts?

---

### Post by rtlustyo on 2010-07-19
Great! You're so close. I just tested this myself so hopefully it works for you. Now that you have a working driver go to System > Preferences > ATI Catalyst Control Center (Administrative). In the Control Center on the left hand side under Pages, you will see  Display Manager, if you click on it you will see the displays that are currently hooked up to your computer. If the HDMI is recognized then you will be able to click on it, and in the tab underneath you will be able to enable the output as a Multi-Display or something else. 

Alternatively you should be able to go to System > Preferences > Monitors, and configure the display there.

---

