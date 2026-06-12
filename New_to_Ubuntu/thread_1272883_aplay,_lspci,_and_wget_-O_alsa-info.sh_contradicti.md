---
title: "aplay, lspci, and wget -O alsa-info.sh contradictions"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by allen blake on 2009-09-22
Sound is not muted
Sliders are up
Sound card is actual card, not built on motherboard. 
Appears to be seated well

**Some symptoms:**

No sound in any aspect of system

sound preferences under volume control preferences grayed out

troubleshoot told me to select sound card under "mixer track", but sound card doesn't appear

attempted to edit implicit authorizations to "yes, yes, yes," but "modify" grayed out

mplayer crashed while silently playing song (sometimes, but I failed to get details)

**Pages I have been referred to by members:**

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://www.compuhowto.com/linux/ubuntu/ubuntu-no-sound/](http://www.compuhowto.com/linux/ubuntu/ubuntu-no-sound/)

***************Confusion with aplay-l:*********************************

With [COLOR=Blue]**Gnome Terminal**[/COLOR], this is the output:

aplay: device_list:217: [COLOR=Blue]**no soundcards found...**[/COLOR]

-----

With the [COLOR=SeaGreen]**Root Terminal**[/COLOR], this is the output:

-----

**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: **[COLOR=SeaGreen]ES1371/1 [ES1371 DAC2/ADC][/COLOR]**
Subdevices: [COLOR=Red]**1**[/COLOR]/1
Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: [COLOR=SeaGreen]**ES1371/2 [ES1371 DAC1/ADC]**[/COLOR]
Subdevices: 1/1
Subdevice #0: subdevice #0

-----
From **[COLOR=Purple]the terminal before "startx"[/COLOR]** just after booting:

[COLOR=Red]I: caps.c: Limited capabilities successfully to CAPS_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CPAS_SYS_NICE.[/COLOR]

card 0: AudioPCI [Ensoniq AudioPCI], device 0: [COLOR=Purple]**ES1371/1 [ES1371 DAC2/ADC]**[/COLOR]
Subdevices: [COLOR=Red]**0**[/COLOR]/1
Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: **[COLOR=Purple]ES1371/2 [ES1371 DAC1/ADC][/COLOR]**
Subdevices: 1/1
Subdevice #0: subdevice #0

************** end aplay confusion**********************************

Results from "lspci -v | less" as instructed to retrieve by forum member:

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
Flags: bus master, medium devsel, latency 64
Memory at e4000000 (32-bit, prefetchable) [size=64M]
Capabilities: <access denied>
Kernel driver in use: agpgart-intel
Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
Flags: bus master, 66MHz, medium devsel, latency 64
Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
I/O behind bridge: 0000d000-0000dfff
Memory behind bridge: d4000000-e3ffffff
Prefetchable memory behind bridge: e8000000-ebffffff
Kernel modules: shpchp

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
Flags: bus master, medium devsel, latency 64
[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
I/O ports at f000 [size=16]
Kernel driver in use: ata_piix

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
Flags: bus master, medium devsel, latency 64, IRQ 10
I/O ports at e000 [size=32]
Kernel driver in use: uhci_hcd

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
Flags: medium devsel, IRQ 9
Kernel driver in use: piix4_smbus
Kernel modules: i2c-piix4

(Note Audio Controller Recognized Here)

[COLOR=Red][B]00:0e.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 0
Subsystem: Ensoniq ES1371 [AudioPCI-97]
Flags: bus master, slow devsel, latency 64, IRQ 11
I/O ports at e400 [size=64]
Capabilities: <access denied>
Kernel driver in use: ENS1371
Kernel modules: snd-ens1371[/B][/COLOR]

00:10.0 Ethernet controller: 3Com Corporation 3c900B-TPO Etherlink XL [Cyclone] (rev 04)
Subsystem: 3Com Corporation 3c900B-TPO Etherlink XL [Cyclone]
Flags: bus master, medium devsel, latency 64, IRQ 5
I/O ports at e800 [size=128]
Memory at ed000000 (32-bit, non-prefetchable) [size=128]
Expansion ROM at ec000000 [disabled] [size=128K]
Capabilities: <access denied>
Kernel driver in use: 3c59x
Kernel modules: 3c59x

01:00.0 VGA compatible controller: S3 Inc. 86C410 Savage 2000 (rev 02)
Subsystem: Diamond Multimedia Systems Device 5934
Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 11
Memory at e1000000 (32-bit, non-prefetchable) [size=512K]
Memory at e8000000 (32-bit, prefetchable) [size=64M]
Memory at d4000000 (32-bit, non-prefetchable) [size=64M]
Memory at d8000000 (32-bit, non-prefetchable) [size=64M]
Memory at dc000000 (32-bit, non-prefetchable) [size=64M]
[virtual] Expansion ROM at e0000000 [disabled] [size=64K]
Capabilities: <access denied>
Kernel modules: savagefb

=====================================================

[B]From Trouble Shooting Sound page to which I was referred by forum member:
[/B]

Open a terminal window, and type "find /lib/modules/`uname -r` | grep snd". You should see a whole list of items come up. If you don't, it means that the upgrade process missed installing the kernel modules for sound. To fix this, type this at the command line:

**sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic**

For Ubuntu 9.04 Jaunty Jackalope

**sudo aptitude install linux-restricted-modules-`uname -r` linux-generic**

[COLOR=Red]Note that I accidentally did both of these instructions, instead of just the second
that is for 9.04.  They both executed, but I didn't write down or capture every thing
they executed.  Maybe the first one aborted itself because it wasn't correct.  I don't
know.  The Troubleshooting guide didn't say which distro the first line went with?  But,
I did do the second, I caught it, but then later in my confusion, did the first by
accident, as well.  Oops.  [COLOR=Black]**Did I screw something up?**[/COLOR]  Also, it asked for British
English, with no other choice when executing the "Jaunty" version, I believe?[/COLOR]

=============================================================

**Further troubleshooting suggested this:**

**[COLOR=Red]wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh[/COLOR]**

--2009-09-21 11:29:52-- [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh)
Resolving alsa-project.org... 212.20.107.51
Connecting to alsa-project.org|212.20.107.51|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-...s/alsa-info.sh](http://git.alsa-project.org/?p=alsa-...s/alsa-info.sh) [following]
--2009-09-21 11:29:53-- [http://git.alsa-project.org/?p=alsa-...s/alsa-info.sh](http://git.alsa-project.org/?p=alsa-...s/alsa-info.sh)
Resolving git.alsa-project.org... 212.20.107.51
Reusing existing connection to alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

[ <=> ] 26,584 36.4K/s in 0.7s

2009-09-21 11:29:54 (36.4 KB/s) - `alsa-info.sh' saved [26584]

ALSA Information Script v 0.4.58
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

dmesg
lspci
lsmod
aplay
amixer
alsactl
/proc/asound/
/sys/class/sound/
~/.asoundrc (etc.)

See './alsa-info.sh --help' for command line options.

/sbin/alsactl: save_state:1513: [COLOR=Red]**No soundcards found...**[/COLOR]
cat: /tmp/alsa-info.eIPkKalLJY/alsactl.tmp: [COLOR=Red]**No such file or directory**[/COLOR]

---

### Post by hailtothethief on 2009-09-23
Try running and posting the output of these four commands (one at a time)

```

dpkg-query -l | grep linux-restricted
dpkg-query -l | grep linux-ubuntu
uname -r
amixer

```

I appreciate you being so thorough. Try some other things to rule out other possibilities e.g. running another OS and playing sound through it, try listening to music with headphones plugged in to the speaker port, etc.

---

### Post by allen blake on 2009-09-23
Thank you for your reply.  I am building some of these computers as donator machines to new Linux users.  There are five or so that were identical, pulled from a dumpster.  I can also swap out the sound card, for an identical one, if you wish, to verify that it isn't hardware-related specific to that one card (damaged, etc.), but it sure seems software related, given the contradictions I am getting in recognizing presence?  Despite the fact that these were pulled from the dumpster they are very clean machines.  They were actually sitting NEXT TO the dumpster :)

I will return home late, and attempt to get on those further suggestions as soon as I can.

Again, thank you for the reply.

---

### Post by allen blake on 2009-09-24
I got in late last night, and was unable to get anything accomplished wrt this system.  Anyone have any insight into the differing output from different terminal locations/logins, etc?

Should get to it tonight, or tomorrow.  If you checked back in based on my predicted return, thank you, and I apologize.  I will be all over it like white on rice, Friday, Saturday, and Sunday.

TIA

---

### Post by allen blake on 2009-09-25
Output from [COLOR=SandyBrown]ROOT TERMINAL[/COLOR]:

[COLOR=Lime]dpkg-query -l | grep linux-restricted[/COLOR]

[COLOR=Red]ii  linux-restricted-modules-2.6.28-15-generic 2.6.28-15.20                           Non-free Linux kernel modules for version 2.
ii  linux-restricted-modules-common            2.6.28-15.20                               Non-free Linux 2.6.28 modules helper script
ii  linux-restricted-modules-generic           2.6.28.15.20                                  Restricted Linux modules for generic kernels[/COLOR]

[COLOR=Lime]dpkg-query -l | grep linux-ubuntu[/COLOR]

[COLOR=Red]This command does nothing visible, output is equivalent to me just hitting the "enter" key.  It takes me to an identical root command prompt just under the previous one.
[/COLOR]
[COLOR=Lime]uname -r[/COLOR]

[COLOR=Red]2.6.28-15-generic[/COLOR]

[COLOR=Lime]amixer[/COLOR]

[COLOR=Red]Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 51 [81%] [-18.00dB] [on]
  Front Right: Playback 51 [81%] [-18.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [-9.00dB] [on]
  Front Right: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]


[/COLOR]

---

### Post by allen blake on 2009-09-25
Also, I am wondering?  Should I be posting this in the other forums, because I am not getting many bites in the "Absolute Beginners" Forum?

Thanks.

---

