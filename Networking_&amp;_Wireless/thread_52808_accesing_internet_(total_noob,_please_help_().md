---
title: "accesing internet (total noob, please help :()"
date: 2005-07-29
forum: Networking &amp; Wireless
---

### Post by nighttime on 2005-07-29
Hey, how do I access the internet with ubuntu? I have an officeconnect cable modem but  I don't know anything about configuring networks in linux... help? anyone?

---

### Post by pestilence4hr on 2005-07-29
[QUOTE=nighttime]Hey, how do I access the internet with ubuntu? I have an officeconnect cable modem but  I don't know anything about configuring networks in linux... help? anyone?[/QUOTE]

You should check out what's under System -> Administration -> Networking.  You will want to enable the ethernet connection, and hopefully it will get a network address automatically and you will be good to go.

---

### Post by nighttime on 2005-07-29
okay, I'm using the network settings interface... how do I enable the ethernet connetion?

There's only a "modem connection" listed

I was told I had to add a connection but there is no add button in this interface.

---

### Post by pestilence4hr on 2005-07-29
[QUOTE=nighttime]okay, I'm using the network settings interface... how do I enable the ethernet connetion?

There's only a "modem connection" listed

I was told I had to add a connection but there is no add button in this interface.[/QUOTE]

If you could, please tell us the model of your network card.  The output of the command "lspci" and "lsmod" will also be helpful.

---

### Post by nighttime on 2005-07-29
I would love to except I don't know the model of my network card (I opened the computer up and all I found were this numbers on the side of the slot: p35-121-16b9) AND I'm running ubuntu in another computer and It doesn't seem to be able to write to a floppy so I can copy/paste the  result of lspci and lsmod here. The computer Im currenty using to access the internet has Win2000 Pro.

---

### Post by pestilence4hr on 2005-07-29
[QUOTE=nighttime]I would love to except I don't know the model of my network card (I opened the computer up and all I found were this numbers on the side of the slot: p35-121-16b9) AND I'm running ubuntu in another computer and It doesn't seem to be able to write to a floppy so I can copy/paste the  result of lspci and lsmod here. The computer Im currenty using to access the internet has Win2000 Pro.[/QUOTE]

So, on your computer that runs ubuntu, type lspci and look for the entry that says "ethernet controller".  Write it down, and post it here.

---

### Post by nighttime on 2005-07-29
there's no ethernet controller entry, there's just:

Host bridge
PCI bridge
ISA bridge
IDE interface
USB controller
Usb controller
Bridge
Multimedia audio controller
VGA compatible controller



oh. and here's the output of lsmod (I could finally write it to a floppy)

Module Size Used by
nls_cp437 5888 1 
msdos 8320 1 
fat 37792 1 msdos
ipv6 229504 6 
proc_intf 4100 0 
freq_table 4100 0 
cpufreq_userspace 4572 0 
cpufreq_ondemand 6172 0 
cpufreq_powersave 1920 0 
video 16260 0 
sony_acpi 6280 0 
pcc_acpi 11264 0 
button 6800 0 
battery 10244 0 
container 4608 0 
ac 4996 0 
snd_via82xx 25248 2 
snd_ac97_codec 64608 1 snd_via82xx
snd_pcm_oss 47652 1 
snd_mixer_oss 16768 2 snd_pcm_oss
snd_pcm 84872 3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer 23300 1 snd_pcm
snd_page_alloc 9604 2 snd_via82xx,snd_pcm
gameport 4608 1 snd_via82xx
snd_mpu401_uart 7168 1 snd_via82xx
snd_rawmidi 22944 1 snd_mpu401_uart
snd_seq_device 8332 1 snd_rawmidi
snd 50276 9 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_o ss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,s nd_seq_device
soundcore 9824 3 snd
i2c_viapro 7436 0 
i2c_core 21264 1 i2c_viapro
uhci_hcd 30224 0 
usbcore 107384 2 uhci_hcd
pci_hotplug 30512 0 
via_agp 9216 1 
agpgart 31784 1 via_agp
floppy 54864 1 
pcspkr 3816 0 
rtc 12216 0 
md 43856 0 
dm_mod 53116 1 
capability 5000 0 
commoncap 7808 1 capability
tsdev 7488 0 
evdev 9088 0 
psmouse 19336 0 
mousedev 11160 1 
parport_pc 34372 1 
lp 10792 0 
parport 33480 2 parport_pc,lp
ide_cd 38532 0 
cdrom 36508 1 ide_cd
ext3 120968 1 
jbd 54168 1 ext3
ide_generic 1664 0 
via82cxxx 12956 1 
ide_disk 18176 3 
ide_core 118988 4 ide_cd,ide_generic,via82cxxx,ide_disk
unix 26164 701 
thermal 13576 0 
processor 22708 1 thermal
fan 4612 0 
fbcon 34048 0 
font 8448 1 fbcon
bitblit 5120 1 fbcon
vesafb 6948 0 
cfbcopyarea 3968 1 vesafb
cfbimgblt 3072 1 vesafb
cfbfillrect 3584 1 vesafb

---

