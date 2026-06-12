---
title: "Asus P5B-MX WIFI-AP problems"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by j0sh0 on 2007-03-23
Hi guys!
I've got an ASUS P5-MX WIFI-AP mobo. I've got the gigabit ethernet working by compiling the drivers on the CD, however I'm stuck with even remotely getting the wifi working. If I"lshw", it says that the "unclaimed" network is an Atheros chipset, but everything else I've read about the ASUS WIFI-AP seems to be a realtek 8187 chipset. How do I force Ubuntu to load the realtek drivers instead of the Atheros ones? "lsmod" or "modprobe" or whichever one it is lists the ath_pci etc modules, so how do I make it load the realtek ones (and how do I search the available modules list to select the correct name??)?

Please guys/gals, I'm in dire need of some advice and I know this is the best place to look!

Cheers!

---

### Post by chili555 on 2007-03-23
I suggest doing:```
sudo lspci -vv
```You do NOT have to post the whole thing here, just the part about your wireless card. In my experience, cards do not report themselves as A when they are actually B. I learn something new every day, however, so this could be it!

Sometimes more than one driver will work with a single card, but not, as far as I know, across families. An rt.whatever module might work as well, or better than a rt.newdriver.

I recently installed Feisty Herd 5 in one of my laptops and was surprised to see this in  /etc/modprobe.d/blacklist, the file which *prohibits* modules from being loaded, ever:```
# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
```So I would be extremely cautious before I messed around with r8187.

Post back your findings and let's see if we can get it going.

---

### Post by j0sh0 on 2007-03-24
Thanks for the reply chili555!

I'm beginning to think that it may actually be an Atheros chipset after all - like you said, why would it report Atheros if its Realtek? Anyhow, I've looked thru some of the system info stuff and here's my findings - hopefully something will give us a clue!

"dmesg":
wifi%d: unable to attach hardware: 'Hardware Revision not supported' (HAL status 13)
ACPI: pci interrupt for device 0000:02:00.0 disabled

"lspci":
02:00.0 Ethernet Controller: Atheros Communications, Inc Unknown device 001c (revision 01)

"lshw":
-network UNCLAIMED
   description: Ethernet Controller
   product: Atheros Communications, Inc
   vendor: Atheros Communications, Inc
   physical Id: 0
   bus info: pci@02:00.0
   version: 01
   width: 64 bits
   clock: 33 Mhz
   capabilities: cap_list
   resources: iomemory: feaf0000-feafffff irq:185

So, there's the low-down. I've tried booting with grub options "pci=routeirq" and "pci=noacpi" however neither makes any difference. Hopefully the messaged above help shed some light!

Thanks for the help!

---

### Post by chili555 on 2007-03-24
Do you have linux-restricted-modules installed? Please do so, if not already and post back the relevant section of sudo lspci -vv.

---

### Post by j0sh0 on 2007-03-24
Chil555

Yeah, I'm pretty sure the module is installed as ls lsmod list ath_pci and other atheros-based modules. Any other ideas? I can't even find anywhere on the asus (or atheros) site which says what chipset it uses!! Very frustrating!

---

### Post by j0sh0 on 2007-03-25
Just an update for anyone interested - I'm sure it must be an atheros-based card. Since the cmputer is dual boot, looking at what XP reports about the card its an Atheros 5006 chipset (chip?).  So, I gave the latest madwifi drivers a go: compiled and installed them, but unfortunately still no go, the same error reported (again trying the boot options as well). Then I tried using ndiswrapper with the XP .inf and .sys files that are provided on the CD, however that was unsuccessful too, although I'm not sure I did it correctly ("ndiswrapper -i [.inf file]",then "ndiswrapper -l" reports "driver present: hardware present", but I still cant bring wlan0 or ath0 up) . 

So, I'm still stuck with a brand new computer I was so excited about running Ubuntu on, with the main feature not available (in linux). :(

Anyone with some advice or ideas would be much appreciated!

---

### Post by chili555 on 2007-03-25
Well, let's go back to basics. May we see:```
sudo iwconfig
sudo iwlist wlan0 scan
```We'll get it.

---

### Post by j0sh0 on 2007-03-27
Hey chili555 thanks for your efforts, mate!

Umm, iwconfig lists no interfaces with wireless extensions, and i cant even bring wlan0 up with ifconfig - it says something about no device or whatever the error message is (same as before I tried using ndiswrapper). 

Incidentally, here is the output from dmesg when booting with the ndiswrapper module:
ndiswrapper version 1.22 loaded (preempt=no, smp=yes)
ndiswrapper (import:241): unknown symbol: ntoskrnl.exe:'ZwDeleteKey'
ndiswrapper (import:241): unknown symbol: ntoskrnl.exe: 'RtlCharToInteger'
ndiswrapper (load_sys_files:215): couldn't prepare driver
ndiswrapper (load_wrap_driver:113): load ndiswrapper failed (65280);

Any ideas?

Cheers

---

### Post by stchman on 2007-03-30
> **j0sh0 said:**
> Hi guys!
I've got an ASUS P5-MX WIFI-AP mobo. I've got the gigabit ethernet working by compiling the drivers on the CD, however I'm stuck with even remotely getting the wifi working. If I"lshw", it says that the "unclaimed" network is an Atheros chipset, but everything else I've read about the ASUS WIFI-AP seems to be a realtek 8187 chipset. How do I force Ubuntu to load the realtek drivers instead of the Atheros ones? "lsmod" or "modprobe" or whichever one it is lists the ath_pci etc modules, so how do I make it load the realtek ones (and how do I search the available modules list to select the correct name??)?

Please guys/gals, I'm in dire need of some advice and I know this is the best place to look!

Cheers!

If it truly is an Atheros wireless card then use my procedure to install the madwifi drivers.  Realtek may use the Atheros chips for their wireless cards.

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

It worked with my laptop.

---

### Post by j0sh0 on 2007-04-05
stchman,
what is the point of installing the shareutils when compiling the madwifi drivers?? what do they do?

Cheers

---

### Post by stchman on 2007-04-16
> **j0sh0 said:**
> stchman,
what is the point of installing the shareutils when compiling the madwifi drivers?? what do they do?

Cheers

According to Madwifi and other wikis sharutils is a required package to make madwifi.

[https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi](https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi)

It is required for Dapper.  Edgy supposedly comes with madwifi enabled on the restriced kernels.  It is for the older Atheros cards but the newer ones require the latest madwifi drivers.

---

