---
title: "Drivers for Nvidia xfx 6600gt"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by Jon Anderson on 2011-02-18
Thanks for the response I have a Nvidia xfx 6600gt coming and I looked on Nvidia page to install drivers and I read a couple of confusing install pages and at the end it had a hypertext that said ,read me,So I hit it and it went to a set of directions that was just  a little smaller than War and Peace. If I run into those type of problems, my new 6600 will not get up and running. Can someone give me a few words of hope?

---

### Post by sandyd on 2011-02-18
> **Jon Anderson said:**
> Thanks for the response I have a Nvidia xfx 6600gt coming and I looked on Nvidia page to install drivers and I read a couple of confusing install pages and at the end it had a hypertext that said ,read me,So I hit it and it went to a set of directions that was just  a little smaller than War and Peace. If I run into those type of problems, my new 6600 will not get up and running. Can someone give me a few words of hope?

just go to system -> administration -> hardware drivers after you install the card.
click activate.
done.

and the power just went out just as I hit "post".

---

### Post by Jon Anderson on 2011-02-19
[QUOTE=sandyd;10472131]just go to system -> administration -> hardware drivers after you install the card.
click activate.
done.

and the power just went out just as I hit "post".[/QUOTE
I went to additional drivers and there is nothing listed in there, it just say "no proprietary drivers"at the top of the page. So how do I get my needed drivers "260.19.36 for linux" into additional drivers application so that it can load them?

---

### Post by cascade9 on 2011-02-20
You cant install the drivers untill you install the card. 

BTW, you wont 'need' the 260.xx series drivers. With 10.10 "system -> administration -> hardware drivers" will get the 260.19.06 drivers, with 10.04 you will get 195.36.15 drivers.

---

### Post by 3rdalbum on 2011-02-20
> 
I went to additional drivers and there is nothing listed in there, it just say "no proprietary drivers"at the top of the page. So how do I get my needed drivers "260.19.36 for linux" into additional drivers application so that it can load them?

It only lists drivers for hardware that's currently installed.

The Additional Drivers program will download the driver for you.

---

### Post by Jon Anderson on 2011-02-22
> **3rdalbum said:**
> It only lists drivers for hardware that's currently installed.

The Additional Drivers program will download the driver for you.

It doesn't list anything, drivers that I will need or drivers for the hardware that is currently installed, It lists nothing. I would like to see what drivers are being used by my hardware now. Is there a program that does that.

---

### Post by alphacrucis2 on 2011-02-22
> **Jon Anderson said:**
> It doesn't list anything, drivers that I will need or drivers for the hardware that is currently installed, It lists nothing. I would like to see what drivers are being used by my hardware now. Is there a program that does that.

lsmod

---

### Post by Jon Anderson on 2011-02-23
> **alphacrucis2 said:**
> lsmod

Thanks for the response,what the hell does it mean

---

### Post by cascade9 on 2011-02-23
It means 'go to terminal, then type 'lsmod', then hit enter (you might need sudo, I'm not sure). You'll get a readout like this- 

```
Module                  Size  Used by
powernow_k8            13403  1 
mperf                   1227  1 powernow_k8
cpufreq_conservative     8596  0 
cpufreq_stats           2920  0 
cpufreq_performance      946  0 
cpufreq_ondemand        8238  1 
freq_table              2339  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave        942  0 
parport_pc             30780  0 
ppdev                   5918  0 
lp                      9761  0 
parport                27971  3 parport_pc,ppdev,lp
sco                     8678  2 
bnep                   10498  2 
rfcomm                 34093  0 
l2cap                  40982  6 bnep,rfcomm
bluetooth              51699  6 sco,bnep,rfcomm,l2cap
rfkill                 15344  2 bluetooth
af_packet              19786  2 
fuse                   63553  1 
dm_crypt               12235  0 
snd_hda_codec_analog    70162  1 
snd_hda_intel          21682  0 
snd_hda_codec          76650  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5804  1 snd_hda_codec
snd_pcm                69167  2 snd_hda_intel,snd_hda_codec
snd_seq                47421  0 
snd_timer              18197  2 snd_pcm,snd_seq
snd_seq_device          5029  1 snd_seq
tpm_tis                 7717  0 
tpm                    10141  1 tpm_tis
rtc_cmos                9054  0 
rtc_core               12933  1 rtc_cmos
shpchp                 25131  0 
rtc_lib                 1857  1 rtc_core
i2c_nforce2             5016  0 
pci_hotplug            22730  1 shpchp
tpm_bios                4785  1 tpm
snd                    52716  8 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
pcspkr                  1771  0 
i2c_core               18092  1 i2c_nforce2
amd64_edac_mod         15825  0 
processor              25440  1 powernow_k8
asus_atk0110            9734  0 
edac_core              34403  3 amd64_edac_mod
k8temp                  3291  0 
evdev                   8180  10 
edac_mce_amd            7009  1 amd64_edac_mod
button                  4594  0 
soundcore               5423  1 snd
snd_page_alloc          6881  2 snd_hda_intel,snd_pcm
ext4                  244554  2 
mbcache                 5522  1 ext4
jbd2                   53949  1 ext4
crc16                   1311  2 l2cap,ext4
dm_mod                 64586  1 dm_crypt
nbd                     8697  0 
usbhid                 35269  0 
hid                    75609  1 usbhid
sg                     21217  0 
sd_mod                 26890  4 
sr_mod                 14051  0 
cdrom                  34100  1 sr_mod
ata_generic             3055  0 
pata_acpi               3232  0 
ohci_hcd               23033  0 
pata_amd               10860  3 
ssb                    44772  1 ohci_hcd
libata                156627  3 ata_generic,pata_acpi,pata_amd
ehci_hcd               36837  0 
mmc_core               59638  1 ssb
usbcore               135848  4 usbhid,ohci_hcd,ehci_hcd
scsi_mod              138901  4 sg,sr_mod,sd_mod,libata
pcmcia                 34318  1 ssb
forcedeth              52275  0 
floppy                 57089  0 
thermal                 7410  0 
pcmcia_core            11773  1 pcmcia
nls_base                6657  1 usbcore

```

---

### Post by Jon Anderson on 2011-02-23
> **cascade9 said:**
> It means 'go to terminal, then type 'lsmod', then hit enter (you might need sudo, I'm not sure). You'll get a readout like this- 

```
Module                  Size  Used by
powernow_k8            13403  1 
mperf                   1227  1 powernow_k8
cpufreq_conservative     8596  0 
cpufreq_stats           2920  0 
cpufreq_performance      946  0 
cpufreq_ondemand        8238  1 
freq_table              2339  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave        942  0 
parport_pc             30780  0 
ppdev                   5918  0 
lp                      9761  0 
parport                27971  3 parport_pc,ppdev,lp
sco                     8678  2 
bnep                   10498  2 
rfcomm                 34093  0 
l2cap                  40982  6 bnep,rfcomm
bluetooth              51699  6 sco,bnep,rfcomm,l2cap
rfkill                 15344  2 bluetooth
af_packet              19786  2 
fuse                   63553  1 
dm_crypt               12235  0 
snd_hda_codec_analog    70162  1 
snd_hda_intel          21682  0 
snd_hda_codec          76650  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5804  1 snd_hda_codec
snd_pcm                69167  2 snd_hda_intel,snd_hda_codec
snd_seq                47421  0 
snd_timer              18197  2 snd_pcm,snd_seq
snd_seq_device          5029  1 snd_seq
tpm_tis                 7717  0 
tpm                    10141  1 tpm_tis
rtc_cmos                9054  0 
rtc_core               12933  1 rtc_cmos
shpchp                 25131  0 
rtc_lib                 1857  1 rtc_core
i2c_nforce2             5016  0 
pci_hotplug            22730  1 shpchp
tpm_bios                4785  1 tpm
snd                    52716  8 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
pcspkr                  1771  0 
i2c_core               18092  1 i2c_nforce2
amd64_edac_mod         15825  0 
processor              25440  1 powernow_k8
asus_atk0110            9734  0 
edac_core              34403  3 amd64_edac_mod
k8temp                  3291  0 
evdev                   8180  10 
edac_mce_amd            7009  1 amd64_edac_mod
button                  4594  0 
soundcore               5423  1 snd
snd_page_alloc          6881  2 snd_hda_intel,snd_pcm
ext4                  244554  2 
mbcache                 5522  1 ext4
jbd2                   53949  1 ext4
crc16                   1311  2 l2cap,ext4
dm_mod                 64586  1 dm_crypt
nbd                     8697  0 
usbhid                 35269  0 
hid                    75609  1 usbhid
sg                     21217  0 
sd_mod                 26890  4 
sr_mod                 14051  0 
cdrom                  34100  1 sr_mod
ata_generic             3055  0 
pata_acpi               3232  0 
ohci_hcd               23033  0 
pata_amd               10860  3 
ssb                    44772  1 ohci_hcd
libata                156627  3 ata_generic,pata_acpi,pata_amd
ehci_hcd               36837  0 
mmc_core               59638  1 ssb
usbcore               135848  4 usbhid,ohci_hcd,ehci_hcd
scsi_mod              138901  4 sg,sr_mod,sd_mod,libata
pcmcia                 34318  1 ssb
forcedeth              52275  0 
floppy                 57089  0 
thermal                 7410  0 
pcmcia_core            11773  1 pcmcia
nls_base                6657  1 usbcore

```

Thanks lots, I found my sound drivers but no video drivers using lsmad and that is what I need. Someone gave me lines to find out my video card driver number and my sound card drivers, it showed me my sound card drivers but it wouldn't work for my video drivers. In synaptic package manager it has the drivers for my video card  that is the latest version ,listed in latest version and it says it is the one that is installed also. I'm still having trouble with my system freezing. My question is ,in synaptic package manager do you think that when it says installed version do you think it is set in the video card as the drivers or do you think it means that it is just in the synaptic package manager and still needs to be loaded into the video card. I'm quite apprehensive about loading any drivers because if there's a problem my limited knowledge will just get me in trouble, I've been using ubuntu for 10 days.

---

### Post by cascade9 on 2011-02-24
Is that running the unichrome pro you mentioned in a different thread? 

[http://ubuntuforums.org/showthread.php?p=10461366#post10461366](http://ubuntuforums.org/showthread.php?p=10461366#post10461366)

If you are using unichrome video, I'm not that suprised that you are getting issues. They were pretty bad cards, S3/VIA never really gave much linux support for them, and the open soruce drivers are reverse engineered. 

If you have the xserver-xoeg-video-openchrome package installed in synaptic, thats the driver you should be using (you dont need to install it, the system does that automatically for you). 

Once you get the 6600GT you should have no problems. ;)

---

### Post by Jon Anderson on 2011-02-24
> **cascade9 said:**
> Is that running the unichrome pro you mentioned in a different thread? 

[http://ubuntuforums.org/showthread.php?p=10461366#post10461366](http://ubuntuforums.org/showthread.php?p=10461366#post10461366)

If you are using unichrome video, I'm not that suprised that you are getting issues. They were pretty bad cards, S3/VIA never really gave much linux support for them, and the open soruce drivers are reverse engineered. 

If you have the xserver-xoeg-video-openchrome package installed in synaptic, thats the driver you should be using (you dont need to install it, the system does that automatically for you). 

Once you get the 6600GT you should have no problems. ;)

  Thanks Cascade, my 6600 will be here in  three days. Kind of tired of rebooting.

---

