---
title: "ati proprietary driver problem! HELP!"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by rtool on 2010-06-16
I set up ubuntu on my dimension dell desktop with a radeon r350 (radeon 9800 pro) graphics card. i used ati's new proprietary driver from here 
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English ]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English")
the installer instructions told me to 
"sh ./ati-driver-installer-9.2-x86.x86_64.run"
and i get
"Can't open ./ati-driver-installer-9.2-x86.x86_64.run"

What is going wrong? :confused:

---

### Post by sikander3786 on 2010-06-16
> **rtool said:**
> I set up ubuntu on my dimension dell desktop with a radeon r350 (radeon 9800 pro) graphics card. i used ati's new proprietary driver from here 
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English ]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English")
the installer instructions told me to 
"sh ./ati-driver-installer-9.2-x86.x86_64.run"
and i get
"Can't open ./ati-driver-installer-9.2-x86.x86_64.run"

What is going wrong? :confused:

Hi.

Try adding sudo.

```

sudo sh ./ati-driver-installer-9.2-x86.x86_64.run

```

Regards.

Edit: An other thing might help. Is your dell dimension 64-bit capable? The driver is meant for 64-bit OS.

---

### Post by rtool on 2010-06-16
using sudo i still got
sh: Can't open ./ati-driver-installer-9.2-x86.x86_64.run
how do i know if the computer is x64?

---

### Post by ibe2fly4chu on 2010-06-16
you are getting that error because you have to exit X in order to run that driver. First: open terminal, *before you type this in make sure you read the whole response, because this will put you into a command line interface*

Type: /etc/init.d/gdm stop

then you have to login using username and password. After that, you need to "cd" into the directory where you have that file. So for example if the file is located in your Downloads folder, the command should then look like: cd /home/yourusername/Downloads

once in the directory of the file, type " sudo sh ./ati-driver-installer-9.2-x86.x86_64.run"...without the quotes, and watch that baby installs.

oh right..almost forgot...after you are done...you can "sudo reboot" to restart your comp.

---

### Post by clhsharky on 2010-06-16
CAT9.3 was made for Ubuntu8.04-8.10. 
Will not work latter releases.

Sharky

rtool  the OSS driver that came with Lucid is the correct driver for your card.

---

### Post by sikander3786 on 2010-06-16
Check out the user manual of your PC from the vendors.

Or please post your specs. Which processor is in use?

---

### Post by rtool on 2010-06-16
the site has two different selections when downloading for either linux x86 or linux x86_64 both download the same file though
**'ATI Catalyst™ 9.3 Proprietary Linux x86 Display Driver**'

---

### Post by rtool on 2010-06-16
should i post a hardinfo report?

---

### Post by rtool on 2010-06-16
[B]
[/B]

**Computer**

Summary Computer ProcessorIntel(R)  Pentium(R) 4 CPU 3.00GHz Memory1025MB (368MB used) Operating SystemUbuntu  10.04 LTS User Namereese (Reese) Date/TimeTue 15 Jun 2010  10:59:47 PM CDT Display Resolution1024x768 pixels OpenGL RendererUnknown X11 VendorThe X.Org  Foundation Multimedia Audio AdapterEMU10K1X -  Dell Sound Blaster Live! Audio AdapterICH4 - Intel  ICH5 Input Devices  Power Button
 Power Button
 Macintosh mouse button emulation
 AT Translated Set 2 keyboard
 Logitech USB-PS/2 Optical Mouse
Printers No printers found
SCSI Disks ATA WDC WD600BB-75CA
LITEON DVD-ROM LTD163
Operating  System Version KernelLinux  2.6.32-22-generic (i686) Compiled#36-Ubuntu SMP Thu  Jun 3 22:02:19 UTC 2010 C LibraryGNU C Library  version 2.11.1 (stable) Default C CompilerGNU C  Compiler version 4.4.3 (Ubuntu 4.4.3-4ubuntu5)  DistributionUbuntu 10.04  LTS Current Session Computer Nameubuntu User Namereese (Reese) Home Directory/home/reese Desktop EnvironmentGNOME  2.30.0 Misc Uptime44 minutes Load Average1.14, 1.12,  1.10 Kernel  Modules Loaded Modules binfmt_misc
fbcon
tileblitTile Blitting  Operation fontConsole Fonts bitblitBit Blitting  Operation softcursorGeneric software  cursor vga16fbLegacy VGA  framebuffer device driver vgastateVGA State  Save/Restore snd_intel8x0Intel  82801AA,82901AB,i810,i820,i830,i840,i845,MX440; SiS 7012; Ali 5455 snd_seq_dummyALSA sequencer  MIDI-through client snd_seq_ossOSS-compatible  sequencer module snd_seq_midiAdvanced Linux  Sound Architecture sequencer MIDI synth. snd_emu10k1xEMU10K1X snd_ac97_codecUniversal  interface for Audio Codec '97 snd_rawmidiMidlevel RawMidi  code for ALSA. snd_pcm_ossPCM OSS  emulation for ALSA. snd_seq_midi_eventMIDI byte  <-> sequencer event coder snd_mixer_ossMixer OSS  emulation for ALSA. snd_seqAdvanced Linux Sound  Architecture sequencer. radeonATI Radeon snd_pcmMidlevel PCM code  for ALSA. snd_seq_deviceALSA  sequencer device management ttmTTM memory manager  subsystem (for DRM device) i82875p_edacMC support for  Intel 82875 memory hub controllers drm_kms_helperDRM KMS  helper snd_timerALSA timer  interface emu10k1_gpEMU10k1 gameport  driver ppdev
edac_coreCore library  routines for EDAC reporting drmDRM shared core routines i2c_algo_bitI2C-Bus  bit-banging algorithm gameportGeneric gameport  layer ac97_bus
dell_wmiDell laptop WMI  hotkeys driver sndAdvanced Linux Sound  Architecture driver for soundcards. parport_pcPC-style parallel  port driver dcdbasDell Systems  Management Base Driver (version 5.6.0-3.2) intel_agp
lp
soundcoreCore sound module snd_page_allocMemory  allocator for ALSA system. agpgartAGP GART driver shpchpStandard Hot Plug PCI  Controller Driver parport
usbhidUSB HID core driver hid
e100Intel(R) PRO/100  Network Driver miiMII hardware support  library floppy
Boots Boots Tue Jun 15 22:152.6.32-22-generi|- Tue Jun 15 19:372.6.32-22-generi|- Mon Jun 14 12:572.6.32-22-generi|- Mon Jun 14 12:542.6.32-22-generi|- Mon Jun 14 12:462.6.32-22-generi|- Sun Jun 13 18:492.6.32-22-generi|- Languages Available Languages en_AGEnglish language  locale for Antigua and Barbuda en_AU.utf8English locale  for Australia en_BW.utf8English locale  for Botswana en_CA.utf8English locale  for Canada en_DK.utf8English locale  for Denmark en_GB.utf8English locale  for Britain en_HK.utf8English locale  for Hong Kong en_IE.utf8English locale  for Ireland en_INEnglish language  locale for India en_NGEnglish locale for  Nigeria en_NZ.utf8English locale  for New Zealand en_PH.utf8English language  locale for Philippines en_SG.utf8English language  locale for Singapore en_US.utf8English locale  for the USA en_ZA.utf8English locale  for South Africa Filesystems Mounted File Systems   /dev/sda1/73.30 % (14.1 GiB of 52.7 GiB)   none/dev0.06  % (496.5 MiB of 496.8 MiB)   none/dev/shm0.37 % (499.0 MiB of 500.9 MiB)   none/var/run0.04 % (500.7 MiB of 500.9 MiB)   none/var/lock0.00 % (500.9 MiB of 500.9 MiB)   none/lib/init/rw0.00 % (500.9 MiB of 500.9 MiB) Display Display Resolution1024x768 pixels VendorThe X.Org Foundation Version1.7.6 Monitors Monitor 01024x768 pixels Extensions BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
RANDR
RECORD
RENDER
SECURITY
SGI-GLX
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
OpenGL VendorUnknown RendererUnknown VersionUnknown Direct RenderingNo Environment  Variables Environment Variables ORBIT_SOCKETDIR/tmp/orbit-reese SSH_AGENT_PID1186 TERMxterm SHELL/bin/bash XDG_SESSION_COOKIE38d2c13c47007703cb46d7e34c156e85-1276658153.181759-1713452225 WINDOWID60817412 GNOME_KEYRING_CONTROL/tmp/keyring-xjWABd GTK_MODULEScanberra-gtk-module USERreese LS_COLORSrs=0:di=01;34:ln=01;36:hl=44;37:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36: SSH_AUTH_SOCK/tmp/keyring-xjWABd/ssh DEFAULTS_PATH/usr/share/gconf/gnome.default.path SESSION_MANAGERlocal/ubuntu:@/tmp/.ICE-unix/1152,unix/ubuntu:/tmp/.ICE-unix/1152 USERNAMEreese XDG_CONFIG_DIRS/etc/xdg/xdg-gnome:/etc/xdg DESKTOP_SESSIONgnome PATH/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games PWD/home/reese GDM_KEYBOARD_LAYOUTus LANGen_US.utf8 GNOME_KEYRING_PID1134 MANDATORY_PATH/usr/share/gconf/gnome.mandatory.path GDM_LANGen_US.utf8 GDMSESSIONgnome SPEECHD_PORT7560 SHLVL1 HOME/home/reese GNOME_DESKTOP_SESSION_IDthis-is-deprecated LOGNAMEreese XDG_DATA_DIRS/usr/share/gnome:/usr/local/share/:/usr/share/ DBUS_SESSION_BUS_ADDRESSunix:abstract=/tmp/dbus-3JhulWFL6R,guid=f0431438877604e4691a404b4c1841e9 LESSOPEN| /usr/bin/lesspipe  %s DISPLAY:0.0 LESSCLOSE/usr/bin/lesspipe  %s %s XAUTHORITY/var/run/gdm/auth-for-reese-GOge2u/database COLORTERMgnome-terminal _/usr/bin/hardinfo Users Users rootroot daemondaemon binbin syssys syncsync gamesgames manman lplp mailmail newsnews uucpuucp proxyproxy www-datawww-data backupbackup listMailing List Manager ircircd gnatsGnats Bug-Reporting  System (admin) nobodynobody libuuid
syslog
messagebus
avahi-autoipdAvahi autoip  daemon avahiAvahi mDNS daemon couchdbCouchDB  Administrator speech-dispatcherSpeech  Dispatcher usbmuxusbmux daemon haldaemonHardware  abstraction layer kernoopsKernel Oops  Tracking Daemon pulsePulseAudio daemon rtkitRealtimeKit saned
hplipHPLIP system user landscape
gdmGnome Display Manager reeseReese **Devices**

Processor Processor NameIntel(R) Pentium(R) 4  CPU 3.00GHz Family, model, stepping15,  2, 9 (Pentium 4) VendorIntel Configuration Cache Size512kb Frequency2992.25MHz BogoMIPS5984.50 Byte OrderLittle Endian Features FDIV Bugno HLT Bugno F00F Bugno Coma Bugno Has FPUyes Cache Cache information not available
Capabilities fpuFloating Point Unit vmeVirtual 86 Mode  Extension deDebug Extensions - I/O  breakpoints psePage Size Extensions  (4MB pages) tscTime Stamp Counter and  RDTSC instruction msrModel Specific Registers paePhysical Address  Extensions mceMachine Check  Architeture cx8CMPXCHG8 instruction apicAdvanced Programmable  Interrupt Controller mtrrMemory Type Range  Registers pgePage Global Enable mcaMachine Check  Architecture cmovConditional Move  instruction patPage Attribute Table pse3636bit Page Size  Extensions clflushCache Line Flush  instruction dtsDebug Store acpiThermal Monitor and  Software Controlled Clock mmxMMX technology fxsrFXSAVE and FXRSTOR  instructions sseSSE instructions sse2SSE2 (WNI) instructions ssSelf Snoop htHyperThreading tmThermal Monitor pbePending Break Enable upsmp kernel running on up pebsPrecise-Event Based  Sampling btsBranch Trace Store cidContext ID xtprSend Task Priority  Messages Memory Memory Total Memory1025824 kB Free Memory253716 kB Buffers28436 kB Cached404736 kB Cached Swap244 kB Active417620 kB Inactive301340 kB Active(anon)129132 kB Inactive(anon)164524 kB Active(file)288488 kB Inactive(file)136816 kB Unevictable0 kB Mlocked0 kB High Memory138712 kB Free High Memory3052 kB Low Memory887112 kB Free Low Memory250664 kB Virtual Memory2438136 kB Free Virtual Memory2436252  kB Dirty172 kB Writeback0 kB AnonPages285568 kB Mapped98128 kB Shmem7860 kB Slab29616 kB SReclaimable19224 kB SUnreclaim10392 kB KernelStack2176 kB PageTables6184 kB NFS_Unstable0 kB Bounce0 kB WritebackTmp0 kB CommitLimit2951048 kB Committed_AS1100608 kB VmallocTotal122880 kB VmallocUsed16856 kB VmallocChunk99324 kB HardwareCorrupted0 kB HugePages_Total0 HugePages_Free0 HugePages_Rsvd0 HugePages_Surp0 Hugepagesize4096 kB DirectMap4k471032 kB DirectMap4M438272 kB PCI  Devices PCI Devices Host bridgeIntel  Corporation 82875P/E7210 Memory Controller Hub (rev 02) PCI bridgeIntel Corporation  82875P Processor to AGP Controller (rev 02) System peripheralIntel  Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02) USB ControllerIntel  Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) USB ControllerIntel  Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) USB ControllerIntel  Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) USB ControllerIntel  Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) USB ControllerIntel  Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)  (prog-if 20) PCI bridgeIntel Corporation  82801 PCI Bridge (rev c2) ISA bridgeIntel Corporation  82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02) IDE interfaceIntel  Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a  [Master SecP PriP]) IDE interfaceIntel  Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master  SecP SecO PriP PriO]) SMBusIntel Corporation  82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02) Multimedia audio controllerIntel  Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02) VGA compatible controllerATI  Technologies Inc Radeon R350 [Radeon 9800 Pro] Display controllerATI  Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary) Multimedia audio controllerCreative  Labs [SB Live! Value] EMU10k1X Input device controllerCreative  Labs [SB Live! Value] Input device controller Ethernet controllerIntel  Corporation 82562EZ 10/100 Ethernet Controller (rev 02) USB  Devices Printers Printers No printers found
Battery No batteries No batteries found on this system
Sensors Input  Devices Input Devices  Power Button
 Power Button
 Macintosh mouse button emulation
 AT Translated Set 2 keyboard
 Logitech USB-PS/2 Optical Mouse
Storage SCSI Disks ATA WDC WD600BB-75CA
LITEON DVD-ROM LTD163
DMI BIOS Date09/27/2004 VendorDell Computer  Corporation ([www.dell.com](www.dell.com)) VersionA07 Board Name0G0728 VendorDell Computer Corp.  ([www.dell.com](www.dell.com)) Resources I/O Ports 0000-001f dma1 0020-0021 pic1 0040-0043 timer0 0050-0053 timer1 0060-0060 keyboard 0064-0064 keyboard 0070-007f rtc0 0080-008f dma page  reg 00a0-00a1 pic2 00c0-00df dma2 00f0-00ff fpu 0170-0177 Intel  Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a  [Master SecP PriP])   0170-0177 ata_piix 01f0-01f7 Intel  Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a  [Master SecP PriP])   01f0-01f7 ata_piix 0376-0376 Intel  Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a  [Master SecP PriP])   0376-0376 ata_piix 0378-037a parport0 03c0-03df vga+ 03f2-03f2 floppy 03f4-03f5 floppy 03f6-03f6 Intel  Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a  [Master SecP PriP])   03f6-03f6 ata_piix 03f7-03f7 floppy 03f8-03ff serial 0778-077a parport0 0800-087f Intel  Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)   0800-0803 ACPI  PM1a_EVT_BLK   0804-0805 ACPI  PM1a_CNT_BLK   0808-080b ACPI  PM_TMR   0810-0815 ACPI  CPU throttle   0828-082f ACPI  GPE0_BLK 0880-08bf Intel  Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02) 0c00-0c7f pnp  00:0a 0cf8-0cff PCI  conf1 c000-cfff PCI Bus  0000:02   cf18-cf1f Creative  Labs [SB Live! Value] Input device controller     cf18-cf1f emu10k1-gp   cf20-cf3f Creative  Labs [SB Live! Value] EMU10k1X     cf20-cf27 EMU10K1X   cf40-cf7f Intel  Corporation 82562EZ 10/100 Ethernet Controller (rev 02)     cf40-cf7f Intel(R)  PRO/100 Network Driver d000-dfff PCI Bus  0000:01   de00-deff ATI  Technologies Inc Radeon R350 [Radeon 9800 Pro] eda0-edbf Intel  Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02) edc0-edff Intel  Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)   edc0-edff Intel  ICH5 ee00-eeff Intel  Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)   ee00-eeff Intel  ICH5 fe00-fe07 Intel  Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master  SecP SecO PriP PriO])   fe00-fe07 ata_piix fe10-fe13 Intel  Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master  SecP SecO PriP PriO])   fe10-fe13 ata_piix fe20-fe27 Intel  Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master  SecP SecO PriP PriO])   fe20-fe27 ata_piix fe30-fe33 Intel  Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master  SecP SecO PriP PriO])   fe30-fe33 ata_piix fea0-feaf Intel  Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master  SecP SecO PriP PriO])   fea0-feaf ata_piix ff20-ff3f Intel  Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)   ff20-ff3f uhci_hcd ff40-ff5f Intel  Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)   ff40-ff5f uhci_hcd ff60-ff7f Intel  Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)   ff60-ff7f uhci_hcd ff80-ff9f Intel  Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)   ff80-ff9f uhci_hcd ffa0-ffaf Intel  Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a  [Master SecP PriP])   ffa0-ffaf ata_piix Memory 00000000-00001fff System  RAM 00002000-00005fff reserved 00006000-0009ffff System  RAM 000a0000-000bffff Video  RAM area 000c0000-000ccfff Video  ROM 000ce800-000cffff Adapter  ROM 000f0000-000fffff reserved   000f0000-000fffff System ROM 00100000-3ff73fff System  RAM   00100000-00590662 Kernel code   00590663-007a2e47 Kernel data   0084c000-008d9e97 Kernel bss 3ff74000-3ff75fff ACPI  Non-volatile Storage 3ff76000-3ff96fff ACPI  Tables 3ff97000-3fffffff reserved e0000000-e7ffffff Intel  Corporation 82875P/E7210 Memory Controller Hub (rev 02) e8000000-f7ffffff PCI  Bus 0000:01   e8000000-efffffff ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]  (Secondary)   f0000000-f7ffffff ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] fe800000-fe8fffff PCI  Bus 0000:02   fe8ff000-fe8fffff Intel Corporation 82562EZ 10/100 Ethernet Controller (rev  02)     fe8ff000-fe8fffff Intel(R) PRO/100 Network Driver fe900000-feafffff PCI  Bus 0000:01   fe9e0000-fe9effff ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]   fe9f0000-fe9fffff ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]  (Secondary)   fea00000-fea1ffff ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] febff900-febff9ff Intel  Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)   febff900-febff9ff Intel ICH5 febffa00-febffbff Intel  Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)   febffa00-febffbff Intel ICH5 febffc00-febfffff Intel  Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a  [Master SecP PriP]) fec00000-fec0ffff reserved   fec00000-fec00fff IOAPIC 0 fecf0000-fecf0fff reserved   fecf0000-fecf0fff Intel Corporation 82875P/E7210 Processor to I/O Memory  Interface (rev 02)     fecf0000-fecf0fff pnp 00:00       fecf0000-fecf0fff Intel Corporation 82875P/E7210 Processor to I/O Memory  Interface (rev 02) fed20000-fed8ffff reserved   fed20000-fed8ffff pnp 00:00 fee00000-fee0ffff reserved   fee00000-fee0ffff pnp 00:00     fee00000-fee00fff Local APIC ffa80800-ffa80bff Intel  Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)  (prog-if 20)   ffa80800-ffa80bff ehci_hcd ffb00000-ffffffff reserved   ffb00000-ffbfffff pnp 00:00   ffc00000-ffffffff pnp 00:00 DMA  2floppy  4cascade **Network**

Interfaces Network Interfaces   lo0.00MiB0.00MiB127.0.0.1   eth0154.63MiB5.07MiB192.168.0.13 IP  Connections Connections   127.0.0.1:631LISTEN0.0.0.0:*tcp   192.168.0.13:56186CLOSE_WAIT66.114.52.25:80tcp   192.168.0.13:40691LAST_ACK91.189.94.12:80tcp   192.168.0.13:45086ESTABLISHED209.85.225.101:443tcp   192.168.0.13:44597ESTABLISHED74.125.95.100:80tcp   192.168.0.13:44608TIME_WAIT74.125.95.100:80tcp   192.168.0.13:42559CLOSE_WAIT91.189.89.31:80tcp   192.168.0.13:57038CLOSE_WAIT84.45.95.208:80tcp   192.168.0.13:56188CLOSE_WAIT66.114.52.25:80tcp   192.168.0.13:56190CLOSE_WAIT66.114.52.25:80tcp   192.168.0.13:45532ESTABLISHED216.185.96.234:80tcp   192.168.0.13:40692LAST_ACK91.189.94.12:80tcp   192.168.0.13:57036CLOSE_WAIT84.45.95.208:80tcp   192.168.0.13:33023CLOSE_WAIT84.45.95.224:80tcp   192.168.0.13:45533ESTABLISHED216.185.96.234:80tcp   192.168.0.13:45534ESTABLISHED216.185.96.234:80tcp   192.168.0.13:56187CLOSE_WAIT66.114.52.25:80tcp   192.168.0.13:57039CLOSE_WAIT84.45.95.208:80tcp   192.168.0.13:45536ESTABLISHED216.185.96.234:80tcp   192.168.0.13:56536CLOSE_WAIT91.189.89.219:443tcp   192.168.0.13:57037CLOSE_WAIT84.45.95.208:80tcp   192.168.0.13:44243TIME_WAIT74.125.95.147:80tcp   192.168.0.13:39653ESTABLISHED74.125.95.155:80tcp   192.168.0.13:56189CLOSE_WAIT66.114.52.25:80tcp   192.168.0.13:45537ESTABLISHED216.185.96.234:80tcp   192.168.0.13:45628ESTABLISHED74.125.95.157:80tcp   192.168.0.13:40689LAST_ACK91.189.94.12:80tcp   192.168.0.13:33445CLOSE_WAIT91.189.89.31:80tcp   192.168.0.13:40688LAST_ACK91.189.94.12:80tcp   192.168.0.13:45535ESTABLISHED216.185.96.234:80tcp   192.168.0.13:40693LAST_ACK91.189.94.12:80tcp   192.168.0.13:56185CLOSE_WAIT66.114.52.25:80tcp   192.168.0.13:47867ESTABLISHED74.125.95.106:80tcp   192.168.0.13:40690LAST_ACK91.189.94.12:80tcp   192.168.0.13:57040CLOSE_WAIT84.45.95.208:80tcp   192.168.0.13:60387CLOSE_WAIT209.85.225.138:80tcp   192.168.0.13:57035CLOSE_WAIT84.45.95.208:80tcp   ::1:631LISTEN:::*tcp6   0.0.0.0:68
0.0.0.0:*udp   0.0.0.0:5353
0.0.0.0:*udp   0.0.0.0:50983
0.0.0.0:*udp Routing  Table IP routing table   192.168.0.0 / 0.0.0.0255.255.255.0Ueth0   169.254.0.0 / 0.0.0.0255.255.0.0Ueth0   0.0.0.0 / 192.168.0.10.0.0.0UGeth0 ARP  Table ARP Table   192.168.0.100:26:5e:10:0e:7deth0 DNS  Servers Name servers 68.115.71.53
24.196.64.53
24.159.193.40
Statistics IP 113575Total packets  received 2With invalid addresses 0Incoming packets discarded 0Incoming packets discarded 113573Incoming packets  delivered 66225Requests sent out ICMP 0ICMP messages failed 0ICMP messages failed 2ICMP messages sent 0ICMP messages failed ICMPMSG TCP 447Active connections  openings 4Passive connection  openings 9Failed connection attempts 37Connection resets  received 11Connections established 112052Segments received 64466Segments send out 234Segments retransmited 0Bad segments received. 215Resets sent UDP 1526Packets received 2Packets to unknown port  received. 0Packet receive errors 1529Packets sent UDPLITE TCPEXT 207TCP sockets finished  time wait in fast timer 419Delayed acks sent 1Forward retransmits 414Packets directly queued  to recvmsg prequeue. 1116Bytes directly in  process context from backlog 488324Bytes directly  received in process context from prequeue 103787Packet headers  predicted 357Packets header predicted  and directly queued to user 824Acknowledgments not  containing data payload received 91Predicted acknowledgments 1Forward retransmits 1Forward retransmits 2DSACKs sent for old  packets 1Forward retransmits 1Forward retransmits 30Other TCP timeouts 2DSACKs sent for old  packets 12Connections reset due to  unexpected data 23Connections aborted due  to timeout 23Connections aborted due  to timeout IPEXT Shared  Directories SAMBA NFS **Benchmarks**

CPU Blowfish CPU Blowfish   **This Machine**2992  MHz20.582   Intel(R) Celeron(R) M processor         1.50GHz(null)26.1876862   PowerPC 740/750 (280.00MHz)(null)172.816713 CPU  CryptoHash CPU CryptoHash   **This Machine**2992  MHz37.414 CPU  Fibonacci CPU Fibonacci   **This Machine**2992  MHz5.867   Intel(R) Celeron(R) M processor         1.50GHz(null)8.1375674   PowerPC 740/750 (280.00MHz)(null)58.07682 CPU  N-Queens CPU N-Queens   **This Machine**2992  MHz10.366 FPU FFT FPU FFT   **This Machine**2992  MHz8.965 FPU  Raytracing FPU Raytracing   **This Machine**2992  MHz30.917   Intel(R) Celeron(R) M processor         1.50GHz(null)40.8816714   PowerPC 740/750 (280.00MHz)(null)161.312647

---

### Post by ibe2fly4chu on 2010-06-16
wait...what are you trying to do. Install that .run driver you got for your ati card? mabey i missed something...

---

### Post by rtool on 2010-06-16
yes that is what im trying to do. i don't know what im doing wrong

---

### Post by rtool on 2010-06-16
> **ibe2fly4chu said:**
> you are getting that error because you have to exit X in order to run that driver. First: open terminal, *before you type this in make sure you read the whole response, because this will put you into a command line interface*

Type: /etc/init.d/gdm stop

then you have to login using username and password. After that, you need to "cd" into the directory where you have that file. So for example if the file is located in your Downloads folder, the command should then look like: cd /home/yourusername/Downloads

once in the directory of the file, type " sudo sh ./ati-driver-installer-9.2-x86.x86_64.run"...without the quotes, and watch that baby installs.

oh right..almost forgot...after you are done...you can "sudo reboot" to restart your comp.

after i did
/etc/init.d/gdm stop
it went to a black screen with a typing prompt. i couldn't type. eventually it came back to the login screen so i logged in. after that i did 
cd/home/reese/downloads 
and i got
bash: cd/home/reese/downloads: No such file or directory

what does that mean?

---

### Post by sikander3786 on 2010-06-16
Seems like your PC is 64-bit capable.

Try installing the drivers the way ibe2fly4chu mentioned above.

Can't understand what clhsharky said above. Is he saying that the driver you downloaded are not meant for Ubuntu Lucid?

---

### Post by rtool on 2010-06-16
thanks for all the help by the way. ive been trying to get this to work all day.

---

### Post by rtool on 2010-06-16
bump

---

### Post by ibe2fly4chu on 2010-06-16
hmm your keyboard stops working o.0? 
thats weird...lol ok...try this...
press: ctrl alt F2 to Exit

then try loggin in again. I will have to check back here tomorrow i gotta get to bed T.T...

---

### Post by nowell29 on 2010-06-16
This might be obvious, but what are the permissions on the file?  It should be 755.  

This could be elementary, but do a 'ls -l' on that file.  If you do not see -rwxr-xr-x then the file will not run, even with sudo.

chmod 755 <file name> 
This will make it executable.  Good luck!

---

### Post by alphacrucis2 on 2010-06-16
Post the output of these before proceding.

```
uname -a 
```

and

```
lsb_release -a
```

---

### Post by waynefoutz on 2010-06-16
If you are using Ubuntu 9.04 or later, that driver will break your system when you do manage to get it installed. It is incompatible with Ubuntu's version of Xorg. It will work with Hardy Heron, (8.04,) or Intrepid, 8.10.

---

### Post by waynefoutz on 2010-06-16
> **sikander3786 said:**
> Seems like your PC is 64-bit capable.

Try installing the drivers the way ibe2fly4chu mentioned above.

Can't understand what clhsharky said above. Is he saying that the driver you downloaded are not meant for Ubuntu Lucid?

That's exactly right. That driver will not work with Lucid. Your ATI card can only use the open source drivers that were installed by default when you installed. If you want to use that driver, you need to to install Hardy Heron, 8.04 instead.

---

### Post by proxess on 2010-06-16
What waynefoutz said. Proprietary drivers from 9.3 onward are HD radeon only and only work on Ubuntu 9.04 and 9.10. The only driver that works in Lucid are 10.4 and onward.

However, judging by your graphics card, the Radeon FOSS driver is a much much better solution. Much more stable and much faster. No tearing and decent 3D.

---

### Post by rtool on 2010-06-16
> **proxess said:**
> What waynefoutz said. Proprietary drivers from 9.3 onward are HD radeon only and only work on Ubuntu 9.04 and 9.10. The only driver that works in Lucid are 10.4 and onward.

However, judging by your graphics card, the Radeon FOSS driver is a much much better solution. Much more stable and much faster. No tearing and decent 3D.

If im better off just using lucid then how can i get the 3d to work better? I'm trying to play WoW and it's not working.

---

### Post by b.bugra on 2010-06-16
I have a different ATI card but I hope installers are similar. In my case, I do to stop X or use chmod or anything. I just write sudo, drag-drop file to terminal, press Enter and wait for program to "check integrity"  and an actual gui appears. Even if I do not use sudo, it just says "I need to run it as super user." 

I think downloaded file is broken. It may take ages but you may try downloading that ~80mb file again as it seems to me that file is the one refusing to be opened.

by the way, sorry for being o total idiot but why not just activate it from hardware drivers? I do not know if WoW requires that particular driver.

---

### Post by alphacrucis2 on 2010-06-16
> **b.bugra said:**
> I have a different ATI card but I hope installers are similar. In my case, I do to stop X or use chmod or anything. I just write sudo, drag-drop file to terminal, press Enter and wait for program to "check integrity"  and an actual gui appears. Even if I do not use sudo, it just says "I need to run it as super user." 

I think downloaded file is broken. It may take ages but you may try downloading that ~80mb file again as it seems to me that file is the one refusing to be opened.

by the way, sorry for being o total idiot but why not just activate it from hardware drivers? I do not know if WoW requires that particular driver.


That doesn't work in Lucid as the fglrx driver (Catalyst 10.4) in the Lucid repos doesn't support his card. ATI dropped support for his card at Catalyst 9.3, so for the last three releases of Ubuntu, only  the open source drivers will work with this particular card. You can't install Catalyst 9.2 in Lucid either as it is not compatible with the X-org version and kernels used by Lucid.

---

### Post by b.bugra on 2010-06-16
> **alphacrucis2 said:**
> That doesn't work in Lucid as the fglrx driver (Catalyst 10.4) in the Lucid repos doesn't support his card. ATI dropped support for his card at Catalyst 9.3, so for the last three releases of Ubuntu, only  the open source drivers will work with this particular card. You can't install Catalyst 9.2 in Lucid either as it is not compatible with the X-org version and kernels used by Lucid.

ah, I see, thank you for the information. I was googling and found [this link with similar problem]("https://answers.launchpad.net/ubuntu/+question/57302") and thought there was nothing wrong with Ubuntu.

---

### Post by alphacrucis2 on 2010-06-16
> **b.bugra said:**
> ah, I see, thank you for the information. I was googling and found [this link with similar problem]("https://answers.launchpad.net/ubuntu/+question/57302") and thought there was nothing wrong with Ubuntu.

Well I suppose they could provide backwards compatibility for old ATI drivers by providing some sort of wrapper but I don't know how hard this would be. The current Maverick Meerkat alpha has already broken support for Catalyst 10.5 because Catalyst 10.5 doesn't handle Xorg v1.8. One guy has gone to the trouble of patching xorg 1.8 to fool the fglrx driver into thinking that it is really 1.7. Otherwise normal folks like us just wait until ATI release a version with the new xorg and or kernel support built in.

---

### Post by waynefoutz on 2010-06-16
> **rtool said:**
> If im better off just using lucid then how can i get the 3d to work better? I'm trying to play WoW and it's not working.

If you want to play WoW, and you have a card that old that requires the 9.3 driver, your choices are pretty much limited to either installing Ubuntu 8.04, dual booting Windows, or upgrading your hardware. The open source drivers that replace it aren't very functional with 3d and WINE just yet. If you do anage to get it running your framerate will still be pretty bad.

---

### Post by waynefoutz on 2010-06-16
> **alphacrucis2 said:**
> Well I suppose they could provide backwards compatibility for old ATI drivers by providing some sort of wrapper but I don't know how hard this would be. The current Maverick Meerkat alpha has already broken support for Catalyst 10.5 because Catalyst 10.5 doesn't handle Xorg v1.8. One guy has gone to the trouble of patching xorg 1.8 to fool the fglrx driver into thinking that it is really 1.7. Otherwise normal folks like us just wait until ATI release a version with the new xorg and or kernel support built in.

ATI stopped giving their older cards Linux support right after AMD bought them out. It's enraging. What's even more enraging is that they are still shipping out new lower end laptops and netbooks that have ATI GPUs that are on ATI's obsolete list.

---

### Post by amohell on 2010-06-20
You can add the packages:

[LIST]
[*]fglrx
[*]fglrx-amdcccle
[/LIST]
With Synaptic, then reboot. This won't update the driver, but you will be able to edit the resolution. For me this was important because working with 800x600 is terrible. I hope there will become a better solution for older cards!

---

### Post by phr0ze on 2010-06-21
You need 
```
sudo chmod +x [filename]
```

Then it will run with the sudo ./[filename]

---

