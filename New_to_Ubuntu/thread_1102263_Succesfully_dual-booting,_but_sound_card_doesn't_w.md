---
title: "Succesfully dual-booting, but sound card doesn't work in XP"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by Edward B. on 2009-03-21
Not strictly an Ubuntu question, I suppose, but I have been unable to find help in other places.

I have finally managed to get my system dual-booting Ubuntu and XP, but my sound card does not work in XP. It worked fine before when my sole OS was XP.

I discovered this wasn't working when I installed a game and the game would not run, which I eventually concluded was because XP was not detecting my sound card.

I have no sounds at all on the computer - no system sounds, music files will not play, etc.

I have been unable to locate my sound card through the XP system. In the hardware tab I did come across an entry next to a yellow question mark that read "mulitmedia sound" or something similar. When I check on properties, it says that drivers are not installed. I can not install drivers automatically, however, because I can not connect to the Internet with XP as it also states that my ethernet card does not have proper drivers installed.

None of this was a problem when I installed Ubunut... it has been so long since I first had XP installed that I don't recall how the drivers were installed at that time.

I tried running dxdiag to figure out what kind of sound card I have (so I could go to Ubuntu, download the driver, and then return to XP with the drivers), but it comes up saying that there are no sound cards.

I am really stumped here. Anyone know of something that could help me out?

---

### Post by suomalainen on 2009-03-21
Could you remove the sound card and use what the MB has to offer and then work from there? You might need to install drivers if you have a namebrand PC your using.

---

### Post by ivanvajar on 2009-03-21
Uninstall sound card driver and install it again. Ubuntu could not cause soundcard to stop working.

---

### Post by InfectedWithDrew on 2009-03-21
Look up your computer model, get the drivers via the internet on another computer or while running Ubuntu, put them on a flash drive, then install them on XP.

When you had just XP, chances are that the OS had been configured and the drivers were already installed.

Alternatively you could find your driver disk but it seems that it's been a while since you knew where it was, judging from your comments.

----------------
Now playing: [Disturbed - Stricken (Live at the Riviera)](http://www.foxytunes.com/artist/disturbed/track/stricken)

---

### Post by Edward B. on 2009-03-21
> **InfectedWithDrew said:**
> Look up your computer model, get the drivers via the internet on another computer or while running Ubuntu, put them on a flash drive, then install them on XP.

When you had just XP, chances are that the OS had been configured and the drivers were already installed.

Alternatively you could find your driver disk but it seems that it's been a while since you knew where it was, judging from your comments.

----------------
Now playing: [Disturbed - Stricken (Live at the Riviera)](http://www.foxytunes.com/artist/disturbed/track/stricken)

Where will the computer model number be listed? I thought I found it (MPT-103), but that turned out to the be the model number for the power supply only.

---

### Post by Edward B. on 2009-03-22
Is there a way I can use Ubuntu to find out what sound card I have installed on my PC?

---

### Post by InfectedWithDrew on 2009-03-22
> **Edward B. said:**
> Where will the computer model number be listed? I thought I found it (MPT-103), but that turned out to the be the model number for the power supply only.

On the back or bottom of the computer, usually.

----------------
Now playing: [tobyMac - Burn For You (Math Remix)](http://www.foxytunes.com/artist/tobymac/track/burn+for+you+(math+remix))

---

### Post by mlentink on 2009-03-22
> **Edward B. said:**
> Is there a way I can use Ubuntu to find out what sound card I have installed on my PC?
```
 lspci -v
```

---

### Post by Edward B. on 2009-03-22
> **mlentink said:**
> ```
 lspci -v
```

According to that, my sound card is:

Multimedia audio controller: Intel Corporation 82801EB/ER...

I can't find any drivers for this! Is the card called the 82801EB/ER or is it just multimedia audio controller?

---

### Post by mlentink on 2009-03-22
> **Edward B. said:**
> According to that, my sound card is:

Multimedia audio controller: Intel Corporation 82801EB/ER...

I can't find any drivers for this! Is the card called the 82801EB/ER or is it just multimedia audio controller?

Hmm. That's your (on-board) sound card all right. But afaik that should be supported out of the box. Intel take great care to be very well supported by GNU/linux distros. 
So why yours doesn't work is, without more info, unclear to me.

---

### Post by Edward B. on 2009-03-22
> **mlentink said:**
> Hmm. That's your (on-board) sound card all right. But afaik that should be supported out of the box. Intel take great care to be very well supported by GNU/linux distros. 
So why yours doesn't work is, without more info, unclear to me.

I know. It is very odd. It works find while in Ubuntu. In fact, I have a video running right now with perfect sound.

Whenever I boot into XP, however, I get no sound from anything and it says my sound card is not installed.

---

### Post by mlentink on 2009-03-22
> **Edward B. said:**
> Whenever I boot into XP, however, I get no sound from anything and it says my sound card is not installed.


My bad, should've read closer.
You might want to look here: [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=948&DwnldID=6816&strOSs=44&OSFullName=Windows*%20XP%20Professional&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=948&DwnldID=6816&strOSs=44&OSFullName=Windows*%20XP%20Professional&lang=eng)

But don't blame me, it's windows...

---

### Post by mlentink on 2009-03-22
Or this, maybe?

[http://www.driverfiles.net/Sound-Cards/Intel/page,level2,904,7,resultpage1.html](http://www.driverfiles.net/Sound-Cards/Intel/page,level2,904,7,resultpage1.html)

---

### Post by Edward B. on 2009-03-23
> **mlentink said:**
> Or this, maybe?

[http://www.driverfiles.net/Sound-Cards/Intel/page,level2,904,7,resultpage1.html](http://www.driverfiles.net/Sound-Cards/Intel/page,level2,904,7,resultpage1.html)

Thanks a lot.

Any idea which of these I'd need?

I tried downloading two of them and neither worked out. I also didn't see any that were listed as 82801EB/ER. None of them had the EB/ER extension. Not sure if that's important or not.

---

### Post by Edward B. on 2009-03-25
> **InfectedWithDrew said:**
> On the back or bottom of the computer, usually.

----------------
Now playing: [tobyMac - Burn For You (Math Remix)](http://www.foxytunes.com/artist/tobymac/track/burn+for+you+(math+remix))

Hmm... my computer does not seem to have this on either the back or on the bottom. It was custom built, so maybe it doesn't have one?

---

### Post by halitech on 2009-03-25
if its a custom built it wouldn't have a model number so the only way to know is by checking it out physically. Are you using the onboard sound in windows?

maybe just for kicks and giggles, boot into windows, remove the item with the yellow triangle and reboot, see what happens.

---

### Post by gsocker on 2009-03-25
```
Multimedia audio controller: Intel Corporation 82801EB/ER
```

This is either an AC'97 or HDA onboard audio controller.
With these, the interface to the controller is standardized but the interface between it and the associated codec/DAC/ADC is **not**. You therefore have to get a driver mainly for the codec portion; every manufacturer seems to have their own unique connections schemes between the controller and the codec chip. As a result, the chip name of the onboard controller doesn't matter that much. If this is a custom PC, best bet is to search the make/model of the motherboard on Google and try to find the manufacturer's drivers. 

You can see whether which type of interface you have by opening up Terminal and running ```
grep snd /proc/modules
```
HDA will probably be "snd-hda-intel", AC'97 will be something along the lines of  "snd-ac97-intel"

---

### Post by Edward B. on 2009-03-26
> **gsocker said:**
> ```
Multimedia audio controller: Intel Corporation 82801EB/ER
```

This is either an AC'97 or HDA onboard audio controller.
With these, the interface to the controller is standardized but the interface between it and the associated codec/DAC/ADC is **not**. You therefore have to get a driver mainly for the codec portion; every manufacturer seems to have their own unique connections schemes between the controller and the codec chip. As a result, the chip name of the onboard controller doesn't matter that much. If this is a custom PC, best bet is to search the make/model of the motherboard on Google and try to find the manufacturer's drivers. 

You can see whether which type of interface you have by opening up Terminal and running ```
grep snd /proc/modules
```
HDA will probably be "snd-hda-intel", AC'97 will be something along the lines of  "snd-ac97-intel"

I don't see either HDA or 97. This is what I get:

snd_intel8x0 37532 4 - Live 0xf8ade000
snd_ac97_codec 111652 1 snd_intel8x0, Live 0xf8af4000
ac97_bus 9856 1 snd_ac97_codec, Live 0xf8aa9000
snd_pcm_oss 46848 0 - Live 0xf8a85000
snd_mixer_oss 22784 1 snd_pcm_oss, Live 0xf8a9e000
snd_pcm 83204 4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss, Live 0xf8ab9000
snd_seq_dummy 10884 0 - Live 0xf8982000
snd_seq_oss 38528 0 - Live 0xf8a93000
snd_seq_midi 14336 0 - Live 0xf8a80000
snd_rawmidi 29824 1 snd_seq_midi, Live 0xf8a5c000
snd_seq_midi_event 15232 2 snd_seq_oss,snd_seq_midi, Live 0xf8a24000
snd_seq 57776 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xf8a70000
snd_timer 29960 2 snd_pcm,snd_seq, Live 0xf8a42000
snd_seq_device 15116 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq, Live 0xf8a1f000
snd 63268 17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xf8a4b000
soundcore 15328 1 snd, Live 0xf89b2000
snd_page_alloc 16136 2 snd_intel8x0,snd_pcm, Live 0xf89ad000

---

### Post by gsocker on 2009-03-27
OK - it's an older AC'97 one, then. "snd-intel8x0" is the driver for these chips.
My newer system's built in audio is HDA and I couldn't remember the exact module name for the older one.

For XP, your best bet is the manufacturer of the motherboard(if custom) or the manufacturer of the computer. Linux has "generic" drivers that attempt to work with as many systems as possible.
XP doesn't have this and needs a driver from the manufacturer.

---

### Post by dse.37 on 2009-03-27
From Windows try this:

Go to this [website]("http://driverpacks.net/DriverPacks/") and download the Sound A and Sound B packs.

Unrar them to somewhere handy (your desktop).

Right click on My Computer and select Manage and then select the Device Manager from the console tree.

Right click on the undetected hardware and select Update Driver...

When asked if you want to search online, select No. On the next screen, select the Install from a specific location button and click next.

Uncheck the Removable media (CD-ROM) and select the Include this location box. Browse to the downloaded driver package (on your desktop) and click next.

If a suitable driver is detected then make a thorough list of your hardware and email it to yourself. That way if you ever need a specific driver for whatever hardware in your machine again you know what to start looking for.

edit: This is why I adore Ubuntu.

---

### Post by Edward B. on 2009-03-27
> **dse.37 said:**
> From Windows try this:

Go to this [website]("http://driverpacks.net/DriverPacks/") and download the Sound A and Sound B packs.

Unrar them to somewhere handy (your desktop).

Right click on My Computer and select Manage and then select the Device Manager from the console tree.

Right click on the undetected hardware and select Update Driver...

When asked if you want to search online, select No. On the next screen, select the Install from a specific location button and click next.

Uncheck the Removable media (CD-ROM) and select the Include this location box. Browse to the downloaded driver package (on your desktop) and click next.

If a suitable driver is detected then make a thorough list of your hardware and email it to yourself. That way if you ever need a specific driver for whatever hardware in your machine again you know what to start looking for.

edit: This is why I adore Ubuntu.

Thanks for going out of your way to help me out. I can't seem to extract the files via Ubuntu... but maybe that's because they're designed for Windows? I will reboot to XP and try doing that.

I'm liking Ubuntu a lot, also, except for games!

And the fact that I'm still having some sort of trouble when I turn my computer on after it has been shut off... I keep getting a screen with a blue pattern.... kinda like bars.... it has a flashing "_" like a DOS prompt, but I can't type anything into it. I have to manually shut the computer off, then turn it back on and everything works fine!

Maybe my computer is just getting old and feeble...

---

### Post by Edward B. on 2009-03-28
Thanks for the earlier info on the sound packets, but I can not open either of them in XP. Is there a specific program I need. I thought winrar was automatically included on XP, but maybe not? 

If not, I guess I'll have to download it to a flash drive and ferry it over to XP.

---

### Post by halitech on 2009-03-29
XP doesn't included winrar or winzip but if its a compressed file then the XP compressed file viewer should open it

---

### Post by InfectedWithDrew on 2009-03-29
> **halitech said:**
> XP doesn't included winrar or winzip but if its a compressed file then the XP compressed file viewer should open it

You can download 7-zip for Windows and it works well inside the shell.

----------------
Now playing: [The Offspring - Autonomy](http://www.foxytunes.com/artist/the+offspring/track/autonomy)

---

### Post by Edward B. on 2009-03-31
Thanks guys. I have more severe problems, however.

Today when Ubuntu started up it went to a black screen with a lot of text. I wish I would have written it down, but, being a moron, I did not.

It said something about not being able to start because of some missing file and then said it was starting some type of shell... a maintenance shell or something? It said to press ctrl D when done. 

I could never figure out what to do, so I ended up having wipe my OS again, and again installing Ubuntu. So now all of the work I did installing Windows is gone (although at least I can do it again if I have to).

Also, I am still having problems when I initially turn on my computer after being turned off, it flashes colours, the screen is a mess. Then if I turn it off and back it on it works fine (at least for now).

Is it possible that my motherboard is dying or something similar?

---

### Post by halitech on 2009-03-31
I'd be more inclined to think video card or monitor (but probably video card since the powercycle seems to give it a kick to work)

---

### Post by Sylslay on 2009-03-31
Becouse You did not say what sound card You got , Tray download Vinyl Audio.  Its work mostly on VIA cheapset. But I install that on fiew laptop with intel chipsest and soundacard VT11... .
For laptop it brings masive improve of sound qality,
Link for VIAARENA softwehe .Vinyl works with no problem on Siemens, Dell laptops, Asrok MB,.
[http://www.viaarena.com/default.aspx?PageID=420&OSID=1&CatID=1010&SubCatID=104](http://www.viaarena.com/default.aspx?PageID=420&OSID=1&CatID=1010&SubCatID=104)

---

### Post by Sylslay on 2009-03-31
Basicly, if that driver will deteact chipset with AC97 sound, than will work
Good luck.

---

