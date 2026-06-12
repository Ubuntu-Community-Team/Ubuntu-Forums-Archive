---
title: "I can't access the networking option"
date: 2005-06-17
forum: Networking &amp; Wireless
---

### Post by FireFusion on 2005-06-17
Under System -> Administration -> Networking

I keep tring to select it, it looks like it's loading and then nothing comes up. Help please. Anything to do with Networking doesn't seem to want to load. I even tried the Ubuntu device database and it seems to hang when it gets to the network test.

By the way i've got a Netgear WG111T USB wireless conector. Any chance of get that working?

If not I have a have an inbulit Dell one and a standard network port and router, so i'm sure I should be able to get one of them working.

---

### Post by intangible on 2005-06-17
[QUOTE=FireFusion]Under System -> Administration -> Networking

I keep tring to select it, it looks like it's loading and then nothing comes up. Help please. Anything to do with Networking doesn't seem to want to load. I even tried the Ubuntu device database and it seems to hang when it gets to the network test.

By the way i've got a Netgear WG111T USB wireless conector. Any chance of get that working?

If not I have a have an inbulit Dell one and a standard network port and router, so i'm sure I should be able to get one of them working.[/QUOTE]
 The atheros chip in that Netgear device is supported by the madwifi module (ath_pci in Ubuntu it seems), but I don't any experience using USB wireless devices in Ubuntu.  Make sure you have **linux-restricted-modules-386 (the one for your kernel)** installed, and then try **sudo modprobe ath_hal; sudo modprobe ath_pci**.

Also, does lspci show your onboard networking?  Do you know what network chip the computer has, if not, what model Dell do you have?

---

### Post by FireFusion on 2005-06-18
I've got an Inspiron 1150. I think the network connector is a broadcom something. Btw i'm a super newb to Linux so you'll have to explain in a little bit more detail.

---

### Post by FireFusion on 2005-06-18
I've working it out. Any program or utility that will ask me for a password won't load on my laptop. Maybe my user account doesn't have the right permissions or something (even though it's the default account I set up during the install. 

The one on my home PC (which i'm using now) works fine.

---

### Post by FireFusion on 2005-06-20
Anyone?

---

### Post by intangible on 2005-06-20
First thing we need to do is verify that your sudo is working properly...

If you open a terminal and type **sudo -s** does it change your prompt from**$** to **#** ?

Also, Broadcom wireless chips are poorly supported, the manufacturer won't realease the specs to anyone to produce linux drivers so we're stuck having to do a wierd "wrap" around the windows ones.  Here's some more info on that process: [https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

But, if I was you, I would just use the wired interface for simplicity to make sure everything is working first.  Plug in the network cable, then goto **System->Administration->Networking** and deactivate then activate the wired connection and see if you get internet connectivity up that way.

---

### Post by FireFusion on 2005-06-20
Hi intangible,

Okay, Sudo most certainly isn't working. It just returns an error about a file not existing or being unable to access. I'm pretty sure something went wrong during install, how do I repair this?

Also the wireless card is not Broadcom, the network socket on my laptop is.

---

### Post by intangible on 2005-06-20
What is the error message exactly?

Do you have anything on there yet that you can't save?  An install over the top would probably be the easiest way to get back the missing file, I have no idea why it would be missing any files after a fresh install.

---

### Post by FireFusion on 2005-06-20
Reinstalled and everything is working great! Network is now working great. But i'd still really like to get my wireless Netgear USB working.

---

### Post by intangible on 2005-06-20
When you plug in the Netgear USB adapter, what does **lsusb** show?

Unplug the usb device, wait about 10 seconds, then plug it in, then give me the output from these commands:
**dmesg|tail**
**lsusb**
**ifconfig**
**lsmod**

---

### Post by FireFusion on 2005-06-30
fire@ubuntu-earth:~$ dmesg|tail
[drm] Initialized i915 1.2.0 20040405 on minor 1: Intel Corp. 82852/855GM Integr ated Graphics Device (#2)
mtrr: base(0xe8020000) is not aligned on a size(0x300000) boundary
cs: IO port probe 0x0100-0x04ff: clean.
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
eth0: no IPv6 routers present
usb 4-3: new high speed USB device using ehci_hcd and address 3
usb 4-3: USB disconnect, address 3
usb 4-3: new high speed USB device using ehci_hcd and address 4
fire@ubuntu-earth:~$ lsusb
Bus 004 Device 004: ID 1385:4251
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 413c:3010 Dell Computer Corp.
Bus 001 Device 001: ID 0000:0000
fire@ubuntu-earth:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:1F:24:EF:47
          inet addr:10.0.0.4  Bcast:255.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20f:1fff:fe24:ef47/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:944 errors:0 dropped:0 overruns:0 frame:0
          TX packets:840 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1132808 (1.0 MiB)  TX bytes:133762 (130.6 KiB)
          Interrupt:7

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:400726 (391.3 KiB)  TX bytes:400726 (391.3 KiB)

fire@ubuntu-earth:~$ lsmod
Module                  Size  Used by
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
pcmcia                 21380  2
i915                   18304  1
drm                    59412  2 i915
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  9
af_packet              20744  2
yenta_socket           19584  0
pcmcia_core            53568  2 pcmcia,yenta_socket
b44                    20356  0
mii                     4736  1 b44
snd_intel8x0           29984  1
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixe r_oss,snd_pcm,snd_timer
soundcore               9824  2 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
hw_random               5524  0
pci_hotplug            30512  0
usbhid                 29376  0
ehci_hcd               29444  0
uhci_hcd               30224  0
usbcore               107384  4 usbhid,ehci_hcd,uhci_hcd
intel_agp              20636  1
agpgart                31784  3 drm,intel_agp
pcspkr                  3816  0
rtc                    12216  0
nls_cp437               5888  2
ntfs                   97136  2
md                     43856  0
evdev                   9088  1
joydev                  9408  0
dm_mod                 53116  1
tsdev                   7488  0
capability              5000  0
commoncap               7808  1 capability
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  0
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  5
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  726
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

---

### Post by skippuff54 on 2005-07-03
listen, i'm drunk and happy fourth of july.

the netgear will use the madwifi drivers and that can be found here [http://sourceforge.net/projects/madwifi/](http://) 

you can use synaptic to update the drivers, and one thing i read earlier was about the linux-restriced module.  i went ahead and uninstalled that module, then downloaded the madwifi driver by itself.  that worked after i updated the path from wherever it was installed through stock installation to wherever it installed when i downloaded just the madwifi driver.

i'm not using usb, i'm using pci, the netgear WG311T.  the madwifi drivers works once you get all the configuration settings right.

---

