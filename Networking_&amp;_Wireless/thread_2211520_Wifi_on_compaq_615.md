---
title: "Wifi on compaq 615"
date: 2014-03-16
forum: Networking &amp; Wireless
---

### Post by K_Christensen on 2014-03-16
[FONT=arial]Trying to detect what wlan card is present in my compaq 615 

so from scratch :-) what to write in terminal ??

I have been trying looking in to this  [http://ubuntuforums.org/showthread.php?t=1645226](http://ubuntuforums.org/showthread.php?t=1645226)

but when typing the :[/FONT]
lspci | grep Network

[FONT=arial]i get no answer ... and im lost 

im frustrated -now i will work on my cit DS to get angry in a green way ;)[/FONT]

---

### Post by deadflowr on 2014-03-16
If lspci | grep whatever doesn't show anything, then
simply
```
lspci
```

post the output this.
It'll be longer, but still...

---

### Post by pqwoerituytrueiwoq on 2014-03-16
```
lspci |egrep -i "Network|Wireless|Ethernet|802.11"
```
should be overkill for finding the network cards
did you check additional drivers?

---

### Post by K_Christensen on 2014-03-16
Roger that :
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS780M [Mobility Radeon HD 3200]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8042 PCI-E Fast Ethernet Controller (rev 10)


I better begin to look in to some linux commands :P

---

### Post by K_Christensen on 2014-03-16
> **pqwoerituytrueiwoq said:**
> ```
lspci |egrep -i "Network|Wireless|Ethernet|802.11"
```
should be overkill for finding the network cards
did you check additional drivers?


NOPE ! im on thin ice so i do as im told :rolleyes:.. learning by doing ... and something deep in there say that its not a good idea just to install "things"
Windows sarcasm off ...

---

### Post by Vladlenin5000 on 2014-03-16
As far as network devices go, the result of lspci shows an Ethernet controller only. 
According to HP, the Compaq 615 should have one of the following cards:

1. [I]Broadcom 4312G 802.11b/g WiFi Adapter
2. Broadcom 4322AGN 802.11a/b/g/draft-n WiFi Adapter
[/I]
We know that either one requires some tweaking in order to work in Ubuntu. Nevertheless, the one you have - assuming you have one in working condition - should have been listed. Are you sure it was working before you installed Ubuntu?

---

### Post by K_Christensen on 2014-03-16
YEP The card was working without any problems what so ever...(4 hours ago )
There is a little button over the keyboard whre i normaly could turn the wifi on/off its now orange (off) and i cant turn it on... But as i recall the same thing happend in windows after a breakdown where the driver broke.. SO ! with the right driver i might be able to turn the card on...
 Makes sence ?

---

### Post by Vladlenin5000 on 2014-03-16
Yes, it makes sense provided the card is working as it should. It depends on what you mean by "driver broke". Were you able to reinstall the driver and it worked?

---

### Post by K_Christensen on 2014-03-16
yes its way back (2 years or more) the card was working until i formated hd/installed Ubuntu today 5 hours ago :-)

---

### Post by Hadaka on 2014-03-16
hi, lets see what cards show up with this command
pleas COPY  and paste the following into a terminal..
```
lspci -nnk | egrep '0200|0280'
lsusb
lsmod
rfkill list all
```
what EXACTLY were you doing when this broke??

---

### Post by K_Christensen on 2014-03-16
when what brooke ? the wifi connection broke(driver stopped working) years ago running VISTA i think it was an suddently power loss that made the insident cant remember.. and i dont see the point (soory) in what happend years ago??  The card and connection worked fine 5 hours ago running vista for the last time when i made backup to server ..


terminal show :
Bus 002 Device 002: ID 04f2:b159 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
kuno@Compaq615:~$ lsmod
Module                  Size  Used by
dm_crypt               23111  1 
bnep                   24107  2 
rfcomm                 74718  0 
bluetooth             391726  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17711  0 
joydev                 17613  0 
snd_hda_codec_idt      55053  1 
snd_hda_intel          53038  3 
uvcvideo               82247  0 
snd_hda_codec         194727  2 snd_hda_codec_idt,snd_hda_intel
videobuf2_core         40815  1 uvcvideo
videodev              138562  2 uvcvideo,videobuf2_core
hp_wmi                 18202  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30416  1 snd_seq_midi
sparse_keymap          13890  1 hp_wmi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 37201  0 
snd                    73753  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse               104093  0 
soundcore              12680  1 snd
sp5100_tco             14114  0 
k10temp                13173  0 
serio_raw              13413  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
lp                     17799  0 
mac_hid                13253  0 
i2c_piix4              22299  0 
parport                42466  3 parport_pc,ppdev,lp
radeon               1447330  3 
ttm                    84837  1 radeon
drm_kms_helper         53237  1 radeon
drm                   306660  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13564  1 radeon
video                  19574  0 
ahci                   30063  2 
wmi                    19256  1 hp_wmi
sky2                   59109  0 
libahci                32118  1 ahci

---

### Post by Vladlenin5000 on 2014-03-16
If you still have Windows boot it, make sure the WiFi in on and working and reboot leaving it on. Some card won't work otherwise.

---

### Post by K_Christensen on 2014-03-16
no windows!! made a total install from usb ... Where is the warning sign on ubunto installer for this little fresh "thing" hmmm

---

### Post by Vladlenin5000 on 2014-03-16
Err... I just told you from memory something often mentioned in thread about the aforementioned WiFi cards - one of then should be yours, unless replaced, not original - but I'm no expert, far from it. However, IMHO, Ubuntu having a warning for every *kinky* hardware behavior out there would be insane. Windows, MacOS, etc. don't have it, why should Ubuntu/Linux?

The first problem I see here is that so far your card hasn't been listed. I guess your last posted output start with lsusb, right? The card is internal and should have been listed by lspci...  - BTW, are you sure it isn't disable in BIOS? - Even when switched off by hard witch or keyboard the card should be listed.

---

### Post by K_Christensen on 2014-03-16
Disabel in bios ? How to check - on start up ?? 
And no off course they cant warn about every little bit of this and that .... But still, it should be ohhh so good and i start with major problem ( missing wifi in 2014 IS a major problem ;))

---

### Post by slooksterpsv on 2014-03-16
What version of Ubuntu (or variant) are you running?

What does **uname -a** output in terminal?

What does **dmesg | grep wifi** output in terminal?

---

### Post by K_Christensen on 2014-03-16
[h=3]12.04 LTS 64 bit[/h]hans@Compaq615:~$ uname -a

**uname -a** answers : Linux Compaq615 3.11.0-15-generic #25~precise1-Ubuntu SMP Thu Jan 30 17:39:31 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
[B]
dmesg | grep wifi [/B] come out emptyand**grep wifi **gives no answer terminal runs a process with no end

---

### Post by slooksterpsv on 2014-03-16
Wifi may be turned off or disabled in BIOS. Worst case scenario, the wifi's toast. Check the BIOS first and while in bios try to press the button to see if it turns it on (IF YOU HAVE indicator lights).

---

### Post by K_Christensen on 2014-03-16
And i get in BIOS how (Somekind of NooB)

---

### Post by slooksterpsv on 2014-03-16
When you turn on your computer keep pressing F10 - if F10 doesn't work, try F1 or DEL

---

### Post by K_Christensen on 2014-03-16
:D yep thats what i didt and it was not working....on  HP for some reason  press escape and THEN F10 ...tada...

And ... i changed the setting it was set to "ON" and the light in butten indicated "OFF" ... so now the light turns to "BLUE" witch is "ON" right at the beginning on start up- and as sone as ubunto kikcs in it shift to "ORANGE" witch is "OFF"..... 

SO ! card is working (i think - and why should it be toasted from a ubunto install ) but ubunto kills it.. missing driver ??

an earlier post claim that there can be only two drivers in play.. so not an over whelming task to test them both... how and where do i install (where is via terminal- but how ) 

OR.... what do i miss ...

---

### Post by slooksterpsv on 2014-03-16
If you can connect it to the internet via Ethernet, try the following:

If you open Ubuntu Software Center -> Edit -> Software Sources... -> Additional Drivers tab - does it show Broadcom STA in the list?
If there is anything saying Broadcom in the list, install it (unless there's multiple then just install 1). If after you install that it doesn't work let me know, otherwise if nothing showed up continue.

The indicators show that the Wifi is functioning, just not in Ubuntu. We can install some packages via terminal to see if I can get it working, if you run the following command:
**pkexec apt-get install broadcom-sta-common broadcom-sta-dkms bcmwl-kernelsource**

After that's installed, try running: 
**pkexec modprobe wl**

---

### Post by K_Christensen on 2014-03-16
well your guide to software center i dont quite understand ? i dont find an edit menu/button neither an additional drivers tab..
BUT i made a search on broadcom under susyem software and found "Broadcom 802.11 Linux STA wireless driver source" install and restart no change ...
there where some other broadcom things ... under systemsoftware

AND the terminal show:
@Compaq615:~$ pkexec apt-get install broadcom-sta-common broadcom-sta-dkms bcmwl-kernelsource
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ        
Læser tilstandsoplysninger... Færdig
E: Kunne ikke lokalisere pakken broadcom-sta-dkms
E: Kunne ikke lokalisere pakken bcmwl-kernelsource


Says . E: couldn't find the package broadcom-sta-dkms

---

### Post by slooksterpsv on 2014-03-16
Before running that run: **pkexec apt-get update**  then try to run those commands again.

---

### Post by K_Christensen on 2014-03-16
> **slooksterpsv said:**
> Before running that run: **pkexec apt-get update**  then try to run those commands again.

SAme answer after that : couldn't find the package broadcom-sta-dkms... ect ect

---

### Post by slooksterpsv on 2014-03-16
try **apt-cache search broadcom**

---

### Post by K_Christensen on 2014-03-16
> **slooksterpsv said:**
> try **apt-cache search broadcom**
YEP ! and "**pkexec apt-get install broadcom-sta-common broadcom-sta-dkms bcmwl-kernelsource" **stil same answer
...

---

### Post by pqwoerituytrueiwoq on 2014-03-16
connect to hardwire and run this
```
sudo apt-get update
```
i know with my old hp laptop the wifi indicator does not act right under linux, give it a press and see if it shows up in lspci

run this command
```
software-properties-gtk
```
look at the additional drivers tab, if you need a special driver that will tell you

---

### Post by K_Christensen on 2014-03-17
> **pqwoerituytrueiwoq said:**
> connect to hardwire and run this
```
sudo apt-get update
```
i know with my old hp laptop the wifi indicator does not act right under linux, give it a press and see if it shows up in lspci

run this command
```
software-properties-gtk
```
look at the additional drivers tab, if you need a special driver that will tell you


Hmm last command open software sources but i cant se any sign of something is missing ...

What commands in terminal to try the two drivers that can be in game for this laptop ?

---

