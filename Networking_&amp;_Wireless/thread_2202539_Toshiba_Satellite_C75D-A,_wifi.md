---
title: "Toshiba Satellite C75D-A, wifi"
date: 2014-01-29
forum: Networking &amp; Wireless
---

### Post by sergulath on 2014-01-29
Hello I have a Toshiba Satellite C75D-A laptop, It came with windows 8 installed and I installed Ubuntu 12.04 onto it.  Wired with ethernet works but I cant seem to get the wireless to work.  I dont even know where to start to check for what driver I need or anything.  Help me please, I am a complete beginner to linux and my friend introduced me but he is no where to help me.  Please give me steps to follow I will post everything I do.  Thank you in advanced!

---

### Post by chili555 on 2014-01-29
First, let's identify your wireless device. Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn | grep 0280
```That funny pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by sergulath on 2014-01-29
Thank you Chili I been seeing you help alot of people with this problem.  Here are my results..

justin@justin-pc:~$ lspci -nn | grep 0280
05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8179] (rev 01)

So should I now google Realtek Semiconductor driver for wifi?

---

### Post by chili555 on 2014-01-29
> So should I now google Realtek Semiconductor driver for wifi? If you'd like to be self-reliant, I suggest you Google the pci.id 10ec:8179 ubuntu 12.04.

I shall stand by...


------------

Hint:  [http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281](http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281)

---

### Post by sergulath on 2014-01-29
> **chili555 said:**
> If you'd like to be self-reliant, I suggest you Google the pci.id 10ec:8179 ubuntu 12.04.

I shall stand by...


------------

Hint:  [http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281](http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281)

Well I am self-reliant but however lazy to this kind of stuff.  I do want to learn so I can help others as well, if you'd like I will follow your steps to resolve.  That link you had seems to be for 13.04 but does it matter or are the drivers similar?

---

### Post by chili555 on 2014-01-29
I'm 98% sure it will compile just fine. If you get no errors at 'make,' you are home free.

---

### Post by sergulath on 2014-01-29
**Update: **I seemed to get it working however, it flashes wireless connections then went away.  Now its all grey: Wireless Networks, Wireless Is Disabled By Hardware Switch, And Enable Wireless is grey and unclickable.  If it is the wireless hardware switch I tried to press it but nothing I tried the following combinations. 

FN + Switch (f12), ALT + (f12), CTRL + ALT + (f12) nothing works to enable it.. im looking in my bios right after I post this.

I ran these commands:

rfkill ublock all
rfkill list all

And I got this:
[B]justin@justin-pc:~$ rfkill unblock all
justin@justin-pc:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes[/B]

---

### Post by chili555 on 2014-01-29
>  im looking in my bios right after I post this. Please do. Also look all around for a hardware switch. Then post:```
rfkill list all
```

---

### Post by sergulath on 2014-01-29
I ran these commands:

rfkill ublock all
rfkill list all

And I got this:
[B]justin@justin-pc:~$ rfkill unblock all
justin@justin-pc:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes[/B]

---

### Post by chili555 on 2014-01-29
And when you manipulate the wireless button F12, without Alt or Fn, and run the command again, does anything change?

---

### Post by sergulath on 2014-01-29
> **chili555 said:**
> And when you manipulate the wireless button F12, without Alt or Fn, and run the command again, does anything change?

No It stays the same.

---

### Post by chili555 on 2014-01-29
Please try:```
sudo modprobe toshiba_acpi
```Let's see if any errors or clues pop up:```
sudo rfkill unblock all
rfkill list all
dmesg | grep -i acpi
```

---

### Post by sergulath on 2014-01-29
> **chili555 said:**
> Please try:```
sudo modprobe toshiba_acpi
```Let's see if any errors or clues pop up:```
sudo rfkill unblock all
rfkill list all
dmesg | grep -i acpi
```

I did as you asked and I got this.

[B]justin@justin-pc:~$ sudo modprobe toshiba_acpi
[sudo] password for justin: 
justin@justin-pc:~$ sudo rfkill unblock all
justin@justin-pc:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
justin@justin-pc:~$ dmesg | grep -i acpi
[    0.000000] BIOS-e820: [mem 0x00000000bf9ff000-0x00000000bfafefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bfaff000-0x00000000bfbfefff] ACPI data
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 TOSQCI)
[    0.000000] ACPI: XSDT 00000000bfbfe120 000BC (v01 TOSQCI TOSQCI00 00000001      01000013)
[    0.000000] ACPI: FACP 00000000bfbfc000 0010C (v05 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: DSDT 00000000bfbea000 0D5CD (v01 TOSQCI TOSQCI00 F0000000 ACPI 00040000)
[    0.000000] ACPI: FACS 00000000bfaa8000 00040
[    0.000000] ACPI: UEFI 00000000bfbfd000 00236 (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: HPET 00000000bfbfb000 00038 (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: APIC 00000000bfbfa000 00090 (v03 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: MCFG 00000000bfbf9000 0003C (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: ASF! 00000000bfbf8000 000A5 (v32 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: BOOT 00000000bfbe9000 00028 (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: SLIC 00000000bfbe8000 00176 (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: WDRT 00000000bfbe7000 00047 (v01 TOSQCI TOSQCI00 00000000 ACPI 00040000)
[    0.000000] ACPI: WDAT 00000000bfbe6000 001AC (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: FPDT 00000000bfbe4000 00044 (v01 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: MSDM 00000000bfbe3000 00055 (v03 TOSQCI TOSQCI00 00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000bfbe2000 00CB4 (v01 AMD    AGESA    00000001 AMD  00000001)
[    0.000000] ACPI: SSDT 00000000bfbdd000 046B7 (v02 AMD    AGESA    00000002 MSFT 04000000)
[    0.000000] ACPI: SSDT 00000000bfbdc000 00141 (v01    AMD    CPMEC 00000001 INTL 20111123)
[    0.000000] ACPI: SSDT 00000000bfbda000 013CA (v01    AMD CPMDFIGP 00000001 INTL 20111123)
[    0.000000] ACPI: SSDT 00000000bfbd9000 006C1 (v01    AMD CPMADPS4 00000001 INTL 20111123)
[    0.000000] ACPI: SSDT 00000000bfbd8000 00D4E (v01    AMD CPMZPODD 00000001 INTL 20111123)
[    0.000000] ACPI: SSDT 00000000bfbd6000 010C2 (v01    AMD   CPMCMN 00000001 INTL 20111123)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: IOAPIC (id[0x05] address[0xfec01000] gsi_base[24])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10228210 base: 0xfed00000
[    0.009546] ACPI: Core revision 20121018
[    0.009733] ACPI: Forced DSDT copy: length 0x0D5CD copied locally, original unmapped
[    0.253442] PM: Registering ACPI NVS region [mem 0xbf9ff000-0xbfafefff] (1048576 bytes)
[    0.255407] ACPI: bus type pci registered
[    0.263191] ACPI: Added _OSI(Module Device)
[    0.263194] ACPI: Added _OSI(Processor Device)
[    0.263197] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.263202] ACPI: Added _OSI(Processor Aggregator Device)
[    0.266016] ACPI: EC: Look up EC in DSDT
[    0.320727] ACPI: Executed 1 blocks of module-level executable AML code
[    0.328607] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.331232] ACPI: Interpreter enabled
[    0.331241] ACPI: (supports S0 S3 S4 S5)
[    0.331270] ACPI: Using IOAPIC for interrupt routing
[    0.339102] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.340412] ACPI: No dock devices found.
[    0.340420] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.340676] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.340680] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.387462] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.GPP0._PRT]
[    0.387565] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.GPP1._PRT]
[    0.387830]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.388038]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.389503] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.389612] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.389717] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.389821] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.389906] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.389969] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.390031] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.390092] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.390640] ACPI: bus type scsi registered
[    0.390785] ACPI: bus type usb registered
[    0.391052] PCI: Using ACPI for IRQ routing
[    0.403454] pnp: PnP ACPI init
[    0.403477] ACPI: bus type pnp registered
[    0.403717] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.403913] pnp 00:01: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.404043] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.404089] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.404164] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.404203] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.404297] pnp 00:06: Plug and Play ACPI device, IDs TOS1102 PNP0303 (active)
[    0.404361] pnp 00:07: Plug and Play ACPI device, IDs TOS0320 SYN1000 SYN0002 PNP0f13 (active)
[    0.404569] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.404689] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.405751] pnp: PnP ACPI: found 10 devices
[    0.405755] ACPI: ACPI bus type pnp unregistered
[    1.938858] ACPI: AC Adapter [ACAD] (on-line)
[    1.939035] ACPI: Power Button [PWRB]
[    1.939156] ACPI: Lid Switch [LID]
[    1.939212] ACPI: Power Button [PWRF]
[    1.939284] ACPI: acpi_idle registered with cpuidle
[    1.949533] ACPI: Thermal Zone [THRM] (55 C)
[    2.116977] powernow-k8: this CPU is not supported anymore, using acpi-cpufreq instead.
[    2.118451] acpi-cpufreq: overriding BIOS provided _PSD data
[    2.312169] ACPI: Battery Slot [BAT1] (battery present)
[    8.440760] acpi device:00: registered as cooling_device4
[    8.440790] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    8.674510] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \_SB_.PCI0.SMBS.SMB0 1 (20121018/utaddress-251)
[    8.674523] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.693546] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19
justin@justin-pc:~$ 
[/B]

---

### Post by chili555 on 2014-01-30
The purpose of toshiba_acpi is to translate key presses, F12, for example, into action,'turn on the wireless, please.' It is evidently not working, because, it seems, you press the button and nothing changes. The light doesn't light and *rfkill* doesn't change. 

I was interested in this:> [ [COLOR="#FF0000"]8.693546[/COLOR]] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19By the timestamp, it appears that the module toshiba_acpi was loaded during the boot process already, and not as a result of your modprobe. You can verify this by rebooting and checking:```
lsmod
```Is it there? I wonder if *removing* it will help us:```
sudo modprobe -rf toshiba_acpi
sudo rfkill unblock all
rfkill list all
```By the way, when you put these entries in your reply, instead of highlighting the text and clicking bold **B**,instead click the code block: **#**.

---

### Post by sergulath on 2014-01-30
After lsmod: 

```
justin@justin-pc:~$ lsmod
Module                  Size  Used by
bnep                   18258  2 
rfcomm                 47864  0 
bluetooth             247024  10 bnep,rfcomm
vesafb                 13876  1 
parport_pc             28284  0 
ppdev                  17113  0 
uvcvideo               82214  0 
binfmt_misc            17540  1 
videobuf2_core         40785  1 uvcvideo
videodev              130053  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
kvm_amd                60205  0 
joydev                 17613  0 
arc4                   12573  2 
kvm                   455932  1 kvm_amd
fglrx                5294837  140 
ghash_clmulni_intel    13259  0 
snd_hda_codec_conexant    62464  1 
aesni_intel            55495  0 
ablk_helper            13597  1 aesni_intel
cryptd                 20501  3 ghash_clmulni_intel,aesni_intel,ablk_helper
lrw                    13294  1 aesni_intel
aes_x86_64             17255  1 aesni_intel
snd_hda_codec_hdmi     37434  1 
rtl8188ee             137586  0 
snd_hda_intel          44339  5 
snd_hda_codec         141716  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
rtlwifi               120562  1 rtl8188ee
xts                    12922  1 aesni_intel
gf128mul               14951  2 lrw,xts
snd_hwdep              13668  1 snd_hda_codec
mac80211              550919  2 rtl8188ee,rtlwifi
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
toshiba_acpi           18774  0 
cfg80211              549566  2 rtlwifi,mac80211
psmouse                97873  0 
sparse_keymap          13890  1 toshiba_acpi
microcode              23017  0 
wmi                    19256  1 toshiba_acpi
snd                    69533  20 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13215  0 
soundcore              12680  1 snd
alx                    73230  0 
fam15h_power           13166  0 
amd_iommu_v2           19198  1 fglrx
mac_hid                13253  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
i2c_piix4              13459  0 
mdio                   13807  1 alx
compat                 15085  4 rtl8188ee,rtlwifi,mac80211,cfg80211
video                  19652  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   25879  2 
libahci                31606  1 ahci


```

after I tried this

```
sudo modprobe -rf toshiba_acpi
sudo rfkill unblock all
rfkill list all
```

I got tis

```
justin@justin-pc:~$ sudo modprobe -rf toshiba_acpi
[sudo] password for justin: 
justin@justin-pc:~$ sudo rfkill unblock all
justin@justin-pc:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
justin@justin-pc:~$ 


```

---

### Post by chili555 on 2014-01-30
I really haven't anything further to suggest. It won't work *with* toshiba_acpi; it won't work *without* toshiba_acpi; it won't work with rfkill unblock all. 

I suggest you file a bug against toshiba_acpi here: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

Last, I'd look for a USB wireless until this gets sorted out.

I'm sorry I have no other ideas.

---

### Post by sergulath on 2014-01-30
Its okay, I will most definitely file a bug report.  Thank you so much for helping!

---

