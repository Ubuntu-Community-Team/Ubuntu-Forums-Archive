---
title: "ndiswrapper netgear ma311 pci card"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by xnszxdotnet on 2006-11-21
Im running ubuntu 6.10
I installed ndiswrapper and my drivers for my netgear ma311 pci card. 
I followed this guide here:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

everything seemed to work just fine till I got to the last couple of steps:

> 
sudo iwconfig wlan0 essid "AP" key ababababababababab mode Managed
iwconfig


I'm lost to what to do. I got an error that says:

> 
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.


can anyone help me??

thanx

---

### Post by FrodoB on 2006-11-21
The key to a successful ndiswrapper installation is getting a source for the NDIS files that will work with your device. Also upgrading to the latest version of ndiswrapper can sometimes be all it takes to be successful.  Here are some installs for other devices:


Broadcom bcm4311:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

Linksys WUSB11v4:
[https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

Netgear WG121:
[https://help.ubuntu.com/community/WifiDocs/Device/WG121?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/WG121?highlight=%28WifiDocs%2FDevice%29)

You should look on the ndiswrapper site for information on successful installs with you device:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#N](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#N)

Also, according to the ndiswrapper site the ma311 is a prism chipset card, have you looked at the output of iwconfig in a terminal to see if the card has been recognized?

---

### Post by FrodoB on 2006-11-21
Install the pcmcia-cs package and run the cardctl ident command and publish the output

sudo apt-get  update 
sudo apt-get install pcmcia-cs

sudo cardctl ident


The identifier will tell us what chipset you really have.

---

### Post by FrodoB on 2006-11-21
If it is a prism chipset card it should just work out of the box.

---

### Post by xnszxdotnet on 2006-11-21
iwconfig shows

> 
lo        no wireless extensions.

wlan0     no wireless extensions.

sit0      no wireless extensions.


I installed the winXP drivers start from Netgear's site. I take it that something isn't set right??

ndiswrapper -l shows:
> 
Installed drivers:
netma311                driver installed, hardware present


what gives??

---

### Post by FrodoB on 2006-11-21
I don't know yet.  Get the ident as described above and we shall see what we really have here.

---

### Post by xnszxdotnet on 2006-11-21
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pcmcia-cs

---

### Post by FrodoB on 2006-11-22
Here is the procedure for getting cardctl ident working:

Uncomment the following lines in /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

and 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe



To edit the file issue these commands at a terminal prompt:

sudo gedit /etc/apt/sources.list

Save the changes.



Update the apt databases so your system can see the new packages:

$ sudo apt-get update



Install the pcmcia-cs package:

$ sudo apt-get install pcmcia-cs



Get the identifier for your PC Card or PCMCIA device to report back to the forum:

$ cardctl ident

---

### Post by xnszxdotnet on 2006-11-22
I'm still getting the error:
> 
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package pcmcia-cs


isn't there a way to have it look at the install disc from source.list??

---

### Post by FrodoB on 2006-11-22
It may, but I have not had time to work on that.  The symptom is like you forgot to run:

$ sudo apt-get update

If that does not work, just uncomment every commented line in sources.list and then run:

$ sudo apt-get update

then try to install pcmcia-cs, etc.

---

### Post by xnszxdotnet on 2006-11-22
I uncommented everything and got the same error.
](*,)

---

### Post by FrodoB on 2006-11-22
And did you successfully run:

sudo apt-get update

afterwards, or did it give you errors?

---

### Post by xnszxdotnet on 2006-11-22
yeah, alot.

> 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
  Temporary failure resolving 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
  Temporary failure resolving 'security.ubuntu.com'
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg
  Temporary failure resolving 'www.getautomatix.com'
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US
  Temporary failure resolving 'www.getautomatix.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
  Temporary failure resolving 'us.archive.ubuntu.com'
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/restricted Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/restricted Translation-en_US
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/i18n/Translation-en_US.bz2)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/Release.gpg](http://www.getautomatix.com/apt/dists/edgy/Release.gpg)  Temporary failure resolving 'www.getautomatix.com'
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2](http://www.getautomatix.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2)  Temporary failure resolving 'www.getautomatix.com'
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by FrodoB on 2006-11-22
Well, that is the problem, you have no internet connection at all.

---

### Post by FrodoB on 2006-11-22
I will try to find it on the CD.

---

### Post by xnszxdotnet on 2006-11-22
well, yeah that is why I'm trying to get ndiswrapper and my netgear ma311 working.

---

### Post by FrodoB on 2006-11-22
Try 
pccardctl ident

---

### Post by xnszxdotnet on 2006-11-22
tryed pccardctl ident and got no resolts

tryed apt-get install pccardctl and got:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pccardctl

---

### Post by FrodoB on 2006-11-22
At this point it does not seem like you will get to run cardctl ident, so take a look at these detailed instructions for the WG121 and see it these can tell you what you need to do to get it going.  Obviously your drivers are named differently.

---

### Post by FrodoB on 2006-11-22
What is the output of lspci?

lspci

---

### Post by xnszxdotnet on 2006-11-22
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0d.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
00:0e.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
00:0f.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
00:10.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 15)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RL/VR AGP
02:08.0 USB Controller: NEC Corporation USB (rev 41)
02:08.1 USB Controller: NEC Corporation USB (rev 41)
02:08.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
02:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by FrodoB on 2006-11-22
00:0d.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)

This should just work.  Provide the output of lsmod in your post.

Have you blacklisted any drivers for your ndiswrapper setup?

---

### Post by xnszxdotnet on 2006-11-22
lsmod
> Module                  Size  Used by
ndiswrapper           208656  0 
nls_utf8                3200  0 
vfat                   14720  0 
fat                    56348  1 vfat
sg                     37404  0 
sd_mod                 22656  0 
usb_storage            75072  0 
libusual               17040  1 usb_storage
nls_cp437               6912  0 
isofs                  38076  0 
udf                    89348  0 
ipv6                  272288  8 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
apm                    23280  1 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
af_packet              24584  0 
sbp2                   24584  0 
scsi_mod              144648  4 sg,sd_mod,usb_storage,sbp2
lp                     12964  0 
tsdev                   9152  0 
floppy                 63044  0 
pcspkr                  4352  0 
evdev                  11392  3 
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
psmouse                41352  0 
serio_raw               8452  0 
snd_ens1371            28704  1 
gameport               17160  1 snd_ens1371
hostap_pci             59152  0 
hostap                123012  1 hostap_pci
snd_rawmidi            27264  1 snd_ens1371
snd_seq_device          9868  1 snd_rawmidi
snd_ac97_codec         97696  1 snd_ens1371
snd_ac97_bus            3456  1 snd_ac97_codec
ieee80211_crypt         7552  1 hostap
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
orinoco_pci             8320  0 
orinoco                45076  1 orinoco_pci
hermes                  9472  2 orinoco_pci,orinoco
snd_pcm                84612  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
i2c_piix4              10000  0 
prism2_pci             74752  0 
intel_agp              26012  1 
agpgart                34888  1 intel_agp
i2c_core               23424  1 i2c_piix4
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
snd                    58372  10 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  1 snd_pcm
ext3                  142728  1 
jbd                    62228  1 ext3
usbhid                 45152  0 
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ehci_hcd               34696  0 
ohci_hcd               22532  0 
uhci_hcd               24968  0 
usbcore               134912  8 ndiswrapper,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  3 
piix                   11780  1 
generic                 5764  0 
processor              31560  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability


no blacklist, I don't even know how to do that.

---

### Post by FrodoB on 2006-11-22
Ok, you have multiple drivers that think they own this card. You need to blacklist at least the following:

# Blacklisted to get prism chipset detected
blacklist orinoco
blacklist orinoco_pci
blacklist hermes
blacklist ndiswrapper

Edit the blacklist file:

$ sudo gedit /etc/modprobe.d/blacklist

add the above blacklist lines to the end and reboot.

Check the output of iwconfig and post it.

Also look into the dmesg output and see if you can find the section where the prism driver loads and post it as well.

---

### Post by xnszxdotnet on 2006-11-22
iwconfig
> lo        no wireless extensions.

wlan0     no wireless extensions.

sit0      no wireless extensions.


dmesg

> 
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 00000000040fd800 (usable)
[17179569.184000]  BIOS-e820: 00000000040fd800 - 00000000040ff800 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000040ff800 - 00000000040ffc00 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000040ffc00 - 0000000014000000 (usable)
[17179569.184000]  BIOS-e820: 00000000fffe7000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 320MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 81920
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 77824 pages, LIFO batch:15
[17179569.184000] DMI 2.1 present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6ac0
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x00000000 PTL  0x01000000) @ 0x040fda87
[17179569.184000] ACPI: FADT (v001 GATEWA TABOR II 0x19990422 PTL  0x000f4240) @ 0x040ff78c
[17179569.184000] ACPI: DSDT (v001 GATEWA TABOR II 0x00000000 MSFT 0x01000000) @ 0x00000000
[17179569.184000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[17179569.184000] ACPI: Disabling ACPI support
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 14000000:ebfe7000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (0128a000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 448.107 MHz processor.
[   40.157873] Using tsc for high-res timesource
[   40.159237] Console: colour VGA+ 80x25
[   40.160470] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   40.161718] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   40.212649] Memory: 315112k/327680k available (1910k kernel code, 11996k reserved, 1070k data, 308k init, 0k highmem)
[   40.212667] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   40.289716] Calibrating delay using timer specific routine.. 897.67 BogoMIPS (lpj=1795354)
[   40.289879] Security Framework v1.0.0 initialized
[   40.289908] SELinux:  Disabled at boot.
[   40.289975] Mount-cache hash table entries: 512
[   40.290499] CPU: After generic identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   40.290532] CPU: After vendor identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   40.290571] CPU: L1 I cache: 16K, L1 D cache: 16K
[   40.290583] CPU: L2 cache: 512K
[   40.290593] CPU serial number disabled.
[   40.290603] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   40.290682] Checking 'hlt' instruction... OK.
[   40.305959] SMP alternatives: switching to UP code
[   40.306377] Freeing SMP alternatives: 16k freed
[   40.306855] checking if image is initramfs... it is
[   42.411337] Freeing initrd memory: 5254k freed
[   42.411363] CPU0: Intel Pentium III (Katmai) stepping 03
[   42.411387] SMP motherboard not detected.
[   42.411398] Local APIC not detected. Using dummy APIC emulation.
[   42.411678] Brought up 1 CPUs
[   42.411757] migration_cost=0
[   42.412988] NET: Registered protocol family 16
[   42.413126] EISA bus registered
[   42.413657] PCI: PCI BIOS revision 2.10 entry at 0xfd983, last bus=2
[   42.413681] PCI: Using configuration type 1
[   42.413690] Setting up standard PCI resources
[   42.415600] ACPI: Interpreter disabled.
[   42.415620] Linux Plug and Play Support v0.97 (c) Adam Belay
[   42.415652] pnp: PnP ACPI: disabled
[   42.415666] PnPBIOS: Scanning system for PnP BIOS support...
[   42.415722] PnPBIOS: Found PnP BIOS installation structure at 0xc00f6ae0
[   42.415738] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x9e31, dseg 0x400
[   42.425633] PnPBIOS: 18 nodes reported by PnP BIOS; 18 recorded by driver
[   42.425851] PCI: Probing PCI hardware
[   42.425867] PCI: Probing PCI hardware (bus 00)
[   42.426329] PCI: Ignoring BAR0-3 of IDE controller 0000:00:07.1
[   42.426487] PCI quirk: region 8000-803f claimed by PIIX4 ACPI
[   42.426501] PCI quirk: region 7000-700f claimed by PIIX4 SMB
[   42.427169] Boot video device is 0000:01:00.0
[   42.431234] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
[   42.436924] pnp: 00:00: ioport range 0x370-0x371 has been reserved
[   42.436979] pnp: 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   42.436993] pnp: 00:0a: ioport range 0x8000-0x803f has been reserved
[   42.437007] pnp: 00:0a: ioport range 0x7000-0x700f has been reserved
[   42.438180] PCI: Bridge: 0000:00:01.0
[   42.438195]   IO window: 9000-9fff
[   42.438210]   MEM window: ec000000-ec0fffff
[   42.438223]   PREFETCH window: f8000000-fbffffff
[   42.438238] PCI: Bridge: 0000:00:10.0
[   42.438245]   IO window: disabled.
[   42.438259]   MEM window: ec100000-ec1fffff
[   42.438269]   PREFETCH window: disabled.
[   42.438392] NET: Registered protocol family 2
[   42.473737] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   42.474175] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   42.474741] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   42.475032] TCP: Hash tables configured (established 16384 bind 8192)
[   42.475045] TCP reno registered
[   42.478290] audit: initializing netlink socket (disabled)
[   42.478343] audit(1164226485.508:1): initialized
[   42.478929] VFS: Disk quotas dquot_6.5.1
[   42.479017] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   42.479236] Initializing Cryptographic API
[   42.479257] io scheduler noop registered
[   42.479289] io scheduler anticipatory registered
[   42.479317] io scheduler deadline registered
[   42.479374] io scheduler cfq registered (default)
[   42.479394] Limiting direct PCI/PCI transfers.
[   42.480357] isapnp: Scanning for PnP cards...
[   42.836581] isapnp: No Plug & Play device found
[   42.976485] Real Time Clock Driver v1.12ac
[   42.976802] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   42.977135] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   42.979931] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   42.983505] pnp: Device 00:0f activated.
[   42.983858] 00:0f: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   42.984840] mice: PS/2 mouse device common for all mice
[   42.987965] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   42.988535] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   42.988553] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   42.989259] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   43.005810] serio: i8042 AUX port at 0x60,0x64 irq 12
[   43.007192] serio: i8042 KBD port at 0x60,0x64 irq 1
[   43.009923] EISA: Probing bus 0 at eisa.0
[   43.009950] Cannot allocate resource for EISA slot 1
[   43.009997] Cannot allocate resource for EISA slot 7
[   43.010008] Cannot allocate resource for EISA slot 8
[   43.010017] EISA: Detected 0 cards.
[   43.010357] TCP bic registered
[   43.010394] NET: Registered protocol family 1
[   43.010419] NET: Registered protocol family 8
[   43.010429] NET: Registered protocol family 20
[   43.010514] Using IPI No-Shortcut mode
[   43.011985] Freeing unused kernel memory: 308k freed
[   43.061115] input: AT Translated Set 2 keyboard as /class/input/input0
[   44.433039] Capability LSM initialized
[   46.200309] PIIX4: IDE controller at PCI slot 0000:00:07.1
[   46.200351] PIIX4: chipset revision 1
[   46.200361] PIIX4: not 100% native mode: will probe irqs later
[   46.200386]     ide0: BM-DMA at 0x1000-0x1007, BIOS settings: hda:pio, hdb:DMA
[   46.200424] Probing IDE interface ide0...
[   46.489009] hda: ST380021A, ATA DISK drive
[   47.272896] hdb: PIONEER DVD-RW DVR-108, ATAPI CD/DVD-ROM drive
[   47.329158] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   47.358294] hda: max request size: 128KiB
[   47.399412] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
[   47.399443] hda: cache flushes not supported
[   47.399590]  hda: hda1 hda2 < hda5 >
[   47.521852] hdb: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(33)
[   47.521887] Uniform CD-ROM driver Revision: 3.20
[   47.901808] Probing IDE interface ide1...
[   47.979092] usbcore: registered new driver usbfs
[   47.981217] usbcore: registered new driver hub
[   47.992259] USB Universal Host Controller Interface driver v3.0
[   47.994456] PCI: Found IRQ 9 for device 0000:00:07.2
[   47.994528] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   47.995377] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   47.995436] uhci_hcd 0000:00:07.2: irq 9, io base 0x00001020
[   47.996286] usb usb1: configuration #1 chosen from 1 choice
[   47.996943] hub 1-0:1.0: USB hub found
[   47.996986] hub 1-0:1.0: 2 ports detected
[   48.088172] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   48.176877] ohci_hcd 0000:02:08.0: OHCI Host Controller
[   48.177658] ohci_hcd 0000:02:08.0: new USB bus registered, assigned bus number 2
[   48.177712] ohci_hcd 0000:02:08.0: irq 9, io mem 0xec104000
[   48.757162] ieee1394: Initialized config rom entry `ip1394'
[   48.804822] usb usb2: configuration #1 chosen from 1 choice
[   48.805413] hub 2-0:1.0: USB hub found
[   48.805463] hub 2-0:1.0: 3 ports detected
[   48.896548] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   49.055358] usb 1-1: configuration #1 chosen from 1 choice
[   49.296500] usb 1-2: new low speed USB device using uhci_hcd and address 3
[   49.320823] ehci_hcd 0000:02:08.2: EHCI Host Controller
[   49.320952] ehci_hcd 0000:02:08.2: new USB bus registered, assigned bus number 3
[   49.344531] ehci_hcd 0000:02:08.2: irq 11, io mem 0xec106800
[   49.344551] ehci_hcd 0000:02:08.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[   49.344809] usb usb3: configuration #1 chosen from 1 choice
[   49.344922] hub 3-0:1.0: USB hub found
[   49.344962] hub 3-0:1.0: 5 ports detected
[   49.451054] ohci_hcd 0000:02:08.1: OHCI Host Controller
[   49.451221] ohci_hcd 0000:02:08.1: new USB bus registered, assigned bus number 4
[   49.451270] ohci_hcd 0000:02:08.1: irq 10, io mem 0xec105000
[   50.012231] usb usb4: configuration #1 chosen from 1 choice
[   50.012867] hub 4-0:1.0: USB hub found
[   50.012914] hub 4-0:1.0: 2 ports detected
[   50.049963] usb 1-2: configuration #1 chosen from 1 choice
[   50.529248] usbcore: registered new driver hiddev
[   50.582260] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[9]  MMIO=[ec106000-ec1067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   50.595545] input: HID 0461:4d03 as /class/input/input1
[   50.596129] input: USB HID v1.00 Mouse [HID 0461:4d03] on usb-0000:00:07.2-1
[   50.645893] input:   USB Keyboard as /class/input/input2
[   50.645935] input: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:07.2-2
[   50.734799] input:   USB Keyboard as /class/input/input3
[   50.734841] input: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:07.2-2
[   50.734894] usbcore: registered new driver usbhid
[   50.734909] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   50.946672] Attempting manual resume
[   51.033574] EXT3-fs: INFO: recovery required on readonly filesystem.
[   51.033592] EXT3-fs: write access will be enabled during recovery.
[   51.854681] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[005042b5c00dff24]
[   52.473937] kjournald starting.  Commit interval 5 seconds
[   52.473989] EXT3-fs: recovery complete.
[   52.474953] EXT3-fs: mounted filesystem with ordered data mode.
[   65.309412] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   66.216337] input: PC Speaker as /class/input/input4
[   67.173620] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   67.195742] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   70.187829] Floppy drive(s): fd0 is 1.44M
[   70.205342] FDC 0 is a post-1991 82077
[   71.138456] Linux agpgart interface v0.101 (c) Dave Jones
[   71.403152] pnp: Device 00:14 activated.
[   71.403169] parport: PnPBIOS parport detected.
[   71.403241] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   71.434250] prism2pci_init: prism2_pci.o: 0.2.5 Loaded
[   71.434440] PCI: Enabling device 0000:00:0d.0 (0114 -> 0116)
[   71.434463] PCI: Found IRQ 10 for device 0000:00:0d.0
[   71.434536] A Prism2.5 PCI device found, phymem:0xec200000, irq:10, mem:0xd4990000
[   72.533297] agpgart: Detected an Intel 440BX Chipset.
[   72.540637] agpgart: AGP aperture is 64M @ 0xf0000000
[   72.759231] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   72.859742] orinoco_pci 0.15rc3 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au> & Jean Tourrilhes <jt@hpl.hp.com>)
[   72.952177] PCI: Enabling device 0000:00:0e.0 (0104 -> 0105)
[   72.952203] PCI: Found IRQ 11 for device 0000:00:0e.0
[   72.952241] PCI: Sharing IRQ 11 with 0000:01:00.0
[   73.041541] ieee80211_crypt: registered algorithm 'NULL'
[   73.114580] hostap_pci: 0.4.4-kernel (Jouni Malinen <jkmaline@cc.hut.fi>)
[   75.362005] ts: Compaq touchscreen protocol output
[   76.578100] lp0: using parport0 (interrupt-driven).
[   76.725593] SCSI subsystem initialized
[   76.745899] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   76.745917] ieee1394: sbp2: Try serialize_io=0 for better performance
[   76.837307] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[   77.024701] Adding 939760k swap on /dev/disk/by-uuid/d6a6cd96-ff76-4ed6-9b1e-4d5c171de15c.  Priority:-1 extents:1 across:939760k
[   77.133834] EXT3 FS on hda1, internal journal
[   79.748515] NET: Registered protocol family 17
[   91.138744] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  102.601315] NET: Registered protocol family 10
[  102.601677] lo: Disabled Privacy Extensions
[  102.601998] IPv6 over IPv4 tunneling driver
[  121.268008] Bluetooth: Core ver 2.8
[  121.268030] NET: Registered protocol family 31
[  121.268039] Bluetooth: HCI device and connection manager initialized
[  121.268090] Bluetooth: HCI socket layer initialized
[  121.342291] Bluetooth: L2CAP ver 2.8
[  121.342308] Bluetooth: L2CAP socket layer initialized
[  121.482541] Bluetooth: RFCOMM socket layer initialized
[  121.482592] Bluetooth: RFCOMM TTY layer initialized
[  121.482603] Bluetooth: RFCOMM ver 1.7
[  133.592837] usb 3-3: new high speed USB device using ehci_hcd and address 2
[  133.728936] usb 3-3: configuration #1 chosen from 1 choice
[  134.105092] usbcore: registered new driver libusual
[  134.283979] Initializing USB Mass Storage driver...
[  134.285540] scsi0 : SCSI emulation for USB Mass Storage devices
[  134.287036] usb-storage: device found at 2
[  134.287048] usb-storage: waiting for device to settle before scanning
[  134.287086] usbcore: registered new driver usb-storage
[  134.287100] USB Mass Storage support registered.
[  139.284968] usb-storage: device scan complete
[  139.286324]   Vendor: LEXAR     Model: JUMPDRIVE         Rev: 1000
[  139.286376]   Type:   Direct-Access                      ANSI SCSI revision: 00
[  139.458508] SCSI device sda: 2026592 512-byte hdwr sectors (1038 MB)
[  139.460053] sda: Write Protect is off
[  139.460071] sda: Mode Sense: 43 00 00 00
[  139.460080] sda: assuming drive cache: write through
[  139.468109] SCSI device sda: 2026592 512-byte hdwr sectors (1038 MB)
[  139.473487] sda: Write Protect is off
[  139.473511] sda: Mode Sense: 43 00 00 00
[  139.473521] sda: assuming drive cache: write through
[  139.474211]  sda: sda1
[  139.524800] sd 0:0:0:0: Attached scsi removable disk sda
[  139.730365] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  158.045500] usb 3-3: USB disconnect, address 2
[  161.057038] usb 3-3: new high speed USB device using ehci_hcd and address 3
[  161.192930] usb 3-3: configuration #1 chosen from 1 choice
[  161.193477] scsi1 : SCSI emulation for USB Mass Storage devices
[  161.193848] usb-storage: device found at 3
[  161.193858] usb-storage: waiting for device to settle before scanning
[  166.193102] usb-storage: device scan complete
[  166.194468]   Vendor: LEXAR     Model: JUMPDRIVE         Rev: 1000
[  166.194520]   Type:   Direct-Access                      ANSI SCSI revision: 00
[  166.201401] SCSI device sda: 2026592 512-byte hdwr sectors (1038 MB)
[  166.202486] sda: Write Protect is off
[  166.202501] sda: Mode Sense: 43 00 00 00
[  166.202511] sda: assuming drive cache: write through
[  166.206520] SCSI device sda: 2026592 512-byte hdwr sectors (1038 MB)
[  166.207501] sda: Write Protect is off
[  166.207517] sda: Mode Sense: 43 00 00 00
[  166.207526] sda: assuming drive cache: write through
[  166.207540]  sda: sda1
[  166.255906] sd 1:0:0:0: Attached scsi removable disk sda
[  166.256082] sd 1:0:0:0: Attached scsi generic sg0 type 0
[  184.249871] usb 3-3: USB disconnect, address 3
[  187.765347] usb 3-3: new high speed USB device using ehci_hcd and address 4
[  187.910518] usb 3-3: configuration #1 chosen from 1 choice
[  187.911557] scsi2 : SCSI emulation for USB Mass Storage devices
[  187.911954] usb-storage: device found at 4
[  187.911965] usb-storage: waiting for device to settle before scanning
[  192.909339] usb-storage: device scan complete
[  192.910667]   Vendor:           Model: USB Flash Memory  Rev: 1.04
[  192.910719]   Type:   Direct-Access                      ANSI SCSI revision: 00
[  194.009905] SCSI device sda: 501760 512-byte hdwr sectors (257 MB)
[  194.011020] sda: Write Protect is off
[  194.011035] sda: Mode Sense: 23 00 00 00
[  194.011045] sda: assuming drive cache: write through
[  194.014398] SCSI device sda: 501760 512-byte hdwr sectors (257 MB)
[  194.015342] sda: Write Protect is off
[  194.015358] sda: Mode Sense: 23 00 00 00
[  194.015367] sda: assuming drive cache: write through
[  194.015381]  sda: unknown partition table
[  194.018829] sd 2:0:0:0: Attached scsi removable disk sda
[  194.019013] sd 2:0:0:0: Attached scsi generic sg0 type 0
[  232.815155] usb 3-3: USB disconnect, address 4
[  232.823667]  2:0:0:0: rejecting I/O to dead device
[  232.823988]  2:0:0:0: rejecting I/O to dead device
[  232.824287]  2:0:0:0: rejecting I/O to dead device
[  232.824583]  2:0:0:0: rejecting I/O to dead device
[  232.824870] sda : READ CAPACITY failed.
[  232.824877] sda : status=0, message=00, host=1, driver=00 
[  232.824890] sda : sense not available. 
[  232.825601]  2:0:0:0: rejecting I/O to dead device
[  232.825626] sda: Write Protect is off
[  232.825637] sda: Mode Sense: 00 00 00 00
[  232.825646] sda: assuming drive cache: write through
[  232.825685]  2:0:0:0: rejecting I/O to dead device
[  232.825714]  2:0:0:0: rejecting I/O to dead device
[  232.825741]  2:0:0:0: rejecting I/O to dead device
[  232.825768]  2:0:0:0: rejecting I/O to dead device
[  232.825788] sda : READ CAPACITY failed.
[  232.825793] sda : status=0, message=00, host=1, driver=00 
[  232.825803] sda : sense not available. 
[  232.825824]  2:0:0:0: rejecting I/O to dead device
[  232.825841] sda: Write Protect is off
[  232.825851] sda: Mode Sense: 00 00 00 00
[  232.825859] sda: assuming drive cache: write through
[  232.825878]  sda:<3> 2:0:0:0: rejecting I/O to dead device
[  232.825976] Buffer I/O error on device sda, logical block 0
[  232.826020]  2:0:0:0: rejecting I/O to dead device
[  232.826035] Buffer I/O error on device sda, logical block 0
[  232.826057]  unable to read partition table
[  287.795516] usb 3-3: new high speed USB device using ehci_hcd and address 5
[  287.931978] usb 3-3: configuration #1 chosen from 1 choice
[  287.932525] scsi3 : SCSI emulation for USB Mass Storage devices
[  287.932913] usb-storage: device found at 5
[  287.932924] usb-storage: waiting for device to settle before scanning
[  292.931255] usb-storage: device scan complete
[  292.932603]   Vendor: LEXAR     Model: JUMPDRIVE         Rev: 1000
[  292.932655]   Type:   Direct-Access                      ANSI SCSI revision: 00
[  292.939305] SCSI device sda: 2026592 512-byte hdwr sectors (1038 MB)
[  292.940379] sda: Write Protect is off
[  292.940395] sda: Mode Sense: 43 00 00 00
[  292.940405] sda: assuming drive cache: write through
[  292.944674] SCSI device sda: 2026592 512-byte hdwr sectors (1038 MB)
[  292.945659] sda: Write Protect is off
[  292.945675] sda: Mode Sense: 43 00 00 00
[  292.945684] sda: assuming drive cache: write through
[  292.945698]  sda: sda1
[  292.994219] sd 3:0:0:0: Attached scsi removable disk sda
[  292.994396] sd 3:0:0:0: Attached scsi generic sg0 type 0


---

### Post by FrodoB on 2006-11-22
You are still loading two drivers for the same card. You need to go back and look at the blacklist entries explained above.

See this:

[   71.434250] prism2pci_init: prism2_pci.o: 0.2.5 Loaded
[   71.434440] PCI: Enabling device 0000:00:0d.0 (0114 -> 0116)
[   71.434463] PCI: Found IRQ 10 for device 0000:00:0d.0
[   71.434536] A Prism2.5 PCI device found, phymem:0xec200000, irq:10, mem:0xd4990000
[   72.533297] agpgart: Detected an Intel 440BX Chipset.
[   72.540637] agpgart: AGP aperture is 64M @ 0xf0000000
[   72.759231] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[ 72.859742] orinoco_pci 0.15rc3 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au> & Jean Tourrilhes <jt@hpl.hp.com>)
[   72.952177] PCI: Enabling device 0000:00:0e.0 (0104 -> 0105)
[   72.952203] PCI: Found IRQ 11 for device 0000:00:0e.0
[   72.952241] PCI: Sharing IRQ 11 with 0000:01:00.0
[   73.041541] ieee80211_crypt: registered algorithm 'NULL'
[   73.114580] hostap_pci: 0.4.4-kernel (Jouni Malinen <jkmaline@cc.hut.fi>)
[   75.362005] ts: Compaq touchscreen protocol output

---

### Post by FrodoB on 2006-11-22
Quite honestly, the quickest path for you may be be reinstall edgy and then blacklist all of the orinoco related modules that show up in lsmod and the reboot. The prism chipset on this card is one of the preferred kernel module devices in Linux wireless.

The ndiswrapper  is an unnecessary  side trip for this device.

---

### Post by xnszxdotnet on 2006-11-22
ok, that one might of been on me. I put the blacklist in twice.
iwconfig


> 

lo        no wireless extensions.

wlan0     no wireless extensions.

sit0      no wireless extensions.


dmesg

> 

[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 00000000040fd800 (usable)
[17179569.184000]  BIOS-e820: 00000000040fd800 - 00000000040ff800 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000040ff800 - 00000000040ffc00 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000040ffc00 - 0000000014000000 (usable)
[17179569.184000]  BIOS-e820: 00000000fffe7000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 320MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 81920
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 77824 pages, LIFO batch:15
[17179569.184000] DMI 2.1 present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6ac0
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x00000000 PTL  0x01000000) @ 0x040fda87
[17179569.184000] ACPI: FADT (v001 GATEWA TABOR II 0x19990422 PTL  0x000f4240) @ 0x040ff78c
[17179569.184000] ACPI: DSDT (v001 GATEWA TABOR II 0x00000000 MSFT 0x01000000) @ 0x00000000
[17179569.184000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[17179569.184000] ACPI: Disabling ACPI support
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 14000000:ebfe7000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (0128a000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 448.139 MHz processor.
[   38.313222] Using tsc for high-res timesource
[   38.314583] Console: colour VGA+ 80x25
[   38.315818] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   38.317067] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   38.367276] Memory: 315112k/327680k available (1910k kernel code, 11996k reserved, 1070k data, 308k init, 0k highmem)
[   38.367294] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   38.445064] Calibrating delay using timer specific routine.. 897.66 BogoMIPS (lpj=1795321)
[   38.445229] Security Framework v1.0.0 initialized
[   38.445258] SELinux:  Disabled at boot.
[   38.445325] Mount-cache hash table entries: 512
[   38.445849] CPU: After generic identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   38.445882] CPU: After vendor identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   38.445921] CPU: L1 I cache: 16K, L1 D cache: 16K
[   38.445933] CPU: L2 cache: 512K
[   38.445943] CPU serial number disabled.
[   38.445953] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   38.446032] Checking 'hlt' instruction... OK.
[   38.461308] SMP alternatives: switching to UP code
[   38.461726] Freeing SMP alternatives: 16k freed
[   38.462205] checking if image is initramfs... it is
[   40.567453] Freeing initrd memory: 5254k freed
[   40.567480] CPU0: Intel Pentium III (Katmai) stepping 03
[   40.567504] SMP motherboard not detected.
[   40.567515] Local APIC not detected. Using dummy APIC emulation.
[   40.567796] Brought up 1 CPUs
[   40.567875] migration_cost=0
[   40.569162] NET: Registered protocol family 16
[   40.569299] EISA bus registered
[   40.569772] PCI: PCI BIOS revision 2.10 entry at 0xfd983, last bus=2
[   40.569796] PCI: Using configuration type 1
[   40.569805] Setting up standard PCI resources
[   40.571713] ACPI: Interpreter disabled.
[   40.571732] Linux Plug and Play Support v0.97 (c) Adam Belay
[   40.571765] pnp: PnP ACPI: disabled
[   40.571779] PnPBIOS: Scanning system for PnP BIOS support...
[   40.571835] PnPBIOS: Found PnP BIOS installation structure at 0xc00f6ae0
[   40.571851] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x9e31, dseg 0x400
[   40.581764] PnPBIOS: 18 nodes reported by PnP BIOS; 18 recorded by driver
[   40.581981] PCI: Probing PCI hardware
[   40.581996] PCI: Probing PCI hardware (bus 00)
[   40.582457] PCI: Ignoring BAR0-3 of IDE controller 0000:00:07.1
[   40.582615] PCI quirk: region 8000-803f claimed by PIIX4 ACPI
[   40.582629] PCI quirk: region 7000-700f claimed by PIIX4 SMB
[   40.583298] Boot video device is 0000:01:00.0
[   40.587361] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
[   40.593064] pnp: 00:00: ioport range 0x370-0x371 has been reserved
[   40.593119] pnp: 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   40.593133] pnp: 00:0a: ioport range 0x8000-0x803f has been reserved
[   40.593146] pnp: 00:0a: ioport range 0x7000-0x700f has been reserved
[   40.594292] PCI: Bridge: 0000:00:01.0
[   40.594306]   IO window: 9000-9fff
[   40.594321]   MEM window: ec000000-ec0fffff
[   40.594334]   PREFETCH window: f8000000-fbffffff
[   40.594349] PCI: Bridge: 0000:00:10.0
[   40.594356]   IO window: disabled.
[   40.594370]   MEM window: ec100000-ec1fffff
[   40.594380]   PREFETCH window: disabled.
[   40.594503] NET: Registered protocol family 2
[   40.633063] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   40.633503] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   40.634071] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   40.634361] TCP: Hash tables configured (established 16384 bind 8192)
[   40.634374] TCP reno registered
[   40.637619] audit: initializing netlink socket (disabled)
[   40.637671] audit(1164229963.512:1): initialized
[   40.638260] VFS: Disk quotas dquot_6.5.1
[   40.638348] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   40.638567] Initializing Cryptographic API
[   40.638587] io scheduler noop registered
[   40.638619] io scheduler anticipatory registered
[   40.638648] io scheduler deadline registered
[   40.638705] io scheduler cfq registered (default)
[   40.638725] Limiting direct PCI/PCI transfers.
[   40.639685] isapnp: Scanning for PnP cards...
[   40.995138] isapnp: No Plug & Play device found
[   41.136154] Real Time Clock Driver v1.12ac
[   41.136471] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   41.136904] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   41.139600] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   41.143174] pnp: Device 00:0f activated.
[   41.143531] 00:0f: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   41.144509] mice: PS/2 mouse device common for all mice
[   41.147624] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   41.148191] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   41.148210] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   41.148938] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   41.165663] serio: i8042 AUX port at 0x60,0x64 irq 12
[   41.166743] serio: i8042 KBD port at 0x60,0x64 irq 1
[   41.169483] EISA: Probing bus 0 at eisa.0
[   41.169509] Cannot allocate resource for EISA slot 1
[   41.169556] Cannot allocate resource for EISA slot 7
[   41.169567] Cannot allocate resource for EISA slot 8
[   41.169576] EISA: Detected 0 cards.
[   41.169917] TCP bic registered
[   41.169955] NET: Registered protocol family 1
[   41.169980] NET: Registered protocol family 8
[   41.169990] NET: Registered protocol family 20
[   41.170074] Using IPI No-Shortcut mode
[   41.171544] Freeing unused kernel memory: 308k freed
[   41.222840] input: AT Translated Set 2 keyboard as /class/input/input0
[   42.592579] Capability LSM initialized
[   44.363576] PIIX4: IDE controller at PCI slot 0000:00:07.1
[   44.363617] PIIX4: chipset revision 1
[   44.363627] PIIX4: not 100% native mode: will probe irqs later
[   44.363651]     ide0: BM-DMA at 0x1000-0x1007, BIOS settings: hda:pio, hdb:DMA
[   44.363691] Probing IDE interface ide0...
[   44.652355] hda: ST380021A, ATA DISK drive
[   45.436243] hdb: PIONEER DVD-RW DVR-108, ATAPI CD/DVD-ROM drive
[   45.492530] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   45.521752] hda: max request size: 128KiB
[   45.562946] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
[   45.562976] hda: cache flushes not supported
[   45.563123]  hda: hda1 hda2 < hda5 >
[   45.693922] hdb: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(33)
[   45.693958] Uniform CD-ROM driver Revision: 3.20
[   46.065236] Probing IDE interface ide1...
[   46.137608] usbcore: registered new driver usbfs
[   46.139705] usbcore: registered new driver hub
[   46.150748] USB Universal Host Controller Interface driver v3.0
[   46.152957] PCI: Found IRQ 9 for device 0000:00:07.2
[   46.153029] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   46.153887] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   46.153947] uhci_hcd 0000:00:07.2: irq 9, io base 0x00001020
[   46.154813] usb usb1: configuration #1 chosen from 1 choice
[   46.155421] hub 1-0:1.0: USB hub found
[   46.155463] hub 1-0:1.0: 2 ports detected
[   46.246953] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   46.336220] ohci_hcd 0000:02:08.0: OHCI Host Controller
[   46.336993] ohci_hcd 0000:02:08.0: new USB bus registered, assigned bus number 2
[   46.337046] ohci_hcd 0000:02:08.0: irq 9, io mem 0xec104000
[   46.916354] ieee1394: Initialized config rom entry `ip1394'
[   46.963067] usb usb2: configuration #1 chosen from 1 choice
[   46.963653] hub 2-0:1.0: USB hub found
[   46.963702] hub 2-0:1.0: 3 ports detected
[   47.055897] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   47.214881] usb 1-1: configuration #1 chosen from 1 choice
[   47.455845] usb 1-2: new low speed USB device using uhci_hcd and address 3
[   47.476633] ehci_hcd 0000:02:08.2: EHCI Host Controller
[   47.476764] ehci_hcd 0000:02:08.2: new USB bus registered, assigned bus number 3
[   47.499842] ehci_hcd 0000:02:08.2: irq 11, io mem 0xec106800
[   47.499863] ehci_hcd 0000:02:08.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[   47.500120] usb usb3: configuration #1 chosen from 1 choice
[   47.500233] hub 3-0:1.0: USB hub found
[   47.500272] hub 3-0:1.0: 5 ports detected
[   47.606435] ohci_hcd 0000:02:08.1: OHCI Host Controller
[   47.607238] ohci_hcd 0000:02:08.1: new USB bus registered, assigned bus number 4
[   47.607291] ohci_hcd 0000:02:08.1: irq 10, io mem 0xec105000
[   48.167641] usb usb4: configuration #1 chosen from 1 choice
[   48.168283] hub 4-0:1.0: USB hub found
[   48.168328] hub 4-0:1.0: 2 ports detected
[   48.205482] usb 1-2: configuration #1 chosen from 1 choice
[   48.579686] usb 3-3: new high speed USB device using ehci_hcd and address 2
[   48.715895] usb 3-3: configuration #1 chosen from 1 choice
[   48.718491] usbcore: registered new driver hiddev
[   48.771594] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[9]  MMIO=[ec106000-ec1067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   48.787522] input: HID 0461:4d03 as /class/input/input1
[   48.787675] input: USB HID v1.00 Mouse [HID 0461:4d03] on usb-0000:00:07.2-1
[   48.837434] input:   USB Keyboard as /class/input/input2
[   48.837483] input: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:07.2-2
[   48.926319] input:   USB Keyboard as /class/input/input3
[   48.926362] input: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:07.2-2
[   48.926420] usbcore: registered new driver usbhid
[   48.926444] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   48.929101] usbcore: registered new driver libusual
[   49.030618] SCSI subsystem initialized
[   49.041931] Initializing USB Mass Storage driver...
[   49.042254] scsi0 : SCSI emulation for USB Mass Storage devices
[   49.042489] usbcore: registered new driver usb-storage
[   49.042504] USB Mass Storage support registered.
[   49.042812] usb-storage: device found at 2
[   49.042823] usb-storage: waiting for device to settle before scanning
[   49.202040] Attempting manual resume
[   49.307537] kjournald starting.  Commit interval 5 seconds
[   49.307605] EXT3-fs: mounted filesystem with ordered data mode.
[   50.044204] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[005042b5c00dff24]
[   54.040125] usb-storage: device scan complete
[   54.040983]   Vendor: LEXAR     Model: JUMPDRIVE         Rev: 1000
[   54.041032]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   63.523259] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   64.333796] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   64.392283] prism2pci_init: prism2_pci.o: 0.2.5 Loaded
[   64.392452] PCI: Enabling device 0000:00:0d.0 (0114 -> 0116)
[   64.392476] PCI: Found IRQ 10 for device 0000:00:0d.0
[   64.392547] A Prism2.5 PCI device found, phymem:0xec200000, irq:10, mem:0xd49ae000
[   65.196669] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   65.203140] orinoco_pci 0.15rc3 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au> & Jean Tourrilhes <jt@hpl.hp.com>)
[   65.325519] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   65.394010] ieee80211_crypt: registered algorithm 'NULL'
[   65.442956] PCI: Enabling device 0000:00:0e.0 (0104 -> 0105)
[   65.442982] PCI: Found IRQ 11 for device 0000:00:0e.0
[   65.443021] PCI: Sharing IRQ 11 with 0000:01:00.0
[   65.563138] hostap_pci: 0.4.4-kernel (Jouni Malinen <jkmaline@cc.hut.fi>)
[   66.237951] Linux agpgart interface v0.101 (c) Dave Jones
[   66.372350] agpgart: Detected an Intel 440BX Chipset.
[   66.379920] agpgart: AGP aperture is 64M @ 0xf0000000
[   68.051113] input: PC Speaker as /class/input/input4
[   69.470085] Floppy drive(s): fd0 is 1.44M
[   69.503927] pnp: Device 00:14 activated.
[   69.503944] parport: PnPBIOS parport detected.
[   69.504016] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   69.643946] FDC 0 is a post-1991 82077
[   72.285322] ts: Compaq touchscreen protocol output
[   74.773258] SCSI device sda: 2026592 512-byte hdwr sectors (1038 MB)
[   74.774542] sda: Write Protect is off
[   74.774555] sda: Mode Sense: 43 00 00 00
[   74.774564] sda: assuming drive cache: write through
[   74.777278] SCSI device sda: 2026592 512-byte hdwr sectors (1038 MB)
[   74.778149] sda: Write Protect is off
[   74.778161] sda: Mode Sense: 43 00 00 00
[   74.778170] sda: assuming drive cache: write through
[   74.778184]  sda: sda1
[   74.849166] sd 0:0:0:0: Attached scsi removable disk sda
[   74.903550] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   75.266277] lp0: using parport0 (interrupt-driven).
[   75.343332] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   75.343351] ieee1394: sbp2: Try serialize_io=0 for better performance
[   75.433964] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[   75.621113] Adding 939760k swap on /dev/disk/by-uuid/d6a6cd96-ff76-4ed6-9b1e-4d5c171de15c.  Priority:-1 extents:1 across:939760k
[   75.730696] EXT3 FS on hda1, internal journal
[   78.412082] NET: Registered protocol family 17
[   89.993820] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   99.690130] NET: Registered protocol family 10
[   99.690491] lo: Disabled Privacy Extensions
[   99.690814] IPv6 over IPv4 tunneling driver
[  120.673798] usb 3-3: USB disconnect, address 2
[  123.464004] Bluetooth: Core ver 2.8
[  123.464025] NET: Registered protocol family 31
[  123.464034] Bluetooth: HCI device and connection manager initialized
[  123.464085] Bluetooth: HCI socket layer initialized
[  123.533988] Bluetooth: L2CAP ver 2.8
[  123.534007] Bluetooth: L2CAP socket layer initialized
[  123.601312] Bluetooth: RFCOMM socket layer initialized
[  123.601362] Bluetooth: RFCOMM TTY layer initialized
[  123.601372] Bluetooth: RFCOMM ver 1.7
[  136.283561] usb 3-3: new high speed USB device using ehci_hcd and address 3
[  136.419357] usb 3-3: configuration #1 chosen from 1 choice
[  136.419961] scsi1 : SCSI emulation for USB Mass Storage devices
[  136.420341] usb-storage: device found at 3
[  136.420351] usb-storage: waiting for device to settle before scanning
[  141.419665] usb-storage: device scan complete
[  141.421035]   Vendor: LEXAR     Model: JUMPDRIVE         Rev: 1000
[  141.421087]   Type:   Direct-Access                      ANSI SCSI revision: 00
[  141.428007] SCSI device sda: 2026592 512-byte hdwr sectors (1038 MB)
[  141.429563] sda: Write Protect is off
[  141.429579] sda: Mode Sense: 43 00 00 00
[  141.429588] sda: assuming drive cache: write through
[  141.433206] SCSI device sda: 2026592 512-byte hdwr sectors (1038 MB)
[  141.434322] sda: Write Protect is off
[  141.434338] sda: Mode Sense: 43 00 00 00
[  141.434347] sda: assuming drive cache: write through
[  141.434361]  sda: sda1
[  141.483458] sd 1:0:0:0: Attached scsi removable disk sda
[  141.483630] sd 1:0:0:0: Attached scsi generic sg0 type 0
[  150.657610] usb 3-3: USB disconnect, address 3
[  154.928978] usb 3-3: new high speed USB device using ehci_hcd and address 4
[  155.073630] usb 3-3: configuration #1 chosen from 1 choice
[  155.074684] scsi2 : SCSI emulation for USB Mass Storage devices
[  155.075089] usb-storage: device found at 4
[  155.075099] usb-storage: waiting for device to settle before scanning
[  160.073456] usb-storage: device scan complete
[  160.076404]   Vendor:           Model: USB Flash Memory  Rev: 1.04
[  160.076458]   Type:   Direct-Access                      ANSI SCSI revision: 00
[  161.184142] SCSI device sda: 501760 512-byte hdwr sectors (257 MB)
[  161.188145] sda: Write Protect is off
[  161.188162] sda: Mode Sense: 23 00 00 00
[  161.188172] sda: assuming drive cache: write through
[  161.196151] SCSI device sda: 501760 512-byte hdwr sectors (257 MB)
[  161.200143] sda: Write Protect is off
[  161.200161] sda: Mode Sense: 23 00 00 00
[  161.200170] sda: assuming drive cache: write through
[  161.200185]  sda: unknown partition table
[  161.207601] sd 2:0:0:0: Attached scsi removable disk sda
[  161.207777] sd 2:0:0:0: Attached scsi generic sg0 type 0



---

### Post by FrodoB on 2006-11-22
No. You are still getting:

orinoco_pci
ndiswrapper

the blacklist file needs:

blacklist orinoco_pci
blacklist ndiswrapper

I have to turn in for the evening. It seems that you are close and your card is seen in dmesg.

When you get orinoco_pci and ndiswrapper out of your dmesg after a boot you should be working.

---

### Post by xnszxdotnet on 2006-11-22
$ sudo gedit /etc/modprobe.d/blacklist

***************
here is what I have in that file.
******************

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801


# Blacklisted to get prism chipset detected
blacklist orinoco
blacklist orinoco_pci
blacklist hermes
blacklist ndiswrapper

***************************
after reboot
***************************


I get a popup window that says:

Internal error
failed to initalize HAL!

i close it and try the iwconfig

lo        no wireless extensions.

wlan0     no wireless extensions.

sit0      no wireless extensions.


then i go and check my blacklist file again and see if it's the same , and it is.


dmesg

...
[   48.453096] Attempting manual resume
[   48.558989] kjournald starting.  Commit interval 5 seconds
[   48.559057] EXT3-fs: mounted filesystem with ordered data mode.
[   49.351555] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[005042b5c00dff24]
[   64.199506] prism2pci_init: prism2_pci.o: 0.2.5 Loaded
[   64.199619] PCI: Enabling device 0000:00:0d.0 (0114 -> 0116)
[   64.199642] PCI: Found IRQ 10 for device 0000:00:0d.0
[   64.199712] A Prism2.5 PCI device found, phymem:0xec200000, irq:10, mem:0xd496c000
[   65.022101] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   65.027956] orinoco_pci 0.15rc3 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au> & Jean Tourrilhes <jt@hpl.hp.com>)
[   65.102525] ieee80211_crypt: registered algorithm 'NULL'
[   65.266466] hostap_pci: 0.4.4-kernel (Jouni Malinen <jkmaline@cc.hut.fi>)
[   65.303551] input: PC Speaker as /class/input/input4
[   65.325054] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   65.520569] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   65.715481] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   65.735328] Linux agpgart interface v0.101 (c) Dave Jones
[   65.748745] agpgart: Detected an Intel 440BX Chipset.
[   65.756012] agpgart: AGP aperture is 64M @ 0xf0000000
[   67.191096] pnp: Device 00:14 activated.
[   67.191112] parport: PnPBIOS parport detected.
[   67.191182] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   70.073876] Floppy drive(s): fd0 is 1.44M
[   70.783572] PCI: Enabling device 0000:00:0e.0 (0104 -> 0105)
[   70.783598] PCI: Found IRQ 11 for device 0000:00:0e.0
[   70.783636] PCI: Sharing IRQ 11 with 0000:01:00.0
[   71.124811] ts: Compaq touchscreen protocol output
[   71.320820] FDC 0 is a post-1991 82077
[   73.160042] lp0: using parport0 (interrupt-driven).
[   73.307682] SCSI subsystem initialized
[   73.327982] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   73.328000] ieee1394: sbp2: Try serialize_io=0 for better performance
[   73.419014] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[   73.606852] Adding 939760k swap on /dev/disk/by-uuid/d6a6cd96-ff76-4ed6-9b1e-4d5c171de15c.  Priority:-1 extents:1 across:939760k
[   73.715913] EXT3 FS on hda1, internal journal
[   76.405508] NET: Registered protocol family 17
[   88.095703] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   97.758327] NET: Registered protocol family 10
...

***********
still not working.

---

### Post by FrodoB on 2006-11-23
Very strange, either there is something wrong with the card or the setup of Ubuntu is really messed up.

I am going to install 6.10 on my machine that has a prism card so I can see what happens, as it works.

---

### Post by FrodoB on 2006-11-23
OK, I did a fresh install of Edgy and rebooted with my pcmcia version of the prism card installed. It was immediately recognized as eth1 as I already have an eth0.

I then entered the correct information into the System -> Administration  -> Networking panel and activated the card. Upon leaving the Networking panel and running iwconfig it showed the device eth1 and that it was associated with my access point.

That is my recommendation,

1) Reinstall Edgy from scratch.   

2) Reboot and run iwconfig, you should see eth1 as a wireless device.

3) Setup using Networking control panel.

4) Check for connection.

5) If connection is not working then publish the contents if /etc/interfaces and the output of iwconfig.

We are either going to see it work or something is likely wrong with this device.

---

### Post by FrodoB on 2006-11-23
Also, at this point shutting the system down and then physically removing the card for 10 or more seconds and replacing it, or better yet changing it to another slot in the computer could not hurt, and it might help a lot if the card is not properly seated in the system.

---

### Post by xnszxdotnet on 2006-11-27
I reisntalled edgy from scatch ran iwconfig:
> 
lo no wireless extensions.

wlan0 no wireless extensions.

sit0 no wireless extensions.

shutdown
moved the card
restarted and the same.

/etc/interfaces
no file or directory

as for the device it was working right before installing edgy under winxp.??

---

### Post by FrodoB on 2006-11-27
I never seen anything like it.  Maybe someone else has some further ideas.

---

### Post by FrodoB on 2006-11-27
OK I see a bug report that may provide a clue:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63989](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63989)

Except we want to remove everything except the prism2_pci

Try these commands and see if iwconfig produces results now:

$ sudo modprobe -r orinoco_pci
$ sudo modprobe -r hostap_pci
$ sudo modprobe -r orinoco_pci
$ sudo modprobe prism2_pci

---

### Post by xnszxdotnet on 2006-11-27
still the same.

lo no wireless extensions.

wlan0 no wireless extensions.

sit0 no wireless extensions.

The last post in the bug report said something about a blacklist should I try that. it didn't work with the last install could it work now? since I reinstalled everything? or don't waste my time on it?

it this point I'm about to pull the card and put a wired ethernet card in, go to home depot buy some cat5e and pull it through the walls, just to get this upstairs computer online!!!

](*,) 

but it does make me feel a little better that other people are haveing the same problem.

I do think that it worked dapper?? I might think of down grading??

---

### Post by FrodoB on 2006-11-28
The easy way may be to go to Ubuntu 6.06, it is the Long Term Support distribution and will have security updates until sometime in 2009.  I believe that the ma311 will work with it from what I have read.

---

### Post by xnszxdotnet on 2006-11-28
downgraded to Dapper. works right off the bat.

Thanks alot FrodoB without your help I wouuld have had to *gasp* go back to windows xp.

I would have never figured any of this stuff out on my own.

thanks again.:p 

now I'm off to install mythTV and ivtv. wish me luck.

---

### Post by FrodoB on 2006-11-28
OK, it is a prism and pci issue. That explains why my PCMCIA card works and this one does not. 

There is a bug report on this:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/53748](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/53748)

If you are running a prism2 card on a PCI bus you have to use Dapper unless you want to recompile the kernel.

Not worth it for most folks, as I said Dapper in on long term support until sometime in 2009.

---

### Post by xnszxdotnet on 2006-11-28
cool, thanx alot

recompiling the kernel is, as you said, not worth it to me.

---

### Post by Konami on 2007-06-16
> **xnszxdotnet said:**
> cool, thanx alot

recompiling the kernel is, as you said, not worth it to me.

What so is required to recopile the kernel to make the MA311 PCI work?

---

