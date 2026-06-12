---
title: "Ubuntu laptop cannot connect to wired internet"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by Snowboi on 2011-08-30
Alright i recently got a new laptop
Lenovo Thinkpad T520(s)
and im having some troubles with the wired connection on ubuntu 10.04.3. The wired connection does not work on windows or ubuntu at all. (i am running a live cd of ubuntu, and windows 7 which i plan on removing anyways)

I have included some logs and testing below
```
ifconfig
```
gave
```


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:744 errors:0 dropped:0 overruns:0 frame:0
          TX packets:744 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56592 (56.5 KB)  TX bytes:56592 (56.5 KB)
```

```
sudo /etc/init.d/networking restart
```
gave
```
 * Reconfiguring network interfaces... 
``` 
With no message after that it just exited back to ubuntu@ubuntu
on the next line.

```
sudo pppoeconf
```
gave
```
/usr/sbin/pppoeconf: 523: modconf: not found
/usr/sbin/pppoeconf: 523: modconf: not found
/usr/sbin/pppoeconf: 523: modconf: not found
```

```
sudo iptables -L
```
gave
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

etc/network/interfaces
auto lo
iface lo inet loopback

sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

```

Checking my /etc/networks/interfaces gave
```
auto lo
iface lo inet loopback
```

```
sudo ifconfig wlan0 up
```
gave
```
wlan0: ERROR while getting interface flags: No such device
```

```
sudo pppoeconf
```
gave
```
sudo pppoeconf
/usr/sbin/pppoeconf: 523: modconf: not found
/usr/sbin/pppoeconf: 523: modconf: not found
/usr/sbin/pppoeconf: 523: modconf: not found
ubuntu@ubuntu:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

```
lspci -v
```
gave
```
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
	Subsystem: Lenovo Device 21cf
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Device 0126 (rev 09)
	Subsystem: Lenovo Device 21cf
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 5000 [size=64]
	Capabilities: <access denied>

00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
	Subsystem: Lenovo Device 21cf
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f2625000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:16.3 Serial controller: Intel Corporation Cougar Point KT Controller (rev 04) (prog-if 02)
	Subsystem: Lenovo Device 21cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	I/O ports at 50b0 [size=8]
	Memory at f262c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: serial

00:19.0 Ethernet controller: Intel Corporation Device 1502 (rev 04)
	Subsystem: Lenovo Device 21ce
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at f2600000 (32-bit, non-prefetchable) [size=128K]
	Memory at f262b000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 5080 [size=32]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04) (prog-if 20)
	Subsystem: Lenovo Device 21cf
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f262a000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
	Subsystem: Lenovo Device 21cf
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f2620000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: f2500000-f25fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b4)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f1d00000-f24fffff
	Prefetchable memory behind bridge: 00000000f0400000-00000000f0bfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b4)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f1400000-f1cfffff
	Prefetchable memory behind bridge: 00000000f0c00000-00000000f13fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04) (prog-if 20)
	Subsystem: Lenovo Device 21cf
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f2629000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation Device 1c4f (rev 04)
	Subsystem: Lenovo Device 21cf
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04) (prog-if 01)
	Subsystem: Lenovo Device 21cf
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 28
	I/O ports at 50a8 [size=8]
	I/O ports at 50bc [size=4]
	I/O ports at 50a0 [size=8]
	I/O ports at 50b8 [size=4]
	I/O ports at 5060 [size=32]
	Memory at f2628000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
	Subsystem: Lenovo Device 21cf
	Flags: medium devsel, IRQ 11
	Memory at f2624000 (64-bit, non-prefetchable) [size=256]
	I/O ports at efa0 [size=32]
	Kernel modules: i2c-i801

03:00.0 Network controller: Intel Corporation Device 0085 (rev 34)
	Subsystem: Intel Corporation Device 1311
	Flags: bus master, fast devsel, latency 0, IRQ 7
	Memory at f2500000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

0d:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 05) (prog-if 01)
	Subsystem: Lenovo Device 21cf
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f1401000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

0d:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 04) (prog-if 10)
	Subsystem: Lenovo Device 21cf
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f1400000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394
```

```
ifconfig -a
```
gave
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:744 errors:0 dropped:0 overruns:0 frame:0
          TX packets:744 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56592 (56.5 KB)  TX bytes:56592 (56.5 KB)

```

```
sudo iwconfig
```
gave
```
lo        no wireless extensions.
```

and kernel

```
uname -r
```
gave
```
2.6.32-33-generic
```

also this is an image of the terminal claiming i have no Ethernet card.

[IMG]http://img690.imageshack.us/img690/9364/screenshotubuntuubuntu.png[/IMG]

(note : pressing yes does absolutely nothing)

---

### Post by jtarin on 2011-08-30
[Chew on this and see if its digestable.]("http://ubuntuforums.org/archive/index.php/t-1741686.html")

---

### Post by Mark Phelps on 2011-08-30
It's not likely to be software or config settings if it does not work in BOTH Windows and Ubuntu.  You should check the BIOS settings to confirmed that the device is enabled.

Also, boot into Win7 and check the status of the device in Device Manager.

---

### Post by tmette on 2011-08-30
> **Mark Phelps said:**
> It's not likely to be software or config settings if it does not work in BOTH Windows and Ubuntu.  You should check the BIOS settings to confirmed that the device is enabled.

Also, boot into Win7 and check the status of the device in Device Manager.

This is what I would also suggest.  If it's enabled in the BIOS and your device manager in Windows is throwing yellow question marks, then I would assume it's a hardware failure.

---

### Post by jtarin on 2011-08-30
Wrong ...it is software....to be specific there is no driver for it. Read my link.

---

### Post by Snowboi on 2011-08-30
> **tmette said:**
> This is what I would also suggest.  If it's enabled in the BIOS and your device manager in Windows is throwing yellow question marks, then I would assume it's a hardware failure.
Its an institutional laptop so only way into bios is to force my way in is by breaking in >.<. The laptop seemed to connect fine at the university itself when i plugged in the ethernet cable.

> Wrong ...it is software....to be specific there is no driver for it. Read my link.


The laptop was able to connected before at the university sounds more like a hardware restriction or relating to bios.

also check this out
[Thinkpad T520 has been awarded Certified on ubuntu PC]("http://www.ubuntu.com/certification/hardware/201102-7229")

---

### Post by Mark Phelps on 2011-08-30
Given ...

> **Snowboi said:**
> ... The laptop seemed to connect fine at the university itself when i plugged in the ethernet cable.
and 
>  The laptop was able to connected before at the university 

I'm having problems seeing how this is a "driver" issue.  If there was no driver installed, then it would NEVER work, right?

However, since > Its an institutional laptop maybe the University IT folks have figured out a way to disable the netword card if it's outside a specific IP range.

---

### Post by jtarin on 2011-08-30
Issue the command ```
lsmod
``` and lets see what modules you have loaded.

---

### Post by Snowboi on 2011-08-30
Alright sorry guys seems the laptop can connect to the internet only on windows.
on ubuntu it cannot connect to the internet once again >.<

---

### Post by Snowboi on 2011-08-30
> **jtarin said:**
> Issue the command ```
lsmod
``` and lets see what modules you have loaded.

```
lsmod
```

```
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
dm_crypt               11331  0 
snd_hda_intel          22069  2 
snd_hda_codec          74201  1 snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8740  0 
snd                    54244  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tpm_tis                 7488  0 
uvcvideo               57374  0 
soundcore               6620  1 snd
tpm                    13936  1 tpm_tis
videodev               34361  1 uvcvideo
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
tpm_bios                5266  1 tpm
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63677  0 
serio_raw               3978  0 
squashfs               20744  1 
aufs                  149050  1 
nls_cp437               4919  1 
isofs                  29250  1 
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
ohci1394               26950  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
video                  17375  0 
output                  1871  1 video
softcursor              1189  1 bitblit
ieee1394               81181  1 ohci1394
ahci                   32360  1 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
ubuntu@ubuntu:~$ 

```

(sorry for double post)

---

