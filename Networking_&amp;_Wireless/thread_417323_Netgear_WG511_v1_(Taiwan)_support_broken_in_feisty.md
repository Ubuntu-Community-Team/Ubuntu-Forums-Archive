---
title: "Netgear WG511 v1 (Taiwan) support broken in feisty?"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by Typhoe on 2007-04-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/108602](https://bugs.launchpad.net/bugs/108602) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
Hi,

I would like to know if this wifi pcmcia card is still working out of the box on feisty for some users?

For I, it doesn't work anymore. I got a kernel bug and my system eventually freeze if I remove the card from the notebook.

I made an entry in launchpad.

Here are the trace I have:

lspci
< 03:00.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

dmesg
< [ 227.768000] pccard: card ejected from slot 0
< [ 233.480000] pccard: CardBus card inserted into slot 0
< [ 233.480000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
< [ 233.480000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [C0C4] -> GSI 11 (level, low) -> IRQ 11
< [ 233.480000] PCI: Setting latency timer of device 0000:03:00.0 to 64
< [ 233.604000] p54: LM86 firmware
< [ 235.792000] 0000:03:00.0 (prism54pci): Cannot read eeprom!
< [ 235.792000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
< [ 235.792000] prism54pci: probe of 0000:03:00.0 failed with error -22
< [ 235.792000] pci 0000:03:00.0: Error adding device, continuing
< [ 235.792000] ------------[ cut here ]------------
< [ 235.792000] kernel BUG at drivers/pci/bus.c:127!
< [ 235.792000] invalid opcode: 0000 [#1]
< [ 235.792000] SMP
< [ 235.792000] Modules linked in: prism54pci prism54common mac80211 cfg80211 binfmt_misc rfcomm l2cap bluetooth vboxdrv ppdev radeon drm speedstep_ich speedstep_lib cpufreq_userspace cpufreq_ondemand cpufreq_powersave cpufreq_stats freq_table cpufreq_conservative pcc_acpi tc1100_wmi sony_acpi dev_acpi container sbs button ac battery dock video i2c_ec i2c_core asus_acpi backlight ipv6 nfs lockd sunrpc lp fuse usb_storage gspca pcmcia videodev cinergyT2 joydev usbhid libusual hid dvb_core v4l2_common v4l1_compat snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event irtty_sir sir_dev irda parport_pc parport yenta_socket rsrc_nonstatic pcmcia_core pcspkr snd_seq snd_timer snd_seq_device snd soundcore crc_ccitt psmouse intel_agp agpgart snd_page_alloc serio_raw iTCO_wdt iTCO_vendor_support shpchp pci_hotplug af_packet tsdev evdev ext3 jbd mbcache sg sr_mod cdrom sd_mod generic ata_piix ata_generic libata scsi_mod floppy ehci_hcd ohci_hcd usbcore e100 mii thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
< [ 235.792000] CPU: 0
< [ 235.792000] EIP: 0060:[<c01f6aff>] Not tainted VLI
< [ 235.792000] EFLAGS: 00010246 (2.6.20-15-generic #2)
< [ 235.792000] EIP is at pci_bus_add_devices+0x10f/0x120
< [ 235.792000] eax: ca269008 ebx: ca269000 ecx: 00000046 edx: 00000000
< [ 235.792000] esi: de4b0c14 edi: de4b0c14 ebp: de4b0c00 esp: da40df38
< [ 235.792000] ds: 007b es: 007b ss: 0068
< [ 235.792000] Process pccardd (pid: 3624, ti=da40c000 task=dff4ea90 task.ti=da40c000)
< [ 235.792000] Stack: c037a1d0 c03711ec ca269100 de4b0c0c de4b0c14 de4b0c00 da599428 e09ed0b8
< [ 235.792000] da599578 00000002 da599428 00000000 da599578 da599548 e09e97e7 e09ed7e4
< [ 235.792000] e09ed5be 00000000 da599428 00000080 da599428 e09e9e9e c1404c40 00000000
< [ 235.792000] Call Trace:
< [ 235.792000] [<e09ed0b8>] cb_alloc+0x98/0xd0 [pcmcia_core]
< [ 235.792000] [<e09e97e7>] socket_insert+0xa7/0xf0 [pcmcia_core]
< [ 235.792000] [<e09e9e9e>] pccardd+0x20e/0x240 [pcmcia_core]
< [ 235.792000] [<c0120b40>] default_wake_function+0x0/0x10
< [ 235.792000] [<e09e9c90>] pccardd+0x0/0x240 [pcmcia_core]
< [ 235.792000] [<c013ac3a>] kthread+0xba/0xf0
< [ 235.792000] [<c013ab80>] kthread+0x0/0xf0
< [ 235.792000] [<c01044c7>] kernel_thread_helper+0x7/0x10
< [ 235.792000] =======================
< [ 235.792000] Code: 43 48 e8 25 e4 05 00 8d 93 00 01 00 00 89 54 24 08 89 44 24 04 c7 04 24 fc a1 37 c0 e8 1b 01 f3 ff eb 8a 83 c4 0c 5b 5e 5f 5d c3 <0f> 0b eb fe 8d b6 00 00 00 00 8d bc 27 00 00 00 00 55 89 d5 57
< [ 235.792000] EIP: [<c01f6aff>] pci_bus_add_devices+0x10f/0x120 SS:ESP 0068:da40df38

Regards,
Typhoe

---

### Post by computx on 2007-04-24
I also am having issues with this  adapter onder feisty. It doesn't freeze my computer but the activity light constantly flashes and I lose connection to the net every few minutes. If I go to network manager and uncheck/check wlan0 it will start again. Unfortunatly Feisty has certainly been a buggy release on my thinkpad laptop. I may be going back to Edgy if there aren't some updates soon.

---

### Post by Typhoe on 2007-04-24
A dev seems to have fix it in the kernel source.

I'm waiting for the fix to be release as a binary kernel to test it (and close the launchpad bug thread).

And indeed, I have encounter some glishes I never had with an ubuntu release on my notebook too.

For exemple, I can't manage to get the dual screen to work on feisty (notebook 1440*1050 + lcd 1920*1200 on ati chipset). That has been perfectly working in the previous (since hoary).

If I can't resolve my problems, I'll certainly switch back to dapper too, and wait for gusty...(and prey :p)

regards.

---

### Post by brainstuff on 2008-03-24
if anyone out there is having trouble with this card in Xubuntu 7.10, I got mine running by following this ndiswrapper guide: 
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

The weird thing though is that I don't think it's using ndiswrapper despite going through the motions - it started working after I added 
```
blacklist prism54
```
to /etc/modprobe.d/blacklist ...and rebooted.
Now when I do ```
lshw -C network
``` the driver shows up as **prism54pci** 

is that weird or what? either way, this is the first time i've ever been able to use this dang card in Ubuntu, so that's another nail in the Windows coffin :-)

---

