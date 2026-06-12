---
title: "BCM 4352 bluetooth not recognized"
date: 2014-01-05
forum: Networking &amp; Wireless
---

### Post by vortexmak on 2014-01-05
Hi, 

I have an Azurewave card using a BCM 4352 chip  [http://wikidevi.com/wiki/AzureWave_AW-CE123H](http://wikidevi.com/wiki/AzureWave_AW-CE123H) with onboard bluetooth
Wifi is working fine fine on it but no bluetooth devices are detected.
Can someone please help.

Helpful commands:

lshw -C network
```
  *-network               
       description: Ethernet interface
       product: Ethernet Connection I217-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: bc:5f:f4:cd:05:aa
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:f0100000-f011ffff memory:f0139000-f0139fff ioport:f040(size=32)
  *-network
       description: Wireless interface
       product: BCM4352 802.11ac Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 24:0a:64:b0:a3:f1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.141 (r415941) ip=192.168.0.21 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:19 memory:f0400000-f0407fff memory:f0200000-f03fffff


```

sudo lspci -vvv

```
03:00.0 Network controller: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter (rev 03)
    Subsystem: AzureWave Device 2123
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at f0400000 (64-bit, non-prefetchable) [size=32K]
    Region 2: Memory at f0200000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: [48] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=2 PME-
    Capabilities: [58] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [68] Vendor Specific Information: Len=44 <?>
    Capabilities: [ac] Express (v2) Endpoint, MSI 00
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr+ NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 1024 bytes
        DevSta:    CorrErr- UncorrErr+ FatalErr- UnsuppReq- AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 5GT/s, Width x1, ASPM L0s L1, Latency L0 <2us, L1 <32us
            ClockPM+ Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Range ABCD, TimeoutDis+
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
        LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
             EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt+ UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 0f, GenCap+ CGenEn- ChkCap+ ChkEn-
    Capabilities: [13c v1] Device Serial Number 24-0a-00-ff-ff-00-00-01
    Capabilities: [150 v1] Power Budgeting <?>
    Capabilities: [160 v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed- WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=01
            Status:    NegoPending- InProgress-
    Capabilities: [1b0 v1] Latency Tolerance Reporting
        Max snoop latency: 71680ns
        Max no snoop latency: 71680ns
    Capabilities: [220 v1] #15
    Kernel driver in use: wl


```

hcitool dev
```

Devices:

```

rfkill list
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by philip550c2 on 2014-01-15
I have the same issue in my new asus laptop. What version of ubuntu are you using? Im on 13.10 but from digging around the net it seems it might work on the older drivers available in the older distros before 12.10 but i am unable to boot 12.04 on my laptop to confirm.

---

### Post by vortexmak on 2014-01-18
> **philip550c2 said:**
> I have the same issue in my new asus laptop. What version of ubuntu are you using? Im on 13.10 but from digging around the net it seems it might work on the older drivers available in the older distros before 12.10 but i am unable to boot 12.04 on my laptop to confirm.

Which laptop do you have ? Do you have the same BCM4352 chip ? I am using Ubuntu 'Saucy' 13.10.
I booted the older version as well, still does not work. In fact, the Wifi works on the never version but I was only able to get Wifi to work after a lot of tinkering.

I would like to know the the historical support that BCM chips get. I am willing to wait, if the support can be added.

---

### Post by praseodym on 2014-01-19
Did you install:

```
sudo apt-get install bluez-utils libopenobex1 gnome-bluetooth 
sudo service bluetooth restart 
lsusb | grep Bluetooth 
hciconfig --all 

```

---

### Post by maxbar on 2014-01-21
I have the same issue - in quick search, I type in "blue" and "bluetooth" shows up, which I open and everything is grayed out, even after I follow above instructions.
"lsusb | grep Bluetooth" and "hciconfig --all" both return nothing (no output at all).

I noticed that the updated showed up, after I executed the first one or first two lines (apt-get... and service bluetooth...) - coincidence perhaps? I closed it down with "remind me later", and the updates listed were "Ubuntu base" under both security and other updates...

Haven't rebooted yet, will do that (after the update) and will see if "bluetooth" app will still have grayed out toggles and such - and I will report if working or not.

Hardware:
Asus ROG Maximus VI Formula w/ supplied mPCIe Combo II (Wi-Fi 802.11ac and Bluetooth 4.0)
Latest Bios update

---

### Post by maxbar on 2014-01-21
The update needed me to restart anyhow, so I did that... I ran the bluetooth app again, still everything is grayed out (Bluetooth = off, Visibility = off, "no bluetooth adapters found" and the + and - are both grayed out, so I can't even add an adapter there) :(

I executed the last two lines again, and still no output at all...

---

### Post by maxbar on 2014-01-21
Btw I use also 13.10 - and during install, I selected "additional drivers" or something, so I'd get internet. I did some search and found out that it's a proprietary driver, also that supposedly it's been noted that it would sporadically disconnect WiFi and it has been described as "crap" lol...

Interestingly, doing a "modprobe -c | grep bcm" I get "blacklist bcm43xx" - that doesn't sound very good? But perhaps that's so the kernel provided driver won't conflict with the proprietary driver. I don't care really which one to use, as long as I have WiFi and bluetooth both working correctly.

---

### Post by vortexmak on 2014-01-22
> **praseodym said:**
> Did you install:

```

*sudo apt-get install bluez-utils libopenobex1 gnome-bluetooth *

gnome-bluetooth is already the newest version.
libopenobex1 is already the newest version.
The following extra packages will be installed:
  bluetooth
The following NEW packages will be installed:
  bluetooth bluez-utils



*sudo service bluetooth restart *

bluetooth stop/waiting
bluetooth start/running, process 2896

*lsusb | grep Bluetooth *

<nothing>
Note that the Bluetooth is integrated into the wifi card and is not a separate USB dongle

*hciconfig --all*

<nothing>

```

---

### Post by vortexmak on 2014-01-22
> **maxbar said:**
> Btw I use also 13.10 - and during install, I selected "additional drivers" or something, so I'd get internet. I did some search and found out that it's a proprietary driver, also that supposedly it's been noted that it would sporadically disconnect WiFi and it has been described as "crap" lol...

Interestingly, doing a "modprobe -c | grep bcm" I get "blacklist bcm43xx" - that doesn't sound very good? But perhaps that's so the kernel provided driver won't conflict with the proprietary driver. I don't care really which one to use, as long as I have WiFi and bluetooth both working correctly.

Wifi works with 13.10, it uses the driver 'wl' automatically, if you enable proprietary drivers. Wifi works just okay, takes a long time to connect after resume though.
If you run 'lspci -vv' , you should be able to see the Network Controller with the last line listing the kernel driver that is in use

It is the bluetooth module that is not being detected at all. I hate redundancy that's why i don't want to get an external bluetooth dongle.

---

### Post by maxbar on 2014-01-23
> **vortexmak said:**
> Wifi works with 13.10, it uses the driver 'wl' automatically, if you enable proprietary drivers. Wifi works just okay, takes a long time to connect after resume though.
If you run 'lspci -vv' , you should be able to see the Network Controller with the last line listing the kernel driver that is in use

It is the bluetooth module that is not being detected at all. I hate redundancy that's why i don't want to get an external bluetooth dongle.

Not sure why you wrote this with a quote of what I've wrote before, I know it's the "bluetooth module" (which is officially called - copy-pasted from the Asus product page: "mPCIe Combo II with 802.11ac/Bluetooth 4.0") because that's the one I'm having too (on the Formula) and I'm having the same problem. I actually do have a USB bluetooth dongle laying around (completely forgot about that) and might use it in the meantime, but, like you, I would prefer redundancy and not having to use it.

---

### Post by maxbar on 2014-01-23
Although this doesn't have anything to do with the BCM4352, but I thought I'd mention it in here anyhow - so apologies if this is semi-off-topic, but it's bluetooth related and perhaps of interest once the BCM 4352 as such is installed correctly:

(note: the first few steps did not work for me, but I thought of mentioning them, for documenting purpose!)

1. So I decided to plug in my spare bluetooth USB dongle, and a second later, the bluetooth symbol showed up in the status bar (or whatever it's called, top-right on the screen, next to the clock and other stuff there).

2. Clicking on it and selecting "Set up new device", brings up the bluetooth setup wizard (not sure exactly what it's called) and turning on my bluetooth mouse (Apple Magic Mouse) and then selecting search, finds it.

3. I selected "connect" (or similar, don't remember exactly) and a new window popped up saying that the process is finishing up, with a clickable "quit" button - which I did not press at that point, instead I patiently waited and after about 15 to 20 seconds, I got the message that connection was successful, and then I selected the "quit" button, still using my non-bluetooth mouse.

4. Now moving my bluetooth mouse around... mouse cursor doesn't move! The mouse shows up in the list within the bluetooth wizard, it says it's connected yet it is not paired. So I removed it and selected the options and after some research I found out to manually set the pairing code to "0000" -> same procedure, same ~20 seconds waiting time for completion of connection, however, again no success :(

5. So after some more searching, I came across a post suggesting to not use that wizard but instead to use one called "bluetooth manager" AKA "blueman", which to be found in the software center. Which I looked up there and indeed it showed in the list and as uninstalled, so I installed that one.

6. I made sure that in the previously - built-in bluetooth wizard - app, I had removed my mouse, deselected "discoverable" and closed it.

7. Then I started up "bluetooth manager", turned off and back on my mouse, selecting "search" and it showed up in the list, then adding it via the plus sign... again, moving the mouse around would not move the mouse cursor.

8. So I right-clicked, using my non-bluetooth mouse, selected "pair" and a window popped up asking for the pin, I entered "0000" and not sure if there was a status message about he pairing, I think not and moving the mouse still wouldn't move the mouse cursor.

9. Right-clicking on the device in the list again, I selected "Input device", moved the bluetooth mouse around and indeed, the cursor would finally move!

10. I also have a bluetooth keyboard (Logitech K810 with custom-applied silicone protector, much improved feel of typing that way, instead of the slippery keys) and I followed the above, although this time I selected "Input device" immediately instead of "pair", and interestingly enough I was not asked to put in a security code like it had me do when I had selected "pair" for the mouse or as it is done when pairing the keyboard in Windows or with my Android phone and tablet... weird, but I don't complain, one less step and also it works!

I hope this is will be helpful once there's a solution to get the BCM 4352 up'n running... but for now I'm satisfied with my current solution. Btw, the USB bluetooth dongle that I'm using is "Medialink model no. MUA-BA3 Class 2 Bluetooth 4.0". I also have bluetooth earbuds but I haven't tried connecting those yet, so no idea if A2DP does work too, but I imagine it probably will.

Again, sorry for this somewhat off-topic reply, I am still wanting to get the BCM4352 working, but once it does I know for sure that I'll try connecting my bluetooth devices using "blueman" first and only if that fails then using the integrated bluetooth wizard.

---

### Post by smidgley792 on 2014-10-16
Hello all, I'm having a hard time with my Lenovo Y510p laptop + Broadcom 4352 combo card. WiFi works but no BT. Blueman solution did not work for me, it just shows a blank list. tried "sudo rfkill unblock bluetooth" even though it had so blocks. I even re installed the proprietary Broadcom driver. I am an extreme novice to Linux based systems and could sure use all the help I can get.

---

### Post by praseodym on 2014-10-17
Hi,
please show the terminal outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
lsusb
lsmod
rfkill list
dmesg | grep Blue
```

---

### Post by GlenH on 2014-11-24
The Bluetooth component of the Azurewave AW-CE123H combo 802.11ac WiFi/Bluetooth module is a Broadcom BCM20702A0 device, and answers are found searching for it. There are two issues; getting the Bluetooth driver to recognize the card, and loading new firmware into it. I was able to get mine working through the following two steps.  

1. Add the vendor and product IDs to the Bluetooth driver in the kernel.  This is covered here [http://ubuntuforums.org/showthread.php?t=2231813](http://ubuntuforums.org/showthread.php?t=2231813), but my solution uses the existing support in the Bluetooth driver for patchram, rather than the homegrown Python script discussed in that thread.
  a. Download the Linux kernel 
  b. Edit drivers/bluetooth/btusb.c to add the following entry in the Broadcom BCM20702A0 section.
   ```
 { USB_DEVICE(0x13d3, 0x3404), .driver_info = BTUSB_BCM_PATCHRAM },
```
  c. Rebuild the kernel.

2. Find the patchram hex file used by Windows for this card.  In my case, it was BCM20702A1_001.002.014.1159.1175.hex.  The Broadcom firmware loader needs this to be in .hcd format and with a name that matches the PID and VID.  Jesse Sung wrote a small utility called hex2hcd that converts the hex file supplied with the Windows driver into the hcd file. Here are the steps to install the firmware file in the correct place:

```
git clone git://github.com/jessesung/hex2hcd.git
cd hex2hcd
make
./hex2hcd BCM20702A1_001.002.014.1159.1175.hex fw-13d3_3404.hcd
sudo cp fw-13d3_3404.hcd /lib/firmware/
```

The card works after a reboot.

---

