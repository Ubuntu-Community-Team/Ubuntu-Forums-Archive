---
title: "No sound in Ubuntu 8.10"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by GHFury on 2009-02-01
Hi! I recently built a computer for me and everything works great. Except I can't get any sound in Ubuntu 8.10. I have no idea why so I thought u could help me! :D My soundcard is a C-Media CMI8738.

---

### Post by matthewbrave on 2009-02-01
have you done the hardware testing?

system>administration>hardware testing

---

### Post by GHFury on 2009-02-01
Yes, I have. No sound anyways... :(

---

### Post by treykee on 2009-02-01
I've been able to remedy different sound issues on various machines using this as a guide: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by GHFury on 2009-02-02
I cant find a driver for my soundcard... Could it just be the driver?

---

### Post by halovivek on 2009-02-03
Could you post your computer configuration ?

Could you post output of this from the terminal

lspci

---

### Post by phr0ze on 2009-02-03
The latest kernel stopped my sound from working... maybe that happened to you too. When you boot, press escape at grub and choose one kernel before. (not the recovery kernels, just go down two).

See if that helps. It brought my sound back.

---

### Post by srtraveler on 2009-02-03
start up with previous kernel (skip recovery mode)

This worked for me after days, off and on, fiddling and thinking of buying more books, rebooting 8.0x, etc.:>)

---

### Post by XanTrax on 2009-02-03
Please post the output of 

```

sudo lshw -C sound

```

and

```

sudo lspci -v 

```



**EDIT:**

In fact, I have been troubleshooting this problem repeatedly lately. So, I made a post on my website about it.  If you are interested: [http://ckozler.net/?p=70](http://ckozler.net/?p=70)

This is more for the HDA Intel Sound device but can be broadened to all sound devices that were working and stop after a kernel upgrade (or randomly).

---

### Post by GHFury on 2009-02-03
On the first one:
rickard@rickard-desktop:~$ sudo lshw -C sound
[sudo] password for rickard: 
  *-multimedia:0          
       description: Multimedia audio controller
       product: CM8738
       vendor: C-Media Electronics Inc
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=C-Media PCI latency=32 maxlatency=24 mingnt=2 module=snd_cmipci
  *-multimedia:1
       description: Multimedia audio controller
       product: CM8738
       vendor: C-Media Electronics Inc
       physical id: b
       bus info: pci@0000:01:0b.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=C-Media PCI latency=32 maxlatency=24 mingnt=2 module=snd_cmipci
rickard@rickard-desktop:~$ 

And the second one:
rickard@rickard-desktop:~$ sudo lspci -v
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev a2)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Memory at e0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [40] AGP version 3.0
	Capabilities: [60] HyperTransport: Host or Secondary Interface
	Kernel driver in use: agpgart-nvidia
	Kernel modules: nvidia-agp

00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
	Subsystem: nVidia Corporation Device 0c17
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
	Subsystem: nVidia Corporation Device 0c17
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
	Subsystem: nVidia Corporation Device 0c17
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
	Subsystem: nVidia Corporation Device 0c17
	Flags: 66MHz, fast devsel

00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
	Subsystem: nVidia Corporation Device 0c17
	Flags: 66MHz, fast devsel

00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
	Subsystem: nVidia Corporation Device 0c11
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [48] HyperTransport: Slave or Primary Interface

00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
	Subsystem: nVidia Corporation Device 0c11
	Flags: 66MHz, fast devsel, IRQ 12
	I/O ports at dc00 [size=32]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3) (prog-if 10)
	Subsystem: nVidia Corporation Device 0c11
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at e9087000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3) (prog-if 10)
	Subsystem: nVidia Corporation Device 0c11
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at e9082000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3) (prog-if 20)
	Subsystem: nVidia Corporation Device 0c11
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at e9083000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port: BAR=1 offset=0080
	Capabilities: [80] Power Management version 2
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
	Subsystem: nVidia Corporation Device 0c11
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at e9086000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at e000 [size=8]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 00009000-0000afff
	Memory behind bridge: e8000000-e8ffffff
	Kernel modules: shpchp

00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: Device f0de:0c11
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
	Flags: bus master, 66MHz, medium devsel, latency 32
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: e6000000-e7ffffff
	Prefetchable memory behind bridge: c0000000-dfffffff
	Kernel modules: shpchp

01:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: C-Media Electronics Inc CM8738
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at 9000 [size=256]
	Capabilities: [c0] Power Management version 2
	Kernel driver in use: C-Media PCI
	Kernel modules: snd-cmipci

01:0b.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: Chaintech Computer Co. Ltd Device 1102
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at 9400 [size=256]
	Capabilities: [c0] Power Management version 2
	Kernel driver in use: C-Media PCI
	Kernel modules: snd-cmipci

03:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
	Subsystem: ATI Technologies Inc Device 4772
	Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 19
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at c000 [size=256]
	Memory at e7000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at e6000000 [disabled] [size=128K]
	Capabilities: [58] AGP version 3.0
	Capabilities: [50] Power Management version 2
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeonfb

03:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
	Subsystem: ATI Technologies Inc Device 4773
	Flags: 66MHz, medium devsel
	Memory at d0000000 (32-bit, prefetchable) [disabled] [size=256M]
	Memory at e7010000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: [50] Power Management version 2

rickard@rickard-desktop:~$ 

And now I've noticed that ubuntu wont find my soundcard!
rickard@rickard-desktop:~$ aplay -l
aplay: device_list:215: no soundcards found...
rickard@rickard-desktop
And when I doubleclick the sound icon, som window pops up saying something like: no volumecontrolled GStreamer modules found or something like that..

What's wrong?

---

### Post by jbehl on 2009-02-03
I found a box checked enabling ditial output unber the sound card options in the volume menu. I cleared the box and it fixed the sound issue.
You might try that.

---

### Post by XanTrax on 2009-02-03
> **GHFury said:**
> On the first one:
rickard@rickard-desktop:~$ sudo lshw -C sound
[sudo] password for rickard: 
  *-multimedia:0          
       description: Multimedia audio controller
       product: CM8738
       vendor: C-Media Electronics Inc
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=C-Media PCI latency=32 maxlatency=24 mingnt=2 module=snd_cmipci
  *-multimedia:1
       description: Multimedia audio controller
       product: CM8738
       vendor: C-Media Electronics Inc
       physical id: b
       bus info: pci@0000:01:0b.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=C-Media PCI latency=32 maxlatency=24 mingnt=2 module=snd_cmipci
rickard@rickard-desktop:~$ 



01:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: C-Media Electronics Inc CM8738
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at 9000 [size=256]
	Capabilities: [c0] Power Management version 2
	Kernel driver in use: C-Media PCI
	Kernel modules: snd-cmipci

01:0b.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: Chaintech Computer Co. Ltd Device 1102
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at 9400 [size=256]
	Capabilities: [c0] Power Management version 2
	Kernel driver in use: C-Media PCI
	Kernel modules: snd-cmipci

rickard@rickard-desktop:~$ 

And now I've noticed that ubuntu wont find my soundcard!
rickard@rickard-desktop:~$ aplay -l
aplay: device_list:215: no soundcards found...
rickard@rickard-desktop
And when I doubleclick the sound icon, som window pops up saying something like: no volumecontrolled GStreamer modules found or something like that..

What's wrong?

Thank you.  I see that lspci -v is showing two audio controllers as is lshw, you may need to rearrange or remove them from a configuration file

First, please post the output of:

```

cat /etc/modprobe.d/alsa-base

```

Then:

Can you please try the sound preferences part of the tutorial I linked to?  I want to see what happens when you test each one of the selections in Sound Preferences.  Make sure to TEST each selection in the Sound Playback area of the preferences and tell me what errors or problems you encounter.  It will either be no sound or the error message that I have posted on that tutorial.

If you can not get it working after that please also post the output of:

```

sudo dmesg | grep -i snd &&  sudo lsmod | grep -i snd

```

Copy and paste it in if need be.

---

### Post by GHFury on 2009-02-03
Ok, here it is:

rickard@rickard-desktop:~$ cat /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

And I've mixed around in the sound preferences aswell. Every time I test each option, that error window shows up.

And when I type in the other one, nothing happens in terminal.
rickard@rickard-desktop:~$ sudo dmesg | grep -i snd &&  sudo lsmod | grep -i snd
rickard@rickard-desktop:~$

I'm confused...

---

### Post by XanTrax on 2009-02-03
Weird.

That second command is supposed to show loaded modules and pull out information regarding your module snd-cmipci, but nothing shows.  The dmesg part of the second command outputs messages sent to the kernel buffer and is also supposed to pull out information about your snd-cmipci module.  What happens when you run the commands indepdentently?

```

sudo lsmod | grep -i snd
sudo dmesg | grep -i snd

```

?

Also, can you post the output of

```

grep 'audio' /etc/group

```

Thank you.

I have never dealt with your sound card before but all these steps I am doing can eventually lead up to a solution.  You can google for "C-Media ubuntu" or "no sound C-media ubuntu" or "CM8738 ubuntu" in the mean time while I try to work with your issue.

EDIT:

Two more commands:

```

sudo modprobe -l | grep -i snd-cmipci
sudo modprobe -l | grep -i snd_cmi

```

---

### Post by GHFury on 2009-02-04
First one:
rickard@rickard-desktop:~$ sudo lsmod | grep -i snd
[sudo] password for rickard: 
snd_cmipci             42400  0 
gameport               19468  1 snd_cmipci
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         16136  1 snd_pcm
snd_opl3_lib           18560  1 snd_cmipci
snd_hwdep              15236  1 snd_opl3_lib
snd_mpu401_uart        15360  1 snd_cmipci
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device         15116  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  12 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd

Nothing happens on the sudo dmesg | grep -i snd command...

grep 'audio' /etc/group output:
rickard@rickard-desktop:~$ grep 'audio' /etc/group
audio:x:29:pulse

I've searched around internet for an solution for like 3 weeks. I havent found anything useful...


rickard@rickard-desktop:~$ sudo modprobe -l | grep -i snd-cmipci
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-cmipci.ko


And nothing happens on the sudo modprobe -l | grep -i snd_cmi command either...

---

### Post by XanTrax on 2009-02-04
> **GHFury said:**
> First one:
rickard@rickard-desktop:~$ sudo lsmod | grep -i snd
[sudo] password for rickard: 
snd_cmipci             42400  0 
gameport               19468  1 snd_cmipci
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         16136  1 snd_pcm
snd_opl3_lib           18560  1 snd_cmipci
snd_hwdep              15236  1 snd_opl3_lib
snd_mpu401_uart        15360  1 snd_cmipci
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device         15116  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  12 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd

Nothing happens on the sudo dmesg | grep -i snd command...

grep 'audio' /etc/group output:
rickard@rickard-desktop:~$ grep 'audio' /etc/group
audio:x:29:pulse

I've searched around internet for an solution for like 3 weeks. I havent found anything useful...


rickard@rickard-desktop:~$ sudo modprobe -l | grep -i snd-cmipci
/lib/modules/2.6.27-11-generic/kernel/sound/pci/snd-cmipci.ko


And nothing happens on the sudo modprobe -l | grep -i snd_cmi command either...

Honestly, hate to tell you this...I am at a loss.  The modules are loaded into the kernel alright, your hardware has a claimed driver, and yet...nothing is working.  From what I have found on google it almost seems as if your card wont work.  You can try one more thing but I am not sure exactly what to do with it.  I am guessing to edit the 

/etc/modprobe.d/alsabase

and append these lines to the end:

```


alias sound-slot-0 snd-cmipci
above snd-cmipci snd-pcm-oss
options snd-cmipci snd_index=0 snd_id="C-Media-8738-6Ch"
options snd_pcm_hw_params_set_access(pcm, hw, SND_PCM_ACCESS_MMAP_INTERLEAVED);
options snd_pcm_hw_params_set_format(pcm, hw, SND_PCM_FORMAT_S16_LE);
options snd_pcm_hw_params_set_channels(pcm, hw, 6);

```

Found here: [https://www.linuxquestions.org/questions/linux-hardware-18/surround-sound-snd-cmipci-135156/](https://www.linuxquestions.org/questions/linux-hardware-18/surround-sound-snd-cmipci-135156/)

He has the same card as you and says he only gets low output from the bass and the center.  I do not know what you have, but you can try that.  That thread is from 4, almost 5 years ago so I would back up the file first.

Good luck, sorry but I am at a loss :(.

Also, you can try this: [http://ubuntuforums.org/archive/index.php/t-402293.html](http://ubuntuforums.org/archive/index.php/t-402293.html)

---

### Post by GHFury on 2009-02-04
Dang... This is like a mystery... I typed /etc/modprobe.d/alsabase in the terminal and it said: "the file or catalog does not excist..." I'm getting really sick of this and I'm thinking of installing Windows XP.

---

### Post by XanTrax on 2009-02-04
> **GHFury said:**
> Dang... This is like a mystery... I typed /etc/modprobe.d/alsabase in the terminal and it said: "the file or catalog does not excist..." I'm getting really sick of this and I'm thinking of installing Windows XP.

at terminal:

sudo gedit /etc/modprobe.d/alsa-base

---

### Post by GHFury on 2009-02-05
I get this:

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

---

### Post by markbuntu on 2009-02-05
Go here for sound troubleshooting help


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by HittingSmoke on 2009-02-05
> **jbehl said:**
> I found a box checked enabling ditial output unber the sound card options in the volume menu. I cleared the box and it fixed the sound issue.
You might try that.

Have you tried this solution? I have to do this every time I make a fresh install.

Start with the simple stuff first ;)

---

### Post by GHFury on 2009-02-06
When I doubleclick the volume icon, I get a window saying something like: Volume control did not find any GStreamer modules or your soundcard is not installed or some thing like that... :S

Help?

---

