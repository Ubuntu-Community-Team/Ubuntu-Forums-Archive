---
title: "simple microphone"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by super kim on 2009-10-22
won't work :(

i am using jaunty and i can't get anything from my mic. it is just a standard pc mic, on the up side the headphones work.

i checked the volume was up and i tried every option in the sound options, i don't understand it.

the microphone does work i did check that :) just not with ubuntu.

please help me

---

### Post by martrn on 2009-10-22
> **super kim said:**
> won't work i am using jaunty and i can't get anything from my mic. it is just a standard pc mic, on the up side the headphones work. i checked the volume was up and i tried every option in the sound options, i don't understand it. the microphone does work i did check that :) just not with ubuntu. please help me

Open a terminal and type :-
```
sudo apt-get install alsamixergui
sudo alsamixergui
```

and ensure that all of your mute boxes have been unchecked.

The sound input and output eg microphones and headphones are controlled by the sound card, you may need to add extra options and check that your sound card has full driver support in the advanced linux sound architecture database.

Just check that under system-->preferences-->sound and under the devices tab that alsa is selected as the driver for all sound options, unless your sound card is not supported by the alsa drivers in which case use the bsd/opensoundsystem drivers, and the oss mixer to make sure all sound inp/outp is not muted.

---

### Post by super kim on 2009-10-24
i can't get it to work yet, i tried to use the alsa mixer. still no joy :(

---

### Post by martrn on 2009-10-24
There may not be a full driver available for your input sockets on for you soundcard, but there might be output for you sound card.  I do not know what sound card you have.

Have you tried checking the asla-maxtix and finding your sound card on the alsa drivers.  [www.alsa-project.org/]("http://www.alsa-project.org/main/index.php/Matrix:Main")?  It maybe that you need to add extra quirks to you sound card to work.

Have you tried the [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") page at ubuntu?  Scroll down until you see the section entitled "Getting Line Input to work", and it will give you the instructions on how to alter or manage the pulse audio server to capture sound.

---

### Post by super kim on 2009-11-01
hi, sorry i have been away from the post for a bit,

my sound card is...
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
there are more details about my alsa configuration and hardware [here]("http://www.alsa-project.org/db/?f=c38b36774e10e2764cc12ccc3b52501ff2bf4565")
and [here]("http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/ALSA-Configuration.txt;h=012858d2b11935aa711e4cf9d2d8fbe637403813;hb=fb0641b49488dc7f1aafdcb1631e7bc5aca69cfb") is the documentation for the driver.

but even with all this information i don't understand how to get the mic to work.

i did try [this]("https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20Line%20Input%20to%20work%20%28Microphone,%20etc%29") and at one point i thought i heard my voice through the mic, very quiet and distorted could of been my imagination even.

---

### Post by super kim on 2009-11-11
i am now using karmic koala (9.10) however i still have had no joy with the mic. if anyone can help that would be awesome.

---

### Post by super kim on 2009-12-01
bump

---

### Post by Calmor on 2009-12-01
If I may ask, what are you trying to do with the microphone?  Some machines (such as my HP laptop) simply do not have any hardware mechanism of passing the sound through the microphone to the headphones.  I can record all day long, and then play back, but neither in Ubuntu (9.04, 8.10, 8.04) nor Windows (7 Pro, Vista Home Premium)can I talk and hear the sound come out of the speakers immediately.

It is of course entirely possible to do so via software.

If you open Sound Recorder and try to record your voice (playing with the settings in there), do you have any luck?

Edit:  Hmm, nevermind, if you've already tried all of the things in Getting Line Input to Work, you were checking the recording.  I'm assuming you also tried any other jacks that might be on your soundcard (usually the first thing checked)... hmm... did you look up your specific hardware device for help?  You can run dmesg | grep ICH to get the hardware ID number (xxxx:xxxx) and Google from there, perhaps.

---

### Post by super kim on 2009-12-17
```
dmesg | grep ICH
[    0.093205] pci 0000:00:1f.0: quirk: region f000-f07f claimed by ICH6 ACPI/GPIO/TCO
[    0.093210] pci 0000:00:1f.0: quirk: region f180-f1bf claimed by ICH6 GPIO
[   23.237755] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   23.237815] Intel ICH 0000:00:1e.2: setting latency timer to 64

```
I've tried the two different jacks and i also tried all the troubleshooting pages i could find. so...
bump

---

### Post by kadaitcha on 2010-02-06
Assistance would be greatly appreciated in respect of a microphone problem. As far as I'm aware, software is completely up to date as I get notifications every few days asking if its OK to update something or other. Machine is a Toshiba Satellite laptop, speakers work fine but despite days of trying every possible suggestion on the internet, I cannot get sound recorder / microphone input to show the slightest sign of life. Hardware is OK because it works fine in Windoze Vista & 'appears' to be supported in linux (speakers work well & a probe identified the sound card)  I've installed 'alsamixer' but in the absence of any relevant info, I haven't much idea  what its supposed to achieve. Only thing of note is that the output volume sliders move but the input ones don't. I notice the odd mention of configuring alsabase.conf but in the absence of a detailed HOWTO, I'm reluctant to mess around with it

Following output (from Comprehensive Sound Solutions Guide) might help someone diagnose this problem[COLOR=navy][U][B][SIZE=4]
[/SIZE][/B][/U][/COLOR]

:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Subsystem: Toshiba America Info Systems Device ff10
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff10
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f0a00000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at f0b00000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff10
    Flags: bus master, fast devsel, latency 0
    Memory at f0a80000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device ff10
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f0b40000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f0600000-f06fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f0700000-f07fffff
    Prefetchable memory behind bridge: 00000000f0200000-00000000f03fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=06, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: f0800000-f08fffff
    Prefetchable memory behind bridge: 00000000f0400000-00000000f05fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff10
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff10
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff10
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff10
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Toshiba America Info Systems Device ff10
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f0d44000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=0b, sec-latency=56
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: f0900000-f09fffff
    Prefetchable memory behind bridge: 0000000040000000-0000000043ffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Toshiba America Info Systems Device ff10
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
    Subsystem: Toshiba America Info Systems Device ff10
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 18b0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device ff10
    Flags: medium devsel, IRQ 10
    I/O ports at 18c0 [size=32]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
    Subsystem: Toshiba America Info Systems Device ff10
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at f0600000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at 2000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
    Subsystem: Askey Computer Corp. Device 7128
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f0700000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath5k

07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
    Subsystem: Toshiba America Info Systems Device ff10
    Flags: bus master, medium devsel, latency 168, IRQ 18
    Memory at f0906000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=07, secondary=08, subordinate=0b, sec-latency=176
    Memory window 0: 40000000-43fff000 (prefetchable)
    Memory window 1: 44000000-47fff000
    I/O window 0: 00005000-000050ff
    I/O window 1: 00005400-000054ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
    Subsystem: Toshiba America Info Systems Device ff10
    Flags: bus master, medium devsel, latency 128, IRQ 17
    Memory at f0905000 (32-bit, non-prefetchable) [size=2K]
    Memory at f0900000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
    Subsystem: Toshiba America Info Systems Device ff10
    Flags: bus master, medium devsel, latency 128, IRQ 18
    Memory at f0904000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
    Subsystem: Toshiba America Info Systems Device ff10
    Flags: bus master, medium devsel, latency 128, IRQ 18
    Memory at f0905800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

:~$ sudo modprobe snd-hda-intel
r:~$ 


OK, how is it possible for the sound card to work and to be correctly detected as such . whilst the module can't be found ?? Sounds like witchcraft to me. I suspect that there is something more to this step that hasn't been fully explained.  Hitting TAB once then ENTER, does absolutely nothing. Hitting TAB twice then ENTER brings up a huge list of things, nothing of which looks remotely relevant to drivers or modules..  The original kernel has been updated several times (automatically), however no update fixed or broke the sound input .... its NEVER worked at any time. 

[COLOR=navy][U][B][SIZE=4]
[/SIZE][/B][/U][/COLOR]

---

### Post by gh4ever on 2010-02-14
I haven't had much luck with my mike, either.
While trying to fix it, I REALLY screwed up my sound, I found a way to reset it and I'm doing that now.
I just found something, though, that may work for you....
Go to "Sound" under Preferences. Under the input, if there's more than one "Connector", test all of them.
I'm gonna try that right now, I'll let you know how it works out.

---

### Post by gh4ever on 2010-02-14
Yup, choosing "Microphone 2" under input fixed it for me.
Good luck!

---

### Post by super kim on 2010-03-21
It is still the thorn in my foot so to speak. I love ubuntu and have encouraged everyone I know to try it with great results. It bothers me that I cannot get the mic to work. If I knew more about sound cards and Linux I might be able to fix it. It is a problem because I want to use VOIP and without the mic I'm unable to.

I am hoping that the lucid update will fix it, but since the sound card isn't getting any newer I'm doubtful that there will be any support for old cards :(

---

