---
title: "Ndiswrapper, Segmentation Fault, 8.04"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by Silenc3 on 2008-10-01
Hello, if have a problem and no idea how to fix it :S, last time i used ubuntu was version 7.04, ndiswrapper was working fine with my pci marvell libertas 88W8335, i wanted to check out the latest ubuntu so i installed 8.04 but ndiswrapper is not working anymore :(, i install the driver (the same files i used in 7.04), i do "ndiswrapper -l" driver is listed and hardware is found....but..."sudo modprobe ndiswrapper" show Segmentation Fault :S i tried to reinstall from repo and from source, nothing works, always the same error, is a clean installation. Also error only appears first time is executed then if i tried later no error appears, no output, command gets stucked.

I have no idea at all, i have searched all over the internet.

Any idea? Thanks!!

PD: Sorry for my bad english :/

---

### Post by Silenc3 on 2008-10-01
Anyone? :( I think maybe is something related with kernel but it exceeds my knowledge.

---

### Post by vikram on 2008-10-01
> **Silenc3 said:**
> Anyone? :( I think maybe is something related with kernel but it exceeds my knowledge.

I had a similar issue. I spent hours trying to troubleshoot it in linux only to find it wasnt a linux issue at all but a windows driver issue. Issue was resolved after using the latest windows XP driver.

also check if you have blacklisted any native driver

---

### Post by Silenc3 on 2008-10-02
I found more drivers for the chip  but none of them detects the  hardware, is a asus card there is only one driver in the support site :(, it worked fine before i can't understand why is not working now.

Is a Marvell 88W8335 (Libertas) rev43.

---

### Post by Ayuthia on 2008-10-02
Can you post the results of (from the Terminal):
```
ndiswrapper -v
ndiswrapper -l
```

---

### Post by caljohnsmith on 2008-10-02
I've got a wireless card that uses the same Marvell 88w8335 chip, and mine works great with ndiswrapper in Hardy. Be sure to post the output of the commands that Ayuthia asked for as that may shed some light on your problem, but I'm attaching my 88w8335 drivers to this post so you can download and try them if you want.

---

### Post by Silenc3 on 2008-10-02
Here the output, with some extra info, thanks.
```

ndiswrapper -v
modinfo: could not open ndiswrapper: No such device
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not open ndiswrapper: No such device

You may need to upgrade driver and/or utils to latest versions available at
http://ndiswrapper.sourceforge.net

ndiswrapper -l
cb55n51 : driver installed
        device (11AB:2A01) present


uname -a
Linux Testbox 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux


lspci
00:00.0 Host bridge: Intel Corporation 82955X Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation 82955X PCI Express Root Port (rev 81)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:01.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
01:02.0 Multimedia audio controller: Creative Labs SB X-Fi
01:04.0 Mass storage controller: Integrated Technology Express, Inc. ITE 8211F Single Channel UDMA 133 (rev 11)
01:05.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
01:0f.0 Ethernet controller: Marvell Technology Group Ltd. 88W8335 [Libertas] 802.11b/g Wireless (rev 43)
02:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
03:00.0 Ethernet controller: Intel Corporation 82573V Gigabit Ethernet Controller (Copper) (rev 03)
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)

```

Searching for the chip id i found this in ndiswrapper old site (google cached):

```
Card: Asus P5WD2 Premium Motherboar with Wi-fi/Tv Hybrid

    *  Chipset: cb55n5x PCI
    *  PCI ID: 11AB:2A01
    *  Driver: WinXP driver. (cb55n51.sys)
    *  Linux: Kubuntu 7.04 (kernel 2.6.20)
    *  Ndiswrapper: 1.43 (smp=yes)
    *  Note: AP (master) mode not supported
```

Any help is greatly appreciated.

---

### Post by Silenc3 on 2008-10-02
Thanks caljohnsmith i'll check with your driver.

---

### Post by caljohnsmith on 2008-10-02
Looks like your installed ndiswrapper may be messed up. Did you install ndiswrapper from the repositories or did you download the latest version and compile it yourself? 

Try doing:
```
sudo rm -fr /etc/ndiswrapper/*
```
Don't be alarmed by the above "rm" command; it is just to make sure the ndiswrapper driver in the /etc/ndiswrapper directory gets completely uninstalled.
```
sudo apt-get purge ndiswrapper-utils-1.9 ndiswrapper-common
```
If the above command works, then reinstall ndiswrapper with:
```
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
```
Once ndiswrapper is installed again, try using your "88w8335" drivers that you used previously that worked (don't use the ones I posted in my previous message yet, it is better to use the ones that worked for you before). Let me know how it goes or what problems you run into.

---

### Post by Silenc3 on 2008-10-02
Hi, hmm i installed ndiswrapper from kubuntu cd, i haven't wired connection, router is too far away so wifi is my only option, i tried to remove and reinstall but error remains. 
I downloaded the source (i have multiboot), but is not compiling (make &&make install).
About 88w8335 there is a problem it seems that there are two revs 3 & 43, mine is 43 i tried with a lot of drivers and none detects the hardware (i tried also the one you posted), cb55n51 is the one i used before and worked fine, hardware is detected, also i haven't found more drivers for rev 43.

:/

---

### Post by caljohnsmith on 2008-10-02
If you have access to the internet from another computer, you could download those ndiswrapper packages from packages.ubuntu.com, copy them into your Ubuntu, and then install them from there. For instance, if you copy the packages to your desktop, you can then do:
```
cd ~/Desktop
sudo dpkg -i ndis*
```
Or if your Kubuntu CD is not too old and has those versions of ndiswrapper that you need, you could put it in your CD-ROM drive and do:
```
sudo apt-cdrom add
```
And then run the apt-get commands I gave previously, first uninstalling ndiswrapper and then installing it again. Let me know how that goes.

---

### Post by Silenc3 on 2008-10-02
I removed ndiswrapped and then reinstalled the updated packages from packages.ubuntu.com:

```
root@Testbox:~# ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-19-generic SMP mod_unload 586
root@Testbox:~# ndiswrapper -l
cb55n51 : driver installed
        device (11AB:2A01) present
root@Testbox:~# modprobe ndiswrapper
Segmentation fault
root@Testbox:~#
```

I don't know what to do.

---

### Post by caljohnsmith on 2008-10-02
Maybe if Ayuthia or pytheas22 come around, they might have seen this kind of problem before and know better what to do; but in the meantime, before you do anything else, please post:
```
dmesg | grep -e ndiswrapper -e wlan0 -e error -e warning -e modprobe
```
That might give us some clues what is going on.

---

### Post by Silenc3 on 2008-10-02
LOL I'm writing this from Kubuntu, this time it worked and i haven't changed anything in configuration! o.O I hope it'll continue working :S:

```

root@Testbox:~# modprobe ndiswrapper
root@Testbox:~# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:E2:2F:0E
                    ESSID:"Wireless"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:20/100  Signal level:-83 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0                   


```

After manually configuring..:

```

root@Testbox:~# ping google.es
PING google.es (216.239.59.104) 56(84) bytes of data.
64 bytes from 216.239.59.104: icmp_seq=1 ttl=243 time=104 ms
64 bytes from 216.239.59.104: icmp_seq=2 ttl=243 time=105 ms
64 bytes from 216.239.59.104: icmp_seq=3 ttl=243 time=108 ms

--- google.es ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10336ms
rtt min/avg/max/mdev = 104.001/105.884/108.209/1.785 ms


```

:D, i don't know how is working now lol.

---

### Post by Ayuthia on 2008-10-02
> **Silenc3 said:**
> LOL I'm writing this from Kubuntu, this time it worked and i haven't changed anything in configuration! o.O I hope it'll continue working :S:

```

root@Testbox:~# modprobe ndiswrapper
root@Testbox:~# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:E2:2F:0E
                    ESSID:"Wireless"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:20/100  Signal level:-83 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0                   


```

After manually configuring..:

```

root@Testbox:~# ping google.es
PING google.es (216.239.59.104) 56(84) bytes of data.
64 bytes from 216.239.59.104: icmp_seq=1 ttl=243 time=104 ms
64 bytes from 216.239.59.104: icmp_seq=2 ttl=243 time=105 ms
64 bytes from 216.239.59.104: icmp_seq=3 ttl=243 time=108 ms

--- google.es ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10336ms
rtt min/avg/max/mdev = 104.001/105.884/108.209/1.785 ms


```

:D, i don't know how is working now lol.

Just to play it safe, you might want to keep track of what is currently being used:
```
lshw -C network
```
It will help you see what driver it is using in case it is not using ndiswrapper.

---

### Post by Silenc3 on 2008-10-03
I restarted and is still working :D, here the output:

```

*-network:1
       description: Wireless interface
       product: 88W8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: f
       bus info: pci@0000:01:0f.0
       logical name: wlan0
       version: 43
       serial: 00:13:d4:9c:1b:87
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+cb55n51 driverversion=1.52+Marvell,04/16/2005,2.0.0.16 ip=192.168.1.13 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11b

```

---

### Post by Silenc3 on 2008-10-03
It was too nice to be true...i restarted and... seg fault:

```
root@Testbox:~$ dmesg | grep -e ndiswrapper -e wlan0 -e error -e warning -e modprobe
[   34.404612] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[  121.552516] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  121.622570] ndiswrapper: driver cb55n51 (Marvell,04/16/2005,2.0.0.16) loaded
[  121.623690] Modules linked in: ndiswrapper rfcomm l2cap bluetooth ppdev acpi_cpufreq cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table video output container sbs sbshc dock battery iptable_filter ip_tables x_tables aes_i586 dm_crypt dm_mod ac lp zc0301 saa7134_alsa snd_pcm_oss snd_mixer_oss snd_pcm gspca snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore agpgart snd_page_alloc saa7134 compat_ioctl32 videobuf_dma_sg videobuf_core ir_kbd_i2c psmouse i2c_core ir_common serio_raw videodev v4l2_common v4l1_compat button parport_pc parport evdev iTCO_wdt iTCO_vendor_support pcspkr shpchp pci_hotplug reiserfs sr_mod cdrom sg sd_mod ata_piix ata_generic usb_storage libusual floppy skge pata_acpi pata_it821x sata_sil24 ehci_hcd uhci_hcd usbcore libata scsi_mod e1000 thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  121.623764] Pid: 6257, comm: modprobe Tainted: P        (2.6.24-19-generic #1)
[  121.623783] Process modprobe (pid: 6257, ti=f6806000 task=f6890b80 task.ti=f6806000)
[  121.626005]  [<f8e59fe4>] mp_init+0xa4/0x1f0 [ndiswrapper]
[  121.626053]  [<f8e5a209>] NdisDispatchPnp+0xd9/0xfc0 [ndiswrapper]
[  121.626194]  [<f8e53521>] IoAllocateIrp+0x61/0x80 [ndiswrapper]
[  121.626235]  [<f8e4f604>] get_current_nt_thread+0x44/0x50 [ndiswrapper]
[  121.626269]  [<f8e53815>] IofCallDriver+0x55/0xc0 [ndiswrapper]
[  121.626307]  [<f8e5885b>] IoSendIrpTopDev+0xbb/0x120 [ndiswrapper]
[  121.626360]  [<f8e58bb0>] pnp_start_device+0x50/0xb0 [ndiswrapper]
[  121.626417]  [<f8e58e4f>] wrap_pnp_start_device+0x23f/0x290 [ndiswrapper]
[  121.626471]  [<f8e58ee5>] wrap_pnp_start_pci_device+0x45/0x50 [ndiswrapper]
[  121.626655]  [<f8e483f2>] loader_init+0x82/0x140 [ndiswrapper]
[  121.626676]  [<f8e5523f>] wrap_procfs_init+0x3f/0xb0 [ndiswrapper]
[  121.626694]  [<f8e592f5>] wrapndis_init+0x45/0x50 [ndiswrapper]
[  121.626717]  [<f8dbe0b7>] wrapper_init+0xb7/0xc2 [ndiswrapper]

```

Kubuntu is playing with my feelings :(, any idea? Thanks!

---

### Post by caljohnsmith on 2008-10-03
> **Silenc3 said:**
> 
```
root@Testbox:~$ dmesg | grep -e ndiswrapper -e wlan0 -e error -e warning -e modprobe
[   34.404612] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[  121.552516] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  121.622570] ndiswrapper: driver cb55n51 (Marvell,04/16/2005,2.0.0.16) loaded
[  121.623690] Modules linked in: ndiswrapper rfcomm l2cap bluetooth ppdev acpi_cpufreq cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table video output container sbs sbshc dock battery iptable_filter ip_tables x_tables aes_i586 dm_crypt dm_mod ac lp zc0301 saa7134_alsa snd_pcm_oss snd_mixer_oss snd_pcm gspca snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore agpgart snd_page_alloc saa7134 compat_ioctl32 videobuf_dma_sg videobuf_core ir_kbd_i2c psmouse i2c_core ir_common serio_raw videodev v4l2_common v4l1_compat button parport_pc parport evdev iTCO_wdt iTCO_vendor_support pcspkr shpchp pci_hotplug reiserfs sr_mod cdrom sg sd_mod ata_piix ata_generic usb_storage libusual floppy skge pata_acpi pata_it821x sata_sil24 ehci_hcd uhci_hcd usbcore libata scsi_mod e1000 thermal processor fan fbcon tileblit font bitblit softcursor fuse
[COLOR="Red"][  121.623764] Pid: 6257, comm: modprobe Tainted: P        (2.6.24-19-generic #1)[/COLOR]
[  121.623783] Process modprobe (pid: 6257, ti=f6806000 task=f6890b80 task.ti=f6806000)
[  121.626005]  [<f8e59fe4>] mp_init+0xa4/0x1f0 [ndiswrapper]
[  121.626053]  [<f8e5a209>] NdisDispatchPnp+0xd9/0xfc0 [ndiswrapper]
[  121.626194]  [<f8e53521>] IoAllocateIrp+0x61/0x80 [ndiswrapper]
[  121.626235]  [<f8e4f604>] get_current_nt_thread+0x44/0x50 [ndiswrapper]
[  121.626269]  [<f8e53815>] IofCallDriver+0x55/0xc0 [ndiswrapper]
[  121.626307]  [<f8e5885b>] IoSendIrpTopDev+0xbb/0x120 [ndiswrapper]
[  121.626360]  [<f8e58bb0>] pnp_start_device+0x50/0xb0 [ndiswrapper]
[  121.626417]  [<f8e58e4f>] wrap_pnp_start_device+0x23f/0x290 [ndiswrapper]
[  121.626471]  [<f8e58ee5>] wrap_pnp_start_pci_device+0x45/0x50 [ndiswrapper]
[  121.626655]  [<f8e483f2>] loader_init+0x82/0x140 [ndiswrapper]
[  121.626676]  [<f8e5523f>] wrap_procfs_init+0x3f/0xb0 [ndiswrapper]
[  121.626694]  [<f8e592f5>] wrapndis_init+0x45/0x50 [ndiswrapper]
[  121.626717]  [<f8dbe0b7>] wrapper_init+0xb7/0xc2 [ndiswrapper]

```

The above "modprobe tainted" line looks suspicious; I've never seen that before, but it doesn't sound good. How about reinstalling the modprobe package and seeing if that makes any difference:
```
sudo apt-get purge module-init-tools
sudo apt-get install module-init-tools
```
Reboot, and let me know what happens. If you get any errors be sure to post them, or post again the output of that dmesg command.

---

