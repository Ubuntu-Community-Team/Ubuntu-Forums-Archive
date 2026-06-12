---
title: "Getting TV card To Work"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by izh34 on 2010-05-28
I have Gigabyte Global TV card model:** GT-PTV-AF-RH-GB1** installed in my PC. It just that I don't know how to make it works in Ubuntu 10.04. I had installed TVTime but it seems nothing happen. I also can't get any FMradio channels with Rythmbox.

It works in Windows with Cyberlink as it software. So any ideas I can make it work in Ubuntu? I really want to watch tv in Ubuntu.

---

### Post by inameiname on 2010-05-28
This is how I got tvtime to work for mine. Just check these two links out:


[http://ubuntuforums.org/showthread.php?t=1477837](http://ubuntuforums.org/showthread.php?t=1477837)

[http://ubuntuforums.org/showthread.php?t=1472297](http://ubuntuforums.org/showthread.php?t=1472297)


Oh, and it'll also depend on what sort of tv tuner you have. TVtime only does analog cable, or if you have any rca or s-video inputs, not digital cable. That requires the mplayer or vlc player or something else.

---

### Post by izh34 on 2010-05-28
> **inameiname said:**
> 
Oh, and it'll also depend on what sort of tv tuner you have. TVtime only does analog cable, or if you have any rca or s-video inputs, not digital cable. That requires the mplayer or vlc player or something else.


Mine use antenna. Still, can it work?

---

### Post by WinterRain on 2010-05-28
> **izh34 said:**
> Mine use antenna. Still, can it work?

Yes.

---

### Post by inameiname on 2010-05-30
Yes, however, I think TVTime won't work for the antenna feed (presumably digital over-the-air channels), just analog cable. I'm guessing it used to work just fine, but as you know ever since all broadcast over-the-air became strictly digital, there are no longer any analog broadcast stations floating around. Well, at least in the US....and no including the really small stations that are still broadcasting in analog, like college stations. 

TVTime should work though if you have s-video or rca input that can be attached to it, which would enable you to say hook up a vcr or record player or whatever you want to the tv card, and have it been seen or listened to on your computer.

And as for the antenna feed that you have, which as I said is digital I'm guessing, SMPlayer or VLC is probably the best.

Oh, and I almost forgot, the tvtime that is in the lucid repos doesn't seem to work correctly. At least for me. So if you experience the same issues, what I did is just installed a later version from the debian repository, [http://packages.debian.org/sid/tvtime](http://packages.debian.org/sid/tvtime) (links are on the bottom), and it works just fine.

---

### Post by izh34 on 2010-05-30
> **inameiname said:**
> Yes, however, I think TVTime won't work for the antenna feed (presumably digital over-the-air channels), just analog cable. I'm guessing it used to work just fine, but as you know ever since all broadcast over-the-air became strictly digital, there are no longer any analog broadcast stations floating around. Well, at least in the US....and no including the really small stations that are still broadcasting in analog, like college stations. 

TVTime should work though if you have s-video or rca input that can be attached to it, which would enable you to say hook up a vcr or record player or whatever you want to the tv card, and have it been seen or listened to on your computer.

And as for the antenna feed that you have, which as I said is digital I'm guessing, SMPlayer or VLC is probably the best.

Oh, and I almost forgot, the tvtime that is in the lucid repos doesn't seem to work correctly. At least for me. So if you experience the same issues, what I did is just installed a later version from the debian repository, [http://packages.debian.org/sid/tvtime](http://packages.debian.org/sid/tvtime) (links are on the bottom), and it works just fine.

Thanks for your quick reply. After I do some quick research I do find what my tv card chip is.

By doing
$ lspci | grep Multimedia

I got this info out on terminal
03:07.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

After seeing this, I quickly check at the box and found that my tv card chip is Philips SAA7131E as it is written on the box.

BY doing some searching I found about it in this thread
[http://ubuntuforums.org/showthread.php?t=884438](http://ubuntuforums.org/showthread.php?t=884438)

I do as the tutorial given and there is progress in it. There is channel management option shown but not the picture. I done some tweaking and scanning but to no avail. 

I'm quite frustrated with it now. I will report my progress later.

---

### Post by inameiname on 2010-05-31
Hmmmm, I've heard of that way that you found for your specific card and whatnot, but I've never tried it to give you any help there.

Did you happen to download the latest TVTime from the Debian link I gave you? I would do that regardless, as the latest version is often the best to have. Who knows. It might be your issue.

---

### Post by izh34 on 2010-06-01
> **inameiname said:**
> Hmmmm, I've heard of that way that you found for your specific card and whatnot, but I've never tried it to give you any help there.

Did you happen to download the latest TVTime from the Debian link I gave you? I would do that regardless, as the latest version is often the best to have. Who knows. It might be your issue.

Nope. Still can't work it out even I got the latest TVtime.

 But now I have another problems with it. After I do some changes with the alsa, my pidgin won't give a sound anymore. Even somebody buzzing me there will be no sound. Hard for me to know where could have made it like that.

Still trying to figure out why and how my pidgin being so soundless.

---

### Post by inameiname on 2010-06-01
Aww, that's too bad the newer TVtime didn't fix it for ya.

And sounds like even more bad news. So you say you followed that one guide you found specifically for your card? Alrighty....uhm, well first off, that tutorial, while very thorough and potentially helpful, was for a version of Ubuntu a couple back, and regarding alsa, if I'm not mistaken, the entire audio workings of Ubuntu changed dramatically in Karmic, with Pulseaudio, and Alsa and OSS isn't used anymore (or something like that). So I'm thinking that stuff from the tutorial would no longer apply. Of course, I'm not expert to say for sure.

As far as how to help with your Pidgin issue, (which doesn't make a lot of sense as to why that would happen), perhaps just try and fix the things you've tweaked/changed from the tutorial back to the way you had them before. If possible. Hopefully that will fix your new woes. 

So....

sudo gedit /etc/modprobe.d/options

...remove...

#options saa7134 card=42 tuner=17
options saa7134 card=59 tuner=56
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa
options saa7134-alsa index=1

...and if you also added this....remove it too...

alias char-major-81 videodev
alias char-major-81-0 saa7134

...then reboot...

In regards to the rest of that tutorial, it shouldn't have anything to do with your troubles as it seems to be strictly for TVtime.

---

### Post by izh34 on 2010-06-06
You're damn right about it. It seems TVtime won't cooperate with me to solve the problem:P. But nevertheless I still won't give up until I find the solution. I found about this [http://ubuntuforums.org/showthread.php?t=340499](http://ubuntuforums.org/showthread.php?t=340499) but not help me at all.

How about I do this command
```
lspci -nn
```And this is out
> 00:00.0 Host bridge [0600]: ATI Technologies Inc RX780/RX790 Chipset Host Bridge [1002:5957]
00:02.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A) [1002:5978]
00:0a.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F) [1002:597f]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] [1002:4390]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: nVidia Corporation G96 [GeForce 9500 GT] [10de:0640] (rev a1)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
**03:07.0 Multimedia controller [0480]: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)**
03:0e.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024]Then I go to
[http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.saa7134#110](http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.saa7134#110)
and match with
> 17 -> AOPEN VA1000 POWER                       **[1131:7133]**Is this mean my tuner or card is no. **17**?

How about this [http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.tuner](http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.tuner)

Could > tuner=**17** - Philips NTSC_M (MK2)Be my tuner number?

I just can't seems to understand about it. Hope I find the answer of it later. Still googling for answers. Will report the progress later :arrow:.

---

### Post by inameiname on 2010-06-09
I don't really know. That method seems too complicated for me, so best not to give you guesses from my end which might make things more confusing for ya. :P

With:

lspci -nn
it shows your card is there, but as you know, just something is preventing it from working right. I would like to think this means your firmware is there, and being read. And about your tv tuner #, from those links you gave, I'm not sure if that would be your specific card just because those last couple numbers match up. Might be, but I would think the first part of that would be closer to your specific hardware. But who knows.

---

### Post by argile on 2010-09-06
Hi,

I have the same card : GT-PTV-AF-RH-GA with the chipset Philips SAA7131E and I'm not able to make it work. I set tvtime with my device : /dev/video1 because I have also a webcam witch I have unplugged, but there is a black screen on tvtime and I'm not able to change the channel. My card appear to be UNKNOW/GENERIC in dmesg as you can see below. I'm trying to follow instructions of [http://tvtime.sourceforge.net/problems.html#undetected](http://tvtime.sourceforge.net/problems.html#undetected)  but I don't know what they means with "If the card appears as UNKNOWN/GENERIC, find the CARDLIST             file in your kernel documentation and find your card in the list." What can I do?

Thanks.

[   13.891406] saa7130/34: v4l2 driver version 0.2.16 loaded
[   13.891447] saa7134 0000:01:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.891453] saa7133[0]: found at 0000:01:00.0, rev: 209, irq: 17, latency: 64, mmio: 0xf9ffe800
[   13.891459] saa7133[0]: subsystem: 1458:9003, board: UNKNOWN/GENERIC [card=0,autodetected]
[   13.891492] saa7133[0]: board init: gpio is c000000
[   13.962911] hda_codec: ALC1200: SKU not ready 0x411111f0
[   13.962991] hda_codec: ALC1200: BIOS auto-probing.
[   14.016544] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[   14.018198] SGI XFS Quota Management subsystem
[   14.025794] sonixj: Sensor mt9v111
[   14.027853] input: sonixj as /devices/pci0000:00/0000:00:1d.3/usb8/8-1/input/input5
[   14.027952] gspca: video0 created
[   14.027955] gspca: found int in endpoint: 0x83, buffer_len=1, interval=100
[   14.027979] gspca: probing 0c45:60c0
[   14.027991] gspca: probing 0c45:60c0
[   14.028019] usbcore: registered new interface driver sonixj
[   14.028020] sonixj: registered
[   14.028109] usbcore: registered new interface driver sn9c102
[   14.056959] usbcore: registered new interface driver snd-usb-audio
[   14.081260] saa7133[0]: i2c eeprom 00: 58 14 03 90 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   14.081271] saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   14.081280] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 03 08 ff 00 c2 ff ff ff ff
[   14.081290] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.081299] saa7133[0]: i2c eeprom 40: ff 22 00 c2 96 ff 02 30 15 50 ff ff ff ff ff ff
[   14.081308] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.081317] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.081326] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.081335] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.081344] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.081353] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.081362] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.081377] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.081384] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.081392] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.081400] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.081856] saa7133[0]: registered device video1 [v4l2]
[   14.081884] saa7133[0]: registered device vbi0
[   14.088344] saa7134 ALSA driver for DMA sound loaded
[   14.088375] saa7133[0]/alsa: saa7133[0] at 0xf9ffe800 irq 17 registered as card -2

---

### Post by inameiname on 2010-09-06
Silly question, but have you changed the video source in TVTime to the appropriate source? Not the video1 to use it instead of the webcam, but inside TVTime itself, to change from S-Video, Composite, and TV? I have to do this whenever I reinstall things.

---

### Post by argile on 2010-09-08
Hi,

I'm unable to change the video source. It's always say "default". By the way, I found the CARDLIST of a chipset near of mine (saa7134) on this web site : [http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.saa7134](http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.saa7134). My tv card is a Gigabyte Tiger 2 TV, so maybe one of these will work:

81 -> Philips Tiger reference design           [1131:2018]
109 -> Philips Tiger - S Reference design 

Also, I see in a forum that someone tried this one with partial success :
57 -> Avermedia AVerTV GO 007 FM               [1461:f31f] 

But, I how to configure them in my Ubuntu 10.10 ?

Thanks.

---

### Post by Baldrick_NZ on 2010-09-08
It might help to go though the repo's and try other TV viewer apps. The only one I'd stay away from is MythTV, it's really not that user friendly - especially for newbies.

I found, for me, TvTime did the biz when others didn't work. Might be that one of the other apps will work better for you?

The other thing is that TvTime will only work for analogue TV, be it over-the-air, or though line inputs. I use mine with an external digital satellite receiver plugged into the S-video socket. 
So, if your country has switched to digital TV transmissions, as many are, then this app won't work for you natively. This may also explain why you are getting sound but no picture. 

Check with your broadcasters as to whether they are using analogue or digital over-the-air (or free-to-air) transmission. If they are using digital only, find another app or use an external receiver pplugged into the card.

Hope that helps..

---

### Post by argile on 2010-09-08
My card is an analog only for TV and FM. I have analog cable only. It's work well in Windows 7. I know that is not the best quality, but it's what I need for the moment. I had unplugged my webcam and restarted Ubuntu. I tried diferents apps without any success :

tvtime opens /dev/video0 with a black screen and no sound. I'm unable to change the video source.
vlc opens /dev/video0 with a black screen and noise sound. I don't know what to enter in Advanced options.
I don't understand MythTV.
XawTV have a black screen and no sound. I don't know how to change the settings.
Zapping TV viewer give me multiple errors.

I enter this without any success :
modprobe saa7134 card=57 tuner=54
Does someone know which card number and tuner I have to enter for a GT-PTV-AF-RH-GA Gigabyte Global TV Card (Gigabyte Tiger 2 TV) with a Philips SAA7131E chipset? How do I know the name of my tuner? Is it written on the physical PCI card itself in my computer?

How do I remove a module ? I got an error when I do this:
rmmod saa7134
ERROR: Module saa7134 is in use by saa7134_alsa
rmmod saa7134_alsa
ERROR: Module saa7134_alsa is in use
I don't see which program use alsa ? How do I send you my list of active programs to help me with this?

Sorry for the multiple questions, I'm a little bit lost.

---

### Post by Cigla on 2010-12-28
I think my card is similar to yours, with subsystem 1458:9003
I have picture, but no sound. 

> **argile said:**
>  I got an error when I do this:
rmmod saa7134
ERROR: Module saa7134 is in use by saa7134_alsa
rmmod saa7134_alsa
ERROR: Module saa7134_alsa is in use
I don't see which program use alsa ? How do I send you my list of active programs to help me with this?

Try to disable your TV card in Sound preferences->Hardware first, and then repeat Terminal commands. I set card to card=109, and now I just need to find out which is my tuner id, hope that will enable sound.

Here is exactly which commands I use:
```

sudo modprobe -vr saa7134_dvb
sudo modprobe -vr saa7134_alsa
sudo modprobe -vr saa7134
sudo modprobe -v saa7134 card=109

```
code found [here]("http://ubuntuforums.org/showthread.php?t=1567212")

You'll find the output of modinfo saa7134 in the attachment.

---

### Post by WhiskeySierraEcho on 2010-12-28
G'day, you could try "Me TV", I have it working on two comps using USB DVTB dongles

ps I am in Austrailia

---

### Post by Cigla on 2010-12-28
Thanks, I'll try it right away and get back here.
And after that, I go to sleep, I'm in Serbia):P
(We're still on analog signal, hope Me TV works with it-No it doesn't, says the Software Center-I go straight to bed)

---

