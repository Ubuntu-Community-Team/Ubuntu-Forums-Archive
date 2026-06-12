---
title: "cannot get computer to recognize wireless signals"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by greyluver on 2011-07-05
Hello,I have an older gateway laptop from around 2002 that was retired for a few years until yesterday. Yesterday, i tried booting it up and to my surprise, it worked. I have only Ubuntu 11.04 on it- no windows dual-boot. Next, i tried to connect wirelessly to the internet, but it said I was missing some firmware, so i downloaded that and it doesn't say that anymore. Now, it just doesn't recognize that there is a wireless signal. I know the wireless works because i have another laptop connected to it. Any tips for getting it connected?
P.S. i have very little experience with linux.

---

### Post by candtalan on 2011-07-05
Welcome!
Try 'hardware drivers' and see if you now can or now have to enable a particular driver, which seems to be already downloaded, but maybe not enabled.
In classic gui
System>Administration>hardware drivers

---

### Post by wildmanne39 on 2011-07-06
> **greyluver said:**
> Hello,I have an older gateway laptop from around 2002 that was retired for a few years until yesterday. Yesterday, i tried booting it up and to my surprise, it worked. I have only Ubuntu 11.04 on it- no windows dual-boot. Next, i tried to connect wirelessly to the internet, but it said I was missing some firmware, so i downloaded that and it doesn't say that anymore. Now, it just doesn't recognize that there is a wireless signal. I know the wireless works because i have another laptop connected to it. Any tips for getting it connected?
P.S. i have very little experience with linux.
Hi, you will have to be connected to the internet with your lan connection before you check additional drivers to see if there is one there for your wireless card, also put these commands in a terminal
```
lspci -nn
```
```
iwconfig
```
```
lsmod
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by greyluver on 2011-07-06
Well, when i went to additional drivers (there was no hardware drivers) it said i had a broadcom driver that was activated and in use, but the software modem was activated but not in use.

after typing lspci -nn i got

```
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 83)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:09.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
08:09.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
08:09.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
```

after typing iwconfig i got

```
lo        no wireless extensions.

eth0      no wireless extensions.
```


after typing lsmod i got

```
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_atiixp_modem       18624  0 
snd_via82xx_modem      18305  0 
snd_intel8x0m          18493  0 
snd_hda_codec_si3054    12924  1 
snd_hda_codec_idt      60537  1 
joydev                 17322  0 
snd_ac97_codec        105614  3 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_si3054,snd_hda_codec_idt,snd_hda_intel
radeon                896428  3 
ac97_bus               12642  1 snd_ac97_codec
snd_hwdep              13274  1 snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ttm                    65184  1 radeon
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                80244  7 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_hda_codec_si3054,snd_ac97_codec,snd_hda_intel,snd_hda_codec
pcmcia                 39671  0 
snd_timer              28659  2 snd_pcm,snd_seq
drm_kms_helper         40745  1 radeon
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   180037  5 radeon,ttm,drm_kms_helper
wl                   2642531  0 
tifm_7xx1              12898  0 
yenta_socket           27230  0 
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
snd                    55295  18 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_hda_codec_si3054,snd_hda_codec_idt,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
video                  18951  0 
tifm_core              15040  1 tifm_7xx1
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
k8temp                 12872  0 
serio_raw              12990  0 
i2c_algo_bit           13184  1 radeon
shpchp                 32345  0 
soundcore              12600  1 snd
snd_page_alloc         14073  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_hda_intel,snd_pcm
lib80211               14570  1 wl
ati_agp                13202  0 
i2c_piix4              13095  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
sky2                   49172  0 
crc_itu_t              12627  1 firewire_core
pata_atiixp            12968  2 
```

---

### Post by wildmanne39 on 2011-07-06
Hi, here is a link that should get your wireless working.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)
Follow the directions for the 4311 card.

---

### Post by greyluver on 2011-07-07
Thanks for all the help.  I did the first thing where you type in a command, then take off anything with bcm and a green box to the side of it, restarted, and put stuff back on, then restarted, and nothing had changed. i then went through the troubleshooting stuff, but those commands didn't do anything. (or at least it didn't have any output)

---

### Post by wildmanne39 on 2011-07-07
> **greyluver said:**
> Thanks for all the help.  I did the first thing where you type in a command, then take off anything with bcm and a green box to the side of it, restarted, and put stuff back on, then restarted, and nothing had changed. i then went through the troubleshooting stuff, but those commands didn't do anything. (or at least it didn't have any output)
Hi, this is the only thing that you should have install in the bcm section of synaptic, I am attaching a screenshot. Also after you restart you may have to go into additional drivers and activate the driver, I am  not sure about that though. After you have the b43fwcutter and the driver in additional drivers active go to the top right of the screen and click on the network icon,make sure wireless is enabled, and you will have to enter you router password.

---

### Post by wildmanne39 on 2011-07-07
Heres the screenshot.

---

### Post by greyluver on 2011-07-07
I downloaded the b43 installer thing, then restarted, checked additional drivers and didn't see that i needed to activate it, but saw that my software modem still says activated but not in use. I then checked the wireless and didn't see any networks. Do I just need to somehow get my software modem to be in use?

---

### Post by wildmanne39 on 2011-07-08
> **greyluver said:**
> I downloaded the b43 installer thing, then restarted, checked additional drivers and didn't see that i needed to activate it, but saw that my software modem still says activated but not in use. I then checked the wireless and didn't see any networks. Do I just need to somehow get my software modem to be in use?Hi, where does it say not in use can you give me a screenshot or explain?

---

### Post by greyluver on 2011-07-08
The screenshot should be attached.

---

### Post by wildmanne39 on 2011-07-08
> **greyluver said:**
> The screenshot should be attached.Hi, that picture shows the green dots, it is in use I am pretty sure, people with video card drivers in additional drivers have the same problem but it is just a bug that shows not in use when it really is. I have not used a laptop with wireless in a while but I have that same wireless card in a laptop and I do not think it shows as modem. I think is shows as wireless card or something like that. Run this command again now that you have installed the firmware.
```
iwconfig
```

---

### Post by greyluver on 2011-07-09
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


Thanks for all of the help and patience.

---

### Post by wildmanne39 on 2011-07-09
> **greyluver said:**
> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


Thanks for all of the help and patience.

Hi, when you click on the network icon in the top right corner is enable wireless checked? or is it grayed out? If you can in the same window it says edit connections, click on it and see if you can set up your wireless.

---

### Post by westie457 on 2011-07-09
Apologies wildmanne39 for butting in.

If the OP has already installed 'b43-fwcutter' and 'firmware-b43-installer' they should remove or deactivate the 'Broadcom STA Wireless Driver from Additional Drivers and reboot. All should be fine. If not then in a terminal run ```
rfkill list
```

If any output run ```
rfkill unblock all
```

if still no wireless we will need to look at the mod. More information here [http://ubuntuforums.org/showpost.php?p=10801185&postcount=240](http://ubuntuforums.org/showpost.php?p=10801185&postcount=240)

---

### Post by wildmanne39 on 2011-07-09
> **westie457 said:**
> Apologies wildmanne39 for butting in.

If the OP has already installed 'b43-fwcutter' and 'firmware-b43-installer' they should remove or deactivate the 'Broadcom STA Wireless Driver from Additional Drivers and reboot. All should be fine. If not then in a terminal run ```
rfkill list
```

If any output run ```
rfkill unblock all
```

if still no wireless we will need to look at the mod. More information here [http://ubuntuforums.org/showpost.php?p=10801185&postcount=240](http://ubuntuforums.org/showpost.php?p=10801185&postcount=240)Hi, your right he told me he followed the directions for doing that in the link I gave him, but he may have missed that part.

---

### Post by westie457 on 2011-07-09
> **wildmanne39 said:**
> Hi, your right he told me he followed the directions for doing that in the link I gave him, but he may have missed that part.

It is easily done. Have missed something several times before now and nearly turned the box into a paperweight or half a boomerang (thrown it out the window).

---

### Post by wildmanne39 on 2011-07-09
> **westie457 said:**
> It is easily done. Have missed something several times before now and nearly turned the box into a paperweight or half a boomerang (thrown it out the window).Hi, I understand, please feel free to jump in here and help anytime, I appreciate it.

---

### Post by greyluver on 2011-07-09
Guess who is typing this without a blue chord attatched to this laptop?  It turned out all i had to do was take off the broadcom thing and reinstall the b43fwcutter and b43 installer (my sister took them off for some reason).
Thanks!

---

### Post by wildmanne39 on 2011-07-09
> **greyluver said:**
> Guess who is typing this without a blue chord attatched to this laptop?  It turned out all i had to do was take off the broadcom thing and reinstall the b43fwcutter and b43 installer (my sister took them off for some reason).
Thanks!Hi, thats great,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

