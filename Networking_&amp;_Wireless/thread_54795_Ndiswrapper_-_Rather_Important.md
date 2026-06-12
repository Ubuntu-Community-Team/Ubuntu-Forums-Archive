---
title: "Ndiswrapper - Rather Important"
date: 2005-08-06
forum: Networking &amp; Wireless
---

### Post by duminas on 2005-08-06
First off, I apologize for the thread title and if I come off as a bit rude during this post at all. I do not intend it, however, I am getting extremely aggrivated by Linux. I have also read the various HOWTOs on ndiswrapper and looked in the Wiki.

Some of you may also remember my posting a thread in here earlier; that is irrelevant to this one. I got a new device confirmed to work on the ndiswrapper listing.

Problem:
ndiswrapper (1.1, which comes with Ubuntu), along with the ndiswrapper-tools installed can install the driver (Mrv8000c.INF) perfectly fine via [font=Courier]ndiswrapper -i Mrv8000c.INF[/font]. Once I [font=Courier]ndiswrapper -l[/font] this, it shows as being installed and seeing hardware. So I go into the Networking utility, only to find that there is no wlan0 interface.

Okay, fine. [font=Courier]sudo modprobe ndiswrapper[/font]--or not. Doing this locks Ubuntu entirely. No mouse or keyboard response. Oh, and if I try to [font=Courier]ndiswrapper -m[/font], I get an error about the operation not being permitted. JOY. Reboot and the same happens. Now, IF I go grab the most recent tar of ndiswrapper (1.2) off of Sourceforge, I follow the HOWTO and install that (after getting rid of the current ndiswrapper).

This gets up to the [font=Courier]sudo modprobe ndiswrapper[/font] step fine. However, once I input that, it just... sits there, blinking at me. The cursor doesn't move. I installed *build-essential* and all dependencies fine, though I had to do it the .deb way, since I do not have internet at this time.

Anyone got a clue what the bloody world is going on?
I'd appreciate a response, as I **really** want to like Linux. I do, but having to go through five hundred hurdles to install my INTERNET is not cool, at all.

Oh, my device is a TEW-423PI. Ndiswrapper's list confirms it to work (both revisions, of which I have the B one).

Thanks for any help.

---

### Post by az on 2005-08-06
Right.  That card uses the Texas instruments chip (acx111)  It has native linux drivers which are being loaded for you by hotplug.  that is why ndiswrapper is not working.

The native driver did not support WEP when it was introduced into the ubuntu kernel.  That is probably why it didn't work for you out-of-the-box.  You need to tell hotplug to not load the4 acx111 knerle module when you boot so that the ndiswrapper module can take charge of the hardware

add the module name to 

/etc/hotplug/blacklist

---

### Post by duminas on 2005-08-06
[QUOTE=azz]Right.  That card uses the Texas instruments chip (acx111)  It has native linux drivers which are being loaded for you by hotplug.  that is why ndiswrapper is not working.

The native driver did not support WEP when it was introduced into the ubuntu kernel.  That is probably why it didn't work for you out-of-the-box.  You need to tell hotplug to not load the4 acx111 knerle module when you boot so that the ndiswrapper module can take charge of the hardware

add the module name to 

/etc/hotplug/blacklist[/QUOTE]
 This card is not using the Texas Instruments chip. This card is reported as being a Marvell.
Regardless, I added "acx111" to the end of blacklist, and that did not help at all.

I am not trying to use WEP, if that matters.

---

### Post by az on 2005-08-06
Actually, I should have written acx_pci.  My bad.  Amyway, please post the output of

lspci

and

lsmod

---

### Post by duminas on 2005-08-06
[QUOTE=azz]Actually, I should have written acx_pci.  My bad.  Amyway, please post the output of

lspci

and

lsmod[/QUOTE]
 lspci:
```
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev c1)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:07.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 1faa (rev 03)
0000:02:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0326 (rev a1)
```

lsmod:
```
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  9
af_packet              20744  2
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
snd_intel8x0           29984  2
driverloader          325264  0
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
ehci_hcd               29444  0
ohci_hcd               19848  0
i2c_nforce2             6400  0
i2c_core               21264  1 i2c_nforce2
nvidia_agp              7452  1
agpgart                31784  1 nvidia_agp
analog                 10784  0
gameport                4608  1 analog
pcspkr                  3816  0
rtc                    12216  0
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
evdev                   9088  0
tsdev                   7488  0
ndiswrapper           150964  0
usbcore               107384  5 driverloader,ehci_hcd,ohci_hcd,ndiswrapper
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  3
jbd                    54168  1 ext3
ide_generic             1664  0
ide_disk               18176  5
amd74xx                13340  1
ide_core              118988  4 ide_cd,ide_generic,ide_disk,amd74xx
unix                   26164  762
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
```
Note about lsmod: I'm using DriverLoader to use the internet on this machine right now, though I would like to get something, er... free working.

I'll go change the acx111 to acx_pci (though it's not even loading right now?).

---

### Post by az on 2005-08-06
driverloader          325264  0

Same thing.  You need to remove that module, reboot and then try ndiswrapper.  You cannot have both at the same time, as far as I know.

And no, it is not an acx111 chipset.  Bastard google!  Sorry.

---

### Post by duminas on 2005-08-06
[QUOTE=azz]driverloader          325264  0

Same thing.  You need to remove that module, reboot and then try ndiswrapper.  You cannot have both at the same time, as far as I know.


And no, it is not an acx111 chipset.  Bastard google!  Sorry.[/QUOTE]
 I just need to *sudo rmmod driverloader* , and reboot then, correct?
Apologies, but being new to this isn't helping me much. XD

-----
**EDIT:**
After rmmod'ing it, then *ndiswrapper -m*ing to write the changes, it works completely. Heck, even just running *modprobe ndiswrapper* after removing driverloader made it run.

Toodles, and thanks, azz.
You've allowed me to use Ubuntu. :)

---

### Post by duminas on 2005-08-07
Updating...
I got it working once before, but now it won't, since I had to reinstall after breaking something. I tried the same steps I took last time, but those (again) failed.

```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
```

Fun.
And I cannot for the life of me figure out how to fix that. Any ideas, guys? ;)

---

### Post by varunus on 2005-08-07
Make sure (by typing lsmod) that no other drivers are loaded for the card.  Also, did you use sudo when modprobing?  (sorry, know its a dumb question).

---

### Post by duminas on 2005-08-07
[QUOTE=varunus]Make sure (by typing lsmod) that no other drivers are loaded for the card.  Also, did you use sudo when modprobing?  (sorry, know its a dumb question).[/QUOTE]
 lsmod, at this point, returns:
```
Module                  Size  Used by
af_packet              20744  4
nls_cp437               5888  1
isofs                  33720  1
udf                    77060  0
ipv6                  229504  6
proc_intf               4100  0
cpufreq_powersave       1920  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
freq_table              4100  0
video                  16260  0
battery                10244  0
container               4608  0
button                  6800  0
pcc_acpi               11264  0
sony_acpi               6280  0
ac                      4996  0
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
ehci_hcd               29444  0
ohci_hcd               19848  0
usbcore               107384  4 ehci_hcd,ohci_hcd
i2c_nforce2             6400  0
i2c_core               21264  1 i2c_nforce2
nvidia_agp              7452  1
agpgart                31784  1 nvidia_agp
analog                 10784  0
gameport                4608  1 analog
pcspkr                  3816  0
rtc                    12216  0
ext3                  120968  1
jbd                    54168  1 ext3
md                     43856  0
dm_mod                 53116  1
tsdev                   7488  0
capability              5000  0
evdev                   9088  0
commoncap               7808  1 capability
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  1
cdrom                  36508  1 ide_cd
reiserfs              225616  2
ide_generic             1664  0
ide_disk               18176  5
amd74xx                13340  1
ide_core              118988  4 ide_cd,ide_generic,ide_disk,amd74xx
unix                   26164  736
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
```

And yes, I did use *sudo*.
Really not sure why it fails this time. :\

---

### Post by az on 2005-08-07
If you rmmod a module that was loaded at boot time, it will get loaded the next time you boot.  Is it loaded by hotplug or is it loaded by being listed in /etc/modules?


I would check in /etc/modules first...

---

