---
title: "Sound stopped working help?? Im a newbie!"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by jrozo17 on 2009-12-21
Ok well I currently have Ubuntu 9.10 on my computer, and thought my sister would like it on her laptop. So I installed Karmic Koala on it and everything seemed to be working.. the sound, the internet, everything. Then I went to the Update Manager to see what updates there were. I installed everything and rebooted the laptop.

When Ubuntu started up, there was no log in sound at all. Then I checked the Sound Preferences, and went to Hardware there was nothing there. Nothing in Output or Input either. All it says is that im using the "Dummy ouput".

Why would they release an update that can do that? Does anyone know how to get the sound back??? If I'm gonna have to type in the Terminal please be very basic and walk me through. 

Any help is greatly appreciated so PLEASE HELP ME :(

---

### Post by nerdy_kid on 2009-12-21
please post output of

```

lspci -vvk

```

also, whats the laptop model?

thnks

---

### Post by jrozo17 on 2009-12-21
> **nerdy_kid said:**
> please post output of

```

lspci -vvk

```also, whats the laptop model?

thnks



ok heres what the code I typed in showed me:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Subsystem: Gateway 2000 Device 0281
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Gateway 2000 Device 0281
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at d8100000 (32-bit, non-prefetchable) [size=512K]
    Region 1: I/O ports at 1800 [size=8]
    Region 2: Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Region 3: Memory at d8200000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Gateway 2000 Device 0281
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at d8180000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Gateway 2000 Device 0281
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 22
    Region 0: Memory at d8240000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d4000000-d5ffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d6000000-d7ffffff
    Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Gateway 2000 Device 0281
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 4: I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Gateway 2000 Device 0281
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 4: I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Gateway 2000 Device 0281
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 4: I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Gateway 2000 Device 0281
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin D routed to IRQ 16
    Region 4: I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Gateway 2000 Device 0281
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 0: Memory at d8444000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=04, subordinate=08, sec-latency=32
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: d8000000-d80fffff
    Prefetchable memory behind bridge: 0000000040000000-0000000043ffffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Gateway 2000 Device 0281
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Gateway 2000 Device 0281
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at 1810 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01)
    Subsystem: Gateway 2000 Device 0281
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 26
    Region 0: I/O ports at 18d0 [size=8]
    Region 1: I/O ports at 18c4 [size=4]
    Region 2: I/O ports at 18c8 [size=8]
    Region 3: I/O ports at 18c0 [size=4]
    Region 4: I/O ports at 18b0 [size=16]
    Region 5: Memory at d8444400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
    Subsystem: Gateway 2000 Device 0281
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 10
    Region 4: I/O ports at 18e0 [size=32]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
    Subsystem: Gateway 2000 Device 0281
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 27
    Region 0: Memory at d4000000 (32-bit, non-prefetchable) [size=128K]
    Region 2: I/O ports at 2000 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Intel Corporation Device 1000
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 28
    Region 0: Memory at d6000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945

04:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
    Subsystem: Gateway 2000 Device 0281
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 168, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at d8006000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=04, secondary=05, subordinate=08, sec-latency=176
    Memory window 0: 40000000-43fff000 (prefetchable)
    Memory window 1: 44000000-47fff000
    I/O window 0: 00004000-000040ff
    I/O window 1: 00004400-000044ff
    BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

04:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
    Subsystem: Gateway 2000 Device 0281
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (750ns min, 1000ns max)
    Interrupt: pin B routed to IRQ 18
    Region 0: Memory at d8005000 (32-bit, non-prefetchable) [size=2K]
    Region 1: Memory at d8000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

04:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
    Subsystem: Gateway 2000 Device 0281
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (1750ns min, 1000ns max)
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at d8004000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

:confused:


and its a Gateway tablet pc laptop MODEL: CX2724

---

### Post by nerdy_kid on 2009-12-22
ok, i have a VERY similar audio card, and it works great, so you should be in luck :)

please paste output of:
```

sudo less /var/log/apt/term.log

```


then, open the terminal and enter:
```

sudo chmod -x /usr/bin/pulseaudio

```
then reboot.


and if you look in the toolbar for posting, youll see a '#' sign, with that you can make the output of stuff inside scrollbars so it takes less space

---

### Post by Chris Edgell on 2009-12-22
[QUOTE 
and if you look in the toolbar for posting, youll see a '#' sign, with that you can make the output of stuff inside scrollbars so it takes less space[/QUOTE]


How does that work, where is the toolbar for posting?

---

### Post by frogotronic on 2009-12-22
I had this problem and I solved it by adding the Ubuntu Audio PPA repository and then doing an update and then rebooting.


[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa)

- CH

---

### Post by nerdy_kid on 2009-12-22
@Chris see attached :)

---

### Post by jrozo17 on 2009-12-22
> **nerdy_kid said:**
> ok, i have a VERY similar audio card, and it works great, so you should be in luck :)

please paste output of:
```

sudo less /var/log/apt/term.log

```
then, open the terminal and enter:
```

sudo chmod -x /usr/bin/pulseaudio

```then reboot.


and if you look in the toolbar for posting, youll see a '#' sign, with that you can make the output of stuff inside scrollbars so it takes less space


Ok i typed those same exact quotes and rebooted. BUT now theres not even a sound icon on the top righthand corner. Then I went to Preferences> Sound and it says somethin about trying to get it to respond. 

Thanks for the help and all, but i dont think that code was right for me. :(

---

### Post by nerdy_kid on 2009-12-22
yeah i know, but but forgot 'bout the sound icon thing (dont try to fix it yet) -- run ```

alsamixer

```
 and post an screenshot please -- it should look something like this: (attached)

and did you try playing music or something?  

What i had u do was disable pulseaudio, which is the default audio system ubuntu uses.  Your apps should now be trying to access ALSA directly, which will help me pinpoint the issue.

sorry i dont have a more direct way to go about this :(

---

### Post by jrozo17 on 2009-12-22
> **nerdy_kid said:**
> yeah i know, but but forgot 'bout the sound icon thing (dont try to fix it yet) -- run ```

alsamixer

``` and post an screenshot please -- it should look something like this: (attached)

and did you try playing music or something?  

What i had u do was disable pulseaudio, which is the default audio system ubuntu uses.  Your apps should now be trying to access ALSA directly, which will help me pinpoint the issue.

sorry i dont have a more direct way to go about this :(


Wow the sound is working! :P Sweet. Heres a screenshot of what it opened.

Now all i need is the icon thing, if that isnt too much work. Your a pro man.

---

### Post by nerdy_kid on 2009-12-22
LOL thanks
```

sudo chmod +x /usr/bin/pulseaudio

```

then reboot and test sound again, if it works, then good luck!  If not, then rerun

```

sudo chmod -x /usr/bin/pulseaudio

```

and you can use the sound until i'll help out more then

---

### Post by jrozo17 on 2009-12-23
> **nerdy_kid said:**
> LOL thanks
```

sudo chmod +x /usr/bin/pulseaudio

```then reboot and test sound again, if it works, then good luck!  If not, then rerun

```

sudo chmod -x /usr/bin/pulseaudio

```and you can use the sound until i'll help out more then


Well the icon came back :) but it doesnt control whether the sound goes up or down, and it says dummy output yet again.

The sound that does come out, is a verrry low pitch and it can only be turned up barely from the terminal code you gave me.

I mustve done somethin wrong or maybe its just the laptop.. who knows :confused: so if your clueless on what to tell me now then its no prob. You did help me alot and im very appreciative. :biggrin:

---

### Post by bodhi.zazen on 2009-12-23
Several great suggestions in this thread :

[http://ubuntuforums.org/showthread.php?t=1308550](http://ubuntuforums.org/showthread.php?t=1308550)

If you have no sound devices (dummy output) => reboot

---

### Post by nerdy_kid on 2009-12-23
> **bodhi.zazen said:**
> Several great suggestions in this thread :

[http://ubuntuforums.org/showthread.php?t=1308550](http://ubuntuforums.org/showthread.php?t=1308550)

If you have no sound devices (dummy output) => reboot

thanks, very useful :)

---

### Post by nerdy_kid on 2009-12-23
you need to adjust both sliders in ALSA mixer, if you hit the right arrow then you can turn the other one up also.....keep messing with the slider and you should be able to get a nice volume.


for the other issue:  i got this from the thread bodhi.zazen posted.

```

Originally Posted by garvinrick4  
Did 3 installs or upgrades to 9.10 and this worked each time. 9.10 Just have to do
Part A. Just follow instructions. Reboot when done. 

sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio


Part A: Common instructions (Hardy, Intrepid, Jaunty & Karmic)
All users must must follow the steps in this section to guarantee a fully working PulseAudio configuration.
9.10
1. Backup (and then delete) your previous configuration files:
Code:

$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
$ rm -r ~/.pulse ~/.asound* 
$ sudo rm /etc/asound.conf

Warning: As always, use caution when removing files on your system. Any typos can potentially cause data loss.
Note: Don't worry if some of these files did not exist on your system.


2. Ensure you have the necessary PulseAudio libraries and configuration utilities installed:
Code:

$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio

3. Ensure the evil "libflashsupport" library is not installed:
Code:

$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound

Note: the libflashsupport library was (and to a certain extent, still is) the most common cause of Firefox instability since the Hardy release, because many users have been misled into thinking they must install it to ensure Flash & PulseAudio can work correctly. If you notice any postings that recommend this library to be installed, please reply to the post and point them to this thread, or the bug report linked. The more people that are aware of this issue the better. Thanks!

5. Open the PulseAudio Volume Control application ("pavucontrol"). In the Output Devices section you will see a listing of the playback devices available on your system. Right-click on the entry that you desire to be made the default playback device on your system and enable the "Default" checkmark. Similarly, navigate to Input Devices, then right-click on the device you wish to set as your default input device (microphone), and ensure the "Default" setting is checked. Close the application when you're finished.

Note: If you are greeted with the error "Connection failed: Connection refused", manually launch PulseAudio before opening the PulseAudio Volume Control application:
Code:

$ pulseaudio & pavucontrol

6. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a common bug in Intrepid and Jaunty):

Code:

$ alsamixer -Dhw

7. you're finished - log out and back in for changes to take effect!
__________________



```
i have edited his instuctions a little

attached i show you the slider you need to move up for big volume (not pitch hahaha)

---

### Post by nerdy_kid on 2009-12-23
your sound *shall* work by the time you leave the forums!

---

### Post by bodhi.zazen on 2009-12-23
glad it is working =)

---

### Post by jrozo17 on 2009-12-24
> **nerdy_kid said:**
> your sound *shall* work by the time you leave the forums!


Your so optimistic! :lolflag:


Ok so I followed the instructions you gave me and typed in the first code it told me.. that went ok (i think), at least it looked like it was processing something. Then i tried the next code and it says command not found. So i tried all the other codes and it says the same thing.. help? i rebooted and its not any differant.


I feel like such a noob but i honestly dont know what im doin wrong! if only u could just hack into my computer and do it for me haha

---

### Post by nerdy_kid on 2009-12-24
> **jrozo17 said:**
> Your so optimistic! :lolflag:


Ok so I followed the instructions you gave me and typed in the first code it told me.. that went ok (i think), at least it looked like it was processing something. Then i tried the next code and it says command not found. So i tried all the other codes and it says the same thing.. help? i rebooted and its not any differant.


I feel like such a noob but i honestly dont know what im doin wrong! if only u could just hack into my computer and do it for me haha
:lolflag:
copy and paste the commands -- they work for me


and then run
```

sudo apt-get update && sudo apt-get upgrade && sudo update-grub
sudo alsa force-reload
sudo apt-get remove sl-modem-daemon

```
and reboot


[edit]

and did you raise the other slider in alsamixer?

---

### Post by jrozo17 on 2009-12-24
> **nerdy_kid said:**
> :lolflag:
copy and paste the commands -- they work for me


and then run
```

sudo apt-get update && sudo apt-get upgrade && sudo update-grub
sudo alsa force-reload
sudo apt-get remove sl-modem-daemon

```and reboot


[edit]

and did you raise the other slider in alsamixer?



Omg dude you rock!! Everything is working perfectly, I didnt think it would actualy fix the problem. I wish there was someway i could repay u cuz i wouldnt have done it without u.

Again, thanks for taking your time with helping me. :)

Your a genious!!!

---

